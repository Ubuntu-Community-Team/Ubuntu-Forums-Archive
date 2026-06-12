---
title: "NX Server Installation Issues"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by draegoonscythe on 2008-05-06
Hi all,

I am currently have some issues setting up a NX server on my desktop. I downloaded all the required files from the NX website, and when I go to install it, I encounter this message while installing the NXserver:

NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.

Not having seen this error the first time through, I got the following message when doing sudo /usr/NX/bin/nxserver --status:

NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.

If anyone has any advice on the matter,that would be most appreciated. Thanks a lot!

To note: Currently using Ubuntu 8.04 Hardy Heron.

---

### Post by draegoonscythe on 2008-05-07
Bump

---

### Post by sungohan on 2008-05-11
I ran into this problem several times, you need to uninstall all nxserver, nxnode and nxclient, then delete directory /usr/NX.
Reinstall everything again, it should not show the broken warnings again.

About the --status error, I also have this error, I can not get it solved, but nxserver is still working.
I just use /usr/NX/nxserver --start to start the service, do not use --status ever.
The error should be something related to file /etc/ssh/sshd_config


Also on Hardy.



> **draegoonscythe said:**
> Hi all,

I am currently have some issues setting up a NX server on my desktop. I downloaded all the required files from the NX website, and when I go to install it, I encounter this message while installing the NXserver:

NX> 700 WARNING: Error when trying to connect to NX server, error is:
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.

Not having seen this error the first time through, I got the following message when doing sudo /usr/NX/bin/nxserver --status:

NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.

If anyone has any advice on the matter,that would be most appreciated. Thanks a lot!

To note: Currently using Ubuntu 8.04 Hardy Heron.

---

### Post by draegoonscythe on 2008-05-13
> I ran into this problem several times, you need to uninstall all nxserver, nxnode and nxclient, then delete directory /usr/NX.
Reinstall everything again, it should not show the broken warnings again.

I have done the uninstall-delete/usr/NX-reinstall (almost up to 10 times) and I still get the same result. I just grabbed the newest version (if I didn't have it already) from the nomachine website, but I still get the exact same error messages. 

Could something be wrong w/ my Hardy configuration that's causing this (it seems like other Hardy users are having problems but manage to fix it). 


Thanks for the help

---

### Post by Nampla on 2008-05-14
Try installing the latest patches from Ubutnu. I have had great sucess with nomachine on all my locations (7) i found the best way to handle odd problems is to uninstall, delete the NX directory and then re-install using the .deb packages.

---

