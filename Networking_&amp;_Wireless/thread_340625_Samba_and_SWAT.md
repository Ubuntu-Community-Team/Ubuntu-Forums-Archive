---
title: "Samba and SWAT"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by happyhacker on 2007-01-17
I have installed these two. I have made no changes to any config files from Ubuntu install.
If I enter [http://localhost:901](http://localhost:901) to get SWAT going it reports NOT FOUND?

Reading the instructions to get my network going from my 6.06 PC would seem it is easy!

If I look at my network in the browser I see a BT Hub (Broadband) as 'bt' and windows network icons. So Ubuntu is seeing something! If I DClick the windows network after a few seconds it tells me it cannot access it.

Does anyone have an idea why these things are not working?

---

### Post by scrooge_74 on 2007-01-17
you need to enable SWAT in your inetd.conf  if I am not mistaken, check the [samba]("http://www.samba.org") site for more info

---

### Post by happyhacker on 2007-01-18
I'm getting fed up with ubuntu and tempted to load a distro that has samba built in. Anyway, don't know what I'm doing here is my inetd.conf file with SWAT apparently enabled. According to the samba site there should be "SWAT" added t the end so I've done that!

Can someone tell me the next move? SWAT will still not run.

#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
swat		stream	tcp	nowait.400	root	/usr/sbin/tcpd	/usr/sbin/swat swat

---

### Post by scrooge_74 on 2007-01-18
Friend if you use Debian, SAMBA needs to be install and configure just the same.

i personally dont use SWAT anymore, just read the [Howto]("http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/") and make changes directly in /etc/samba/smb.conf , the files comes with a lot of stuff you can make changes and go from there. SAMBA is very subtle and needs to be treated like a pretty girlfriend.

---

### Post by scrooge_74 on 2007-01-19
> **cantthinkofanickname said:**
> I'm getting fed up with ubuntu and tempted to load a distro that has samba built in. Anyway, don't know what I'm doing here is my inetd.conf file with SWAT apparently enabled. According to the samba site there should be "SWAT" added t the end so I've done that!

Can someone tell me the next move? SWAT will still not run.

#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
swat		stream	tcp	nowait.400	root	/usr/sbin/tcpd	/usr/sbin/swat swat

in this thread you may find your answer [http://www.ubuntuforums.org/showthread.php?t=335394](http://www.ubuntuforums.org/showthread.php?t=335394)

---

