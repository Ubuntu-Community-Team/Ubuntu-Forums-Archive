---
title: "Another Samba problem 16.04 mate"
date: 2016-05-05
forum: Networking &amp; Wireless
---

### Post by decrepit on 2016-05-05
I've just installed Mate on my emachines laptop. First job was to get samba working so it can connect to the PC, (where samba is working fine also with mate 16.04.)
It all looked good "windows network" came up with "workgroup" and the printer share. So then I had a go at smb.conf to change "workgroup" and add my home directory. After doing that clicking on "windows network" just gave me this, 
"Failed to retrieve share list from server: No such file or directory" 
Tried a few things including the smb.conf from 14.04. All to no avail, so I tried removing and reinstalling with App Grid. I then got an install error, so I tried the same thing with apt-get and got this during the process.
" >>>>>>>>>
update-alternatives: using /usr/bin/tdbbackup.tdbtools to provide /usr/bin/tdbbackup (tdbbackup) in auto mode
Setting up samba (2:4.3.9+dfsg-0ubuntu0.16.04.1) ...
Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "start" failed.
dpkg: error processing package samba (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up attr (1:2.4.47-2) ...
Setting up libaio1:amd64 (0.3.110-2) ...
Setting up samba-dsdb-modules (2:4.3.9+dfsg-0ubuntu0.16.04.1) ...
Setting up samba-vfs-modules (2:4.3.9+dfsg-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@michael-eME528:~$ "

I've tried searching for systemctl and journalctl but they don't seem to exist.

Samba didn't work all that well on the laptop in 14.04, i couldn't get it to share any of it's folders. So Maybe hardware has something to do with my problems?
I used very similar steps to get samba working on the PC and that's fine.

---

### Post by decrepit on 2016-05-06
Pressed the "fix broken packages button", then removed and reinstalled samba and samba config with apt-get. That all went well this time, so maybe the job app grid did wasn't as good, or maybe the bug in samba is now fixed?
Then used samba config to add a couple of shares without touching smb.conf.
Now it's working fine.

---

