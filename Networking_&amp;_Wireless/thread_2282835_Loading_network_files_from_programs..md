---
title: "Loading network files from programs."
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by oakridge on 2015-06-17
We have a Ubuntu 14.04 machine which is used as a fileserver and I use a dual-boot Windows 7/Ubuntu 12.04 machine.  I can connect to to the network with no trouble from 'Home Folder' but if I try to open a file from LibreOffice or upload to flickr the network is not listed. It is not a problem with Windows 7 or with any of the other machines using the server.

---

### Post by TheFu on 2015-06-17
Not the answer you want ... but a little history might be useful ... 

For files to be available under Unix, the location must be "mounted".  Historically, that feat was accomplished by the system administrator either for directly connected disks OR by the system admin by making NFS mounts. Administrators, not end-users, did this because it has huge security implications to the system.

In the last few years, there has been an expectation that end-users should be able to mount storage - network and local. For other OSes, that might be fine, because their file permissions are not as important to overall system security.  The core methods for mounting have not been altered, rather a new way, which isn't really a "mount," has been created using **gvfs**.  That is what most GUI programs use to make network storage available to 1 user of a system. The older programs haven't been modified to support mounting themselves, so if that is what you need, then you should use a file manager to cause gvfs to pseudo-mount the storage and access those files from any programs you like.  This may NOT work for all programs and using the *old school* mount might be necessary.

Comparing all the things that Linux can do vs what Windows can do is a good way to become frustrated with Windows. I suspect the alternative would also be true. For example, ever tried to use a "Library" under Windows from a cmd.exe?  It doesn't work - not at all. That is because a "Library" isn't part of the file system, so only specific programs can make use of it. Total implementation failure, if you ask me.  In Unix/Linux, things like that ARE part of the file system, so they always work when mounted as expected.

Anyway, I hope this helps with a "why is it this way" even if it is not the desired solution. There is a method to this madness, trust me.

---

### Post by oakridge on 2015-06-19
Up to retiring 7 years ago all the data was on Unix/Linux servers, but the old brain seems to have slowed somewhat. Even with 'Home folder' open at the required remote directory I cannot 'see' it using the file open window in any application.  It is a bit irritating to have to cope the required files to the home machine in order to open them.

---

### Post by Morbius1 on 2015-06-19
So I have a Linux Samba server at 192.168.0.100 with a samba share named downloads.

If I go to the Linux client machine and connect to the share first I can open LibreOffice Writer and "see" the connection to the share on the side panel:
[ATTACH=CONFIG]262715[/ATTACH]
What Writer will not do is give you a "Browse Network" link so that you can  find the server and it's share and mount it through that.

You might consider using Gigolo to automount these shares so that you don't have to go through the file manager first to mount them.

Also, not all applications are "gvfs-aware" so even if the share is mounted it may not show up as it does in Writer.

---

### Post by TheFu on 2015-06-19
> **oakridge said:**
> Up to retiring 7 years ago all the data was on Unix/Linux servers, but the old brain seems to have slowed somewhat. Even with 'Home folder' open at the required remote directory I cannot 'see' it using the file open window in any application.  It is a bit irritating to have to cope the required files to the home machine in order to open them.

Just "mount" the storage first. That is how this stuff works and your applications will see that.

---

### Post by oakridge on 2015-06-22
Thank you all for your help and I am connected, but....   I need to Mount the two directories concerned each morning and connect to them with the standard network password.  whereas this is a great step forward it would be nice to get rid of the mounting/logging on.

---

### Post by Morbius1 on 2015-06-22
Gigolo can remember the password so you don't have to logon manually.

EDIT:

*** Install gigolo:
```
 sudo apt-get install gigolo
```
*** Run gigolo and set up your preferences this way:
[ATTACH=CONFIG]262781[/ATTACH]
*** Connect to the server within gigolo and then bookmark it specifying that you want it to autoconnect at login and to remember the password.
*** Then have the gigolo application start at every login my adding a "startup applications":
[ATTACH=CONFIG]262782[/ATTACH]

---

### Post by TheFu on 2015-06-22
> **oakridge said:**
> Thank you all for your help and I am connected, but....   I need to Mount the two directories concerned each morning and connect to them with the standard network password.  whereas this is a great step forward it would be nice to get rid of the mounting/logging on.

Or you can use **autofs**. That will mount the storage, when it is requested and keep it mounted as long as it is used.  If it is unused, the mount is removed.  I find this perfect for well-known USB storage and NFS, but not everyone does.

---

### Post by oakridge on 2015-06-22
Bingo.  Job's a good 'un as they say.  I didn't see the autofs suggestion until after I had installed Gigolo.

Thank you all for your help.

---

