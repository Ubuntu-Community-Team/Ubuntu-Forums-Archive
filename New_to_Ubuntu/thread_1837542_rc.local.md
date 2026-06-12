---
title: "rc.local"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by gcave on 2011-09-01
I am trying to get a script to run on startup of LXDE.  I have edited /etc/rc.local to include the full path to my shell script, making sure both the script and rc.local have the x bit turned on.  (chmod -x)  I tried putting "/usr/bin/path/foo", xterm -e, etc, etc.  No worky, worky.

I also tried creating a script in /etc/init.d/bar, and editing "update-rc.d bar defaults 80" to create a symbolic link to bar without success.


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/foobar

exit 0

ll /etc/rc.local
-rwxr-xr-x 1 root root 340 2011-09-01 21:47 /etc/rc.local*

---

### Post by yetiman64 on 2011-09-01
> **gcave said:**
> ... making sure both the script and rc.local have the x bit turned on.  (**chmod -x**)  I tried putting "/usr/bin/path/foo", xterm -e, etc, etc.  No worky, worky.....
Maybe it is just a typo here but that should be a +x to make a script executable -x removes the executable bit.

---

