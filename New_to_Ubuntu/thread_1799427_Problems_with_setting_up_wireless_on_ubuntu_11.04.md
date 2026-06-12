---
title: "Problems with setting up wireless on ubuntu 11.04"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by MrMittens on 2011-07-07
As the title explains, I am using Ubuntu 11.04 and having problems with using wireless. I've followed some random wiki pages and what not, and have come up with no success. I've installed the STA driver required for my BroadCom wireless card. The exact name escapes me at this moment.

When I boot Ubuntu, it tries to connect to my internet; but fails after about a minute or so.

Any help would be appreciated.

Thanks,

MM

---

### Post by terrykiwi83 on 2011-07-07
Type the following in terminal

```

lshw

```

Also does it show your wireless networks when you click on the wireless icon? if so does it allow you to select and network and enter its security credentials?

---

### Post by wildmanne39 on 2011-07-07
Hi, it also would not hurt to post this information.
```
sudo lshw -C network 
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
Post the outcome here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by mapes12 on 2011-07-09
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29|%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29|%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

and when all else failed I bought a wifi adapter that is natively supported from these guys:-

[http://shop.linuxemporium.co.uk/hardware/hardware-wireless.html](http://shop.linuxemporium.co.uk/hardware/hardware-wireless.html)

Mark

---

### Post by MrMittens on 2011-07-09
I do rather appreciate both your replying to my dilemma, however I have been able to solve this on my own.

So, I shall close this thread as solved.

Thank you for your help.

I shall also post the solution below.

MM

---

### Post by MrMittens on 2011-07-09
Solution is here: [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)

Note, if you have v2 of the BELKIN usb mentioned in the solution, replace every 935a with 935b.

Hope this helps.

MM

---

### Post by wildmanne39 on 2011-07-09
> **MrMittens said:**
> Solution is here: [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)

Note, if you have v2 of the BELKIN usb mentioned in the solution, replace every 935a with 935b.

Hope this helps.

MMHi, your welcome I am glad you got it working.

---

