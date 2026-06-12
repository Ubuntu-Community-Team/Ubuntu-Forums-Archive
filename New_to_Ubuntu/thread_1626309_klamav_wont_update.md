---
title: "klamav wont update"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by wizandrew on 2010-11-20
hello i have a similar problem with klamav 0.46 (clamav 0.96.3) it wont update!

running (also with sudo)  freshclam returns:
```
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

```i tried to reinstall it already happens during the installation:
```
Preconfiguring packages ...
Selecting previously deselected package libclamav6.
(Reading database ... 182681 files and directories currently installed.)
Unpacking libclamav6 (from .../libclamav6_0.96.3+dfsg-2ubuntu1.1_amd64.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.96.3+dfsg-2ubuntu1.1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.96.3+dfsg-2ubuntu1.1_amd64.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.96.3+dfsg-2ubuntu1.1_amd64.deb) ...
Selecting previously deselected package klamav.
Unpacking klamav (from .../klamav_0.46-3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Setting up libclamav6 (0.96.3+dfsg-2ubuntu1.1) ...
Setting up clamav-base (0.96.3+dfsg-2ubuntu1.1) ...
Setting up clamav-freshclam (0.96.3+dfsg-2ubuntu1.1) ...
 * Starting ClamAV virus database updater freshclam                              ERROR: Can't open /var/log/clamav/freshclam.log in append mode  (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
                                                                         [fail]
Setting up clamav (0.96.3+dfsg-2ubuntu1.1) ...
Setting up klamav (0.46-3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```i am running kubuntu 10.10 x64
tried changing permissions for freshclam.log didn't help... :sad:

running kalmav as a regular user grays out the update button and as root  u get update process died unexpectedly did you kill it manually?

any ideas?

p.s.
after reading this [http://ubuntuforums.org/showthread.php?t=1547713](http://ubuntuforums.org/showthread.php?t=1547713)
it changes the database dir and now i can press the update button when i  run klamav (as regular user not root) however it now says: "unknown  option passed"
running freshclam returns the same error as before.

---

