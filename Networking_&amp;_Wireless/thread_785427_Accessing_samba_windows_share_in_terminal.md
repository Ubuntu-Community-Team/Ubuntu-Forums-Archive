---
title: "Accessing samba windows share in terminal"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by jockmullin on 2008-05-07
Greetings. I am a total Ubuntu newbie, recently installed Hardy & have p2p networking with win xp & 98 shares working fine.

Hwvr, now wondering how/if these shares are accessible from a terminal session. Can't locate shares in file system.

i.e. looking to do something like:
ls -la smb://winserver/winshare 

Is this possible, if so what is syntax, pls. Owise how to access shares from scripts?

Many thanks, Jock

---

### Post by jtrindle on 2008-05-07
You're going to have to either mount the samba volume, or use smbclient and script that somehow.

To mount, the command looks like:

sudo mount -t smbfs //linuxserver/shared /mnt

Then your script navigates to the folders under /mnt

You may need to specify something like -o username=ferd,password=berfle  after the -t smbfs for your setup.

---

### Post by jockmullin on 2008-05-07
Hi, jtrindle

OK, thanks I will give that a try.
I thought having mounted the volume on the desktop would already have it mounted.

Thanks again, Jock

---

### Post by jockmullin on 2008-05-07
Yes, it worked!

First I had to get the mount.smbfs helper program by installing smbfs, but the error message I got when I tried the mount said exactly what to do.

I like the way mount allows you to specify where the filesystem from the share will appear in the linux filesystem. Nice.

Jock

---

### Post by imfaisal87 on 2012-12-11
This might also help

for Domain environment

mount -t cifs -o username=abc@xyz.com 192.168.1.1:/Folder /mnt

for simple enviornment this should work I believe

mount -t cifs -o 192.168.1.1:/Folder /mnt

---

