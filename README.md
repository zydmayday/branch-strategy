# branch-strategy

This is a repo for testing branch strategy

## Case 1 No hot fix

- test
- dev

checkout feature-1 from test.
create PR feature-1 > test, feature-1 > dev.

merge and release 1.0.0.

## Case 2 Hot fix without bug

- test
- dev

checkout feature-2 from test.
create PR feature-2 > test, feature-2 > dev.

- test > feature-2
- dev > feature-2

Then comes the hotfix.

reset test to `release-1.0.0`

- test(release-1.0.0)
- dev > feature-2

checkout bug-1 from test.
create PR bug-1 > test, bug-1 > dev.
merge and release 1.0.1

at the same time,
checkout feature-2 from dev,
create PR feature-2 > dev,
so that we can do bug fix and feature development at the same time.

after release 1.0.1,
rebase test with latest dev,
then we go back to case 1.

## Case 3 Hot fix with conflict, resolve in dev

the basic idea is the same as case 2,
difference is after we merge bug-2 to dev,
bug-2 could have conflicts with feature-3 > dev.
so we need to resolve conflicts before we merge feature-3 to dev.

## Case 4 Hot fix with conflict, resolve in test


