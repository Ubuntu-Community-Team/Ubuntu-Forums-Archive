---
title: "Easy access to network-shares"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by ZarathustraDK on 2008-10-02
I have this annoying minor problem with my network-shares on ubuntu. Whenever I log in the mounted shares from previous session are gone (smb://yadda/yadda...) and then I can manually mount them once again.

I can also make a launcher (with location-option instead of application-option) that points to the share on the network, but if do that then it'll mount the share, resulting in another folder with the share popping up on the desktop (I have three shares, with this method I get six folders, which is a lot on my puny eee).

So is there an easy way around this?

---

### Post by jones139 on 2008-10-02
Firstly, I don't use samba much, so I might be talking nonsense, but with NFS mounts you just have to add a line to /etc/fstab listing the filesystems you want to mount at boot time.
I found this: [http://http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/]("http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/"), which looks like it is doing what you want by usng /etc/fstab.
I don't know a GUI way, sorry - I'm a luddite!

---

### Post by ZarathustraDK on 2008-10-03
So for my part adding

```
smb://lelouch/shared/ /mnt/lelouch smbfs 0 0
```

to fstab would be the way to go? (I don't have passwords set up on the network, just security=share and guests allowed.

---

### Post by Paul41 on 2008-10-03
There is something in this guide on how to add samba shares to fstab so they mount permanently.  Hope it helps

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by ZarathustraDK on 2008-10-03
Tried the guide, it said I should write something akin to
```
//apollo/install_files /path/to/mnt smbfs iocharset=utf8,credentials=/path/to/.smbcredentials,gid=1234 0 0
```
However, I don't have any users or passwords set for my shares (they're basically just empty folders I can dump stuff to across the network with 777 permissions).

Tried adding 
```
//lelouch/shared/ /mnt/lelouch smbfs 0 0
```
To fstab to no avail (and yes I did create the folder in /mnt). I must be missing something.

---

### Post by Paul41 on 2008-10-03
You would use your samba user and samba password, not the user and pw for the specific folder.

---

