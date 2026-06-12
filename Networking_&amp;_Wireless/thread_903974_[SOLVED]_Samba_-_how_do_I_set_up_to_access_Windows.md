---
title: "[SOLVED] Samba - how do I set up to access Windows folders"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by charonred on 2008-08-28
Been trawling through these forums, but can't find a simple answer; How do I set-up this Samba thing so I can view and access my Windows machines

I have a LAN at home with 5 PCs; couple are multi boot, but most are XP based and simply have a workgroup name - there is no domain, nor user passwords (I just don't need, nor want, all that security for a home network)

How do I access these Windows machines :confused:

---

### Post by tolmeda on 2008-08-28
If you're using Gnome, go to Places -> Connect to Server...
Select Service Type = Windows share
If I remember correctly, Domain should be your Workgroup name.

To mount on boot see a more advanced tutorial [here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

---

### Post by charonred on 2008-08-28
Thanks Tolmeda, 
but what do I enter in the other fields, it asks for the server (I don't have one).

attached image is what pops up when I go to Places -> Connect to Server..

Strange thing is I can access my Ubuntu install from Windows (normally a real hassle getting that to happen, and I did nothing), which means Samba is functioning correctly; it's just I can't figure out how to access Windows from Ubuntu via Samba.

---

### Post by bab1 on 2008-08-29
The windows host is the server.  The server is built into the "share".  Check to see that you have "smbfs installed.  It's the Samba client part.  If not: ```
sudo apt-get install smbfs
``` will install it.  Then you should be able to browse via Places>>Network.

---

### Post by charonred on 2008-08-29
Thanks Bab1, that sorted that part out - smbfs wasn't installed, but is now.

it shows my network name and windows network 'Workgroup' and this PC is listed under that, but I want it listed as part of my home network name.

How do I change the network name it's on from 'Workgroup' to my own network name?

---

### Post by bab1 on 2008-08-29
You can edit the /etc/samba/smb.conf file to change the Ubuntu Samba server to the workgroup of your choice.  look at the [global] section of the file for:```
 workgroup = MSHOME
```or some name similar.  Change that to what you want.

---

### Post by charonred on 2008-08-29
Thanks again,
had a stumble around there in text editor, but I don't have permissions to save changes.
 
I suspect I have to do this in Terminal or similar, but have forgotten how to 'edit' in that mode (still trying to learn this)

---

### Post by bab1 on 2008-08-30
Try alt-f2 to run an application. in the box try:```
gksudo gedit /etc/samba/smb.cong
```.

This allows you to edit the file as "root" (the super user) and save it.

---

### Post by charonred on 2008-08-30
That fixed it, thanks

---

