---
title: "Annoying! Trying to connect to a windows share."
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by w0ts0n on 2008-10-22
Hi all.
I have a windows share called server/e$ no matter what I try I can't get it to mount permenantly 

when I got to address bar and type in smb://server/e$ it attached, but no matter what I try (samba). I can't get it to mount, the server does not have a static I.P (and re-sets every night) so I need the machine to be able to resolve the host name.

Any ideas? I'm pretty stuck here :(

---

### Post by camoanimal on 2008-10-22
Making sure that Samba is properly configured is the first priority.  Use this link to check that Samba is setup and configured properly. ([HowTo: Samba]("http://ubuntuforums.org/showthread.php?t=202605"))  Once this is done, trying going to Places>Network>Windows Shares and you should see it assuming you are not on a network with proxys.  After clicking on it (and logging in if necessary) a link should appear on your desktop.  It will then stay mounted for as long as the computer is on.

Does this answer you question?

---

### Post by jimv on 2008-10-22
Do you want this to mount everytime you boot?

If so, do this:

Install smbfs:

```
sudo apt-get install smbfs
```

Add your share to your /etc/fstab file:

```
//server/e$  /media/somefolder smbfs user=someuser,password=somepassword
```

AND

If you just want to mount the share, use this command
```

sudo smbmount //server/share /somefolder -o user=user,password=password
```

---

### Post by Iowan on 2008-10-22
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good CIFS mounting How-To.

---

