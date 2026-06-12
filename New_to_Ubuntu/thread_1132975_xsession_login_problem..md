---
title: "xsession login problem."
date: 2009-04-22
forum: New to Ubuntu
---

### Post by italtap on 2009-04-22
i am unable to  log into the xsession. I get the error message 'your session only lasted less than 10 seconds...', etc. The content of the xsession-errors file is:
```
/etc/gdm/Xseesion: beginning session setup...
No profile for user 'kassan' found
===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2009/04/23 00:12:54.0107 (sabayon-apply): No profile for user 'kassan' found
MainThread 2009/04/23 00:12:54.0113 (sabayon-apply): Fatal exception: Exiting abnormally.
MainThread 2009/04/23 00:12:54.0124 (sabayon-apply): Traceback (most recent call last):
  File "usr/sbin/sabayon-apply", line 107, in <module>
      sys.edit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END MILESTONES (/usr/bin/sabayon-apply) =====

===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2009/04/23 00:12:54.0107 (sabayon-apply): No profile for user 'kassan' found
MainThread 2009/04/23 00:12:54.0113 (sabayon-apply): Fatal exception: Exiting abnormally.
MainThread 2009/04/23 00:12:54.0124 (sabayon-apply): Traceback (most recent call last):
  File "usr/sbin/sabayon-apply", line 107, in <module>
      sys.edit (util.EXIT_CODE_NORMAL)
SystemExit: 0

===== END RING BUFFER (/usr/bin/sabayon-apply) =====

This configuration for the debug log can be re-created by putting the following in ~/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
setting IM through im-switch for locale=en_PH.
start IM through /home/kassan/.xinput.d/en_PH linked to /etc/X11/xinit/xinput.d/scim-bridge
Smat Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
/usr/bin/seahorse-agent: error while loading shared libraries: libICE.so.6:cannot open shared object file: No such file or directory
```I wasn't trying to change anything, just one day it stopped working and hasn't come since. if i try to start th the failsafe sessions they don't work either, but i can use ctrl-alt-f1 to use the command line.

can anyone help me with this problem? I've searched this forum, and found lots of questions and solutions that seem similar to me, but no solutions that have worked yet...

oh, it's ubuntu hardy...

---

