---
title: "Samba connects to NAS, but file names not displayed correctly."
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by Turnba on 2007-11-01
I installed Ubuntu 7.10, and can quite happily use Nautilus to browse to my NAS drive and do all the usual stuff. All the folders on the remote drive are present and correct.

The problem is I would like to mount the shares on boot. I put the following line in /etc/fstab:

//NASdrive/Michael   /mnt/NASdrive/Michael  smbfs   credentials=/etc/samba/user,rw,uid=michael   0   0

This does mount the share, but the folder names are all scrambled, like the charset is wrong. Doing ls in the folder gives me:

???  ????  ?????  ay Backupsl  n  pge  st.jpgm  sv

instead of the file/folder names. I've tried putting in charset=UTF-8 or isoblahblah or CP850, but the same thing happens. I just find it odd that I can browse there ok and it displays fine, but mounting goes wrong. I did testparm -v | grep "dos charset", "unix charset", "display charset", which gave me:
dos charset = CP850
unix charset = UTF-8
display charset = LOCALE

I've not idea what's wrong, if anyone can offer advice. Maybe the charset thing is a blind alley.

Thanks!

---

### Post by Thies on 2007-11-06
Hi!

Here is how I mount my NAS (LaCie Ethernet Big Disk) in "/etc/fstab":

```
//192.168.0.20/share  /media/NAS/share  smbfs  uid=thies,gid=thies,credentials=/home/thies/.smbcredentials,dmask=777,fmask=777,iocharset=utf8,codepage=unicode,unicode 0  0

```

I don't know if that's how it should be but at least this works (up to now) fine for me.

Cheers and good luck!

---

### Post by Turnba on 2007-11-06
Thanks for the suggesstion Thies, but it didn't work :-( When I try that the contents of the directory are now listed as:

&#64387;&#455;  &#50415;:x01  :x6e  :x6e  &#26480;:x65  &#29811;&#27182;&#26480;:x6d  &#30323;  &#31073;&#16928;&#25441;&#30059;&#29552;:x6c  &#33707;&#51195;:x01

Which is clearly not correct! Does anyone know how I can tell what charset/codepage is being used? Or since I can use Nautilus to browse the drive ok, how do I find the settings Nautilus is using?

---

### Post by hellibombelli on 2007-11-08
I'm mounting my TeraStation with:
```
mount -t smbfs -o rw,uid=helli,username=helli,password=mysecretpassword,codepage=cp850,iocharset=utf8 //mytera/daten  /media/myTera
```

Hope it helps.

---

