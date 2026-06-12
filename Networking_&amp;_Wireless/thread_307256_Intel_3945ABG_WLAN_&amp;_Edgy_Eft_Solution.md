---
title: "Intel 3945ABG WLAN &amp; Edgy Eft Solution"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by ec99210 on 2006-11-26
Hi guys,

I have to tell you that I was pretty reluctant to post this but I think I've depleted both resources and patience ;)

**Problem:** Wireless device Intel PRO/Wireless 3945ABG not working anymore after fiddling with the ipw3945 driver. I read all the readme and INSTALL files I was pointed to and have been trying for a few days... also read other how-to resources but since I am a linux n00b this is a bit overwhelming...

There are a lot of people struggling with this 3945 driver problem from what I gathered while googling and lurking, either because they need WPA working or because their AP doesn't like their wireless device in particular.

If I do "lshw" it shows up but not on the Network Settings GUI menu.

Please tell me what information you would like me to post here, I don't know where to start really :oops: 

Thanks a great lot!

Miguel

---

### Post by zgornel on 2006-11-26
If all modules are loaded, drivers ok, firmware in place, check this: [http://www.ubuntuforums.org/showthread.php?t=306596](http://www.ubuntuforums.org/showthread.php?t=306596)

---

### Post by ec99210 on 2006-11-27
Thanks for that.

My wireless device wasn't showing up on Networks.

I don't know _exactly_ what I did but now its working.

Roughly I think it was this:

-Reinstall kernel, google it, not that hard
-Reinstall ieee drivers, do 'make patch_kernel'
-Install ipw3945, 'make'
-Reboot

Hope it works for you all out there cursing at your screens ;)

---

### Post by Kjow on 2006-11-28
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62452](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62452)

:(

---

