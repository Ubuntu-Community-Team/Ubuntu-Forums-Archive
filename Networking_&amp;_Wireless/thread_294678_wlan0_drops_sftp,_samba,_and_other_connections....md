---
title: "wlan0 drops sftp, samba, and other connections...?"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by sekim27n2 on 2006-11-07
I have installed ubuntu dapper.  I recently purchased a new wireless card ZyXel G102 V2.  I searched long and far and found instructions to install the driver using ndiswrapper.  I was able to get a connection and start browsing the internet.  Yay...

But alas, not all was well with my wlan0.  I decided to try and copy some files over the wireless connection using sftp.  It locked up my friends wireless router...so I figured the problem was with my friends wireless router(Netgear something something..)....so I purchased a new wireless router(Dlink DI-524), and set it up accordingly to use my wireless card using WPA-PSK.

I again tried to use sftp, and the sftp connection would go for so long, and then die.  I could still browse the internet, but that seemed to lag as well.  So I also tried to use samba.  At first Samba would appear to work, but then the connection would time out as well.

NdisWrapper 
===========
utils version: 1.7
driver version: 1.8

Driver for wlan0 card
=====================
net5211 from ZyXel's homepage.



Anyways, wondering if anyone has any idea why my connection is going slow or timing out.

---

### Post by wieman01 on 2006-11-07
Have you disabled IPV6 by chance? Not sure if that adds to your problem, but it's worth a try anyway.

[http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

Also can you check your logfiles?

---

### Post by sekim27n2 on 2006-11-08
Hmm, I think I have located and corrected the problem.  I did a firmware update on my wireless router(DI-524), and the magically disconnects appear to be gone.  Go figure, two router issues. ](*,)

---

