---
title: "windows box"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Bigtrigger on 2007-11-09
I have a windows box and a 50/50 box lol 

the 50/50 box has win xp install on one hd with linux installed on the other . 

i am able to share files from my windows machine to the linux box without a problem .

how do i get my windows box to see the linux shared folders ?

---

### Post by SpiritIsReality on 2007-11-10
howdy
I haven't quite got the hang of the samba dance yet.
I've had the most success with the first link. Your mileage may vary.
With his smb.conf file, I had to put the comments on a line of their own, and the testparm said it was ignoring Public, which I used as a share directory.
I don't know if it's correct, but I uninstalled Firestarter after.
[http://ubuntuforums.org/showthread.php?t=528592](http://ubuntuforums.org/showthread.php?t=528592)
[http://screencasts.ubuntu.com/SAMBA_Filesharing](http://screencasts.ubuntu.com/SAMBA_Filesharing)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
trails

HermanAB ... thanks
[http://us1.samba.org/samba/](http://us1.samba.org/samba/)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by HermanAB on 2007-11-10
Go to the Samba web site and read the Official Howto.  It has specific examples for each situation.

Cheers,

Herman

---

### Post by Bigtrigger on 2007-11-10
Thanks for the great info guys ill check it out  .

---

