---
title: "Accessing WD Netcenter Drive from Ubuntu"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by air0day on 2006-11-13
I looked all over the forums but I couldn't find someone with my exact problem.  I saw a bunch of tips for mounting and unmounting, but trying that in different ways didn't help.

Basically, I have a Western Digital netcenter drive on my network.  It has a number of folders on it, all of which are shared in the network publically, without any password restrictions.

I can access smb://netcenter and see the folders.  I can go into the folders and open files.  I can even mount //netcenter/music to /media/mp3 without a problem.

After accessing for a while though (doing a number of ls's in a terminal, scanning the folder for mp3s in a media player, or even just clicking through in nautilus for a while) whatever program is accessing the mount or the share will freeze completely.  To make matters worse, if I kill it and try to access it in anything else (even a terminal window) it won't work, and THAT program will freeze and have to be killed.

I actually bought the netcenter in anticipation for switching to linux, and It's been working fine from windows (I map \\netcenter\music to X:) since I got it, so this is pretty frustrating.

I'm using Edgy.  Anyone have any ideas?  Much appreciated.

---

### Post by Tripletaco on 2007-06-19
I can't get my netcenter to work at all on ubuntu.  I have another pc which I have PCLinuxOS 2007 on and it just works.  Over on PCLinuxOS My touchpad doesn't work as nice as it does here on Ubuntu.  So this is where I spend most of my time.  Other than when I'm on XP

---

### Post by lwalsh on 2007-06-30
hi folks

this was driving me mad until I found this link - works a treat!

[http://www.nomachetejuggling.com/2007/01/13/using-western-digital-netcenter-with-ubuntu-linux/](http://www.nomachetejuggling.com/2007/01/13/using-western-digital-netcenter-with-ubuntu-linux/)

---

### Post by air0day on 2007-07-09
:lolflag: What an informative post!  The guy who wrote that is clearly some kind of demigod, in addition to being extremely attractive and muscular.

That's actually mine.  I figured it out after much gnashing of teeth and posted about it.  I hope others find the information helpful (I sure could have ;)).

---

### Post by dodgeman79 on 2007-10-28
I tried the method posted from the link and can't get my netcenter to mount.  i recently upgraded to 7.10 and this is the first attempt to mount my netcenter.

```
baker@ubuntu:~$ sudo mount -t nfs 192.168.1.105:/shares/Main/Shared /media/mediacenter
mount: wrong fs type, bad option, bad superblock on 192.168.1.105:/shares/Main/Shared,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by dodgeman79 on 2007-11-27
anyone have anything to get me going?

---

### Post by mrajsic on 2008-05-12
I have succeded connecting WD NetCenter using cifs method with full R/W. Under Ubuntu transfers seams to be 20 to 30% faster than in Windows. It is because Windows is using samba and it seams that somehow samba is slower than cifs.

Try this mounting method:
sudo mount -t cifs //192.168.x.y/dir /home/user/somedir -o ,iocharset=utf8,file_mode=0777,dir_mode=0777,lfs,uid=yourname,gid=root

note if you have password than add after -o password=yourpassword. lfs is not necessary but if you deceide to use smbfs than it is useful. It is very important to set uid to local user name. Sometimes there can be problems in 7.10 ubuntu regarding access rights to netcenter causing no respond from Netcenter or you will enter only read only mode
192.168.x.y is IP address of Net Center

This also works very well for WD My BOOK WE

---

### Post by dodgeman79 on 2008-05-20
just thought I would let everyone know that in 8.04 there is a network link to my netcenter drive.  Everything works like it should and the tranfser speed is great.  I guess they put in some good stuff in this version.

---

