---
title: "RTL8185L not working"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by dc740 on 2008-02-04
Hello, this is my first post, I always use google before asking, but this is too much for me, I mailed Realtek about this but they didn't even bother to reply, this is the mail with the problem:


> Hello, I'm using a Realtek RTL8185L based card (EDIMAX 7326lG) under windows XP (32 bits) but I can't use it under Vista Ultimate x64 (fully updated) and XUbuntu (32 bits) (also updated).

I'm using a WEP key (128bits/hex) and a hidden SSID. I'm taking all the needed information from a text file, so I'm REALLY sure that it's not a typo problem with the wep key... I connected 3 winxp computers with the 8185L and one Vista Starter 32bits using Realtek 8187.

under vista and using the latest drivers from [www.realtek.com.tw](www.realtek.com.tw) (ver.1097) the card can't associate to the router, it gives me an unknow error, and trying to fix the problem automatically using Vista is useless, it complains that it can't associate to the router be cause it's on a hidden net (I use a Spanish version of vista so I don't know if it's the correct translation)

I can't give more details about the Vista problem, I'm following the same steps on all the machines, but it just doesn't associate under Win Vista Ultimate x64 with all the updates installed (it finds the wireless network anyway).

about XUbuntu, i tried using the graphical wireless manager after installing the realtek drivers (1027) and running ./wlan0up successfully, using the 'dmesg' command I can see that the card is associated and using B rates. but I can't ping anything, so i tried setting the ssid and wep key manually using iwconfig, then setting the ips manually using ipconfig (using the root account of course). the card is listed under iwconfig, also the ssid is shown, but I think that the wep key is not being set. and I'm sure I set it, I did it manually about 5 times but it just doesn't appear on iwconfig, maybe that is the problem? how can i solve it? can you give me a solution?

Since the card (I tried different 8185L cards be cause I own three of them) it's not working under Vista and XUbuntu I think that maybe it's a driver related problem with WEP or something


thanks for your time.



I also tried this : [http://ubuntuforums.org/showthread.php?t=555526](http://ubuntuforums.org/showthread.php?t=555526) seems like a similar problem


ANY suggestion is welcome :(

thanks!

---

### Post by alan34 on 2008-02-04
Could look at this might help

[http://ubuntuforums.org/showthread.php?t=646320](http://ubuntuforums.org/showthread.php?t=646320)

I have got a realtek rtl8185 card and this is what worked for me.

---

### Post by dc740 on 2008-02-04
yes, I tried ndiswrapper first than anything else, but it didn't work, so I uninstalled it and installed the native realtek drivers... this is so frustating! :(

---

### Post by squell on 2008-03-31
[https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/176507](https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/176507)

This device should now work in Fedora 9... can we include it in Hardy?

---

### Post by jlauio on 2008-05-12
Hi.
I find a howto where you can download the modules to the wireless card rtl8185.

[URL="http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy"]http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy
[/URL]

I have a Gateway MT3422 with Hardy amd64 and found ok.
Good luck.

---

