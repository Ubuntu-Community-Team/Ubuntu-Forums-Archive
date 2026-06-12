---
title: "MythTV won't uninstall"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-10-31
I tried MythTV but for some reason it didn't work.

I was gonna uninstall it so I deleted the "mythtv" user account using "removeuser mythtv".

Problem is, now when I go to uninstall MythTV, it gives me an error: > chown: invalid user: `mythtv'
invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: error processing mythtv-backend (--remove):
 subprocess pre-removal script returned error exit status 1
chown: invalid user: `mythtv'
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-backend
E: Sub-process /usr/bin/dpkg returned an error code (1)
Fixing the broken package in Synaptic does nothing. :(

This is what happens when I try to reinstall the MythTV backend> E: mythtv-backend: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured


I tried adding the "mythtv" user back manually, through graphical Users and Groups and through terminal, but it says the user already exists (although it doesn't show that it does exist and "chown" doesn't see the account)

Any help please?

---

### Post by Cuco3 on 2009-10-31
BTW I've tried googling already with no success, fyi.

I tried using "useradd mythtv -g" to create the user account but the error still appears, the message changes to reflect that it can't find the home directory. > Removing mythtv-backend ...
 * MythTV home directory, /home/mythtv does not exist.
invoke-rc.d: initscript mythtv-backend, action "stop" failed.
dpkg: error processing mythtv-backend (--remove):
 subprocess pre-removal script returned error exit status 1
 * MythTV home directory, /home/mythtv does not exist.
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-backend
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Cuco3 on 2009-10-31
Please?

---

