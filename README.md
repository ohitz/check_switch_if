# check_switch_if

This is a nagios check which allows to check multiple network
interfaces defined by their name and/or description for their status
and for errors at once.

You specify the interfaces you would like to include in the check
using a perl regular expression which is matched against ifDescr
and/or ifAlias. All matching interfaces are then checked for their
ifOperStatus and for error rate.

If any of the matched interfaces is not up, the check returns
CRITICAL. Furthermore, the errors/min rate since the last invocation
of the check is calculated and WARNING or CRITICAL is reported if the
rate exceeds the configured limits.

At each invocation, the error counter is stored to disk. This state doesn't
have to survive a reset, by default it is stored in the
/var/run/nagios3/check_switch_if/ directory. If the state cannot be read, no
error rate calculation is done.
