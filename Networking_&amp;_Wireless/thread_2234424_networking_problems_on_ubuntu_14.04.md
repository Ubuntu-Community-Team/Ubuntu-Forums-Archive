---
title: "networking problems on ubuntu 14.04"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by bryan-welsh-wolf on 2014-07-14
to be specific, I have been having networking problems for quite some time with ubuntu. I had installed 13.10 but the networking would never work, so I reinstalled with 14.04, and at first it appeared to be broken too... however then it started connecting. Now it connects probably 60% of the time, the rest of the time it fails. I have a wireless receiver - Edimax EW-7811UN 150Mbps Wireless Nano USB Adapter - when I look to connect, it always shows my network, it just doens't always succeed in connecting. I have tried going to additional drivers and changing but the options would never change for some reason. I really want to get this sorted, its extremely frustrating and I want to get on with things! help would be greatly appreciated.

---

### Post by varunendra on 2014-07-19
Welcome to the forums bryan!

Your adapter may be using rtl8192cu driver as per the information on [wikidevi]("https://wikidevi.com/wiki/Edimax_EW-7811Un"). To confirm that, open a terminal (Ctrl-Alt-T) and run the following command -
```
nm-tool
```
Apart from other details, it should also show the driver in use. If it is indeed 'rtl8192cu', you may need a patched version of it. Please follow the instructions in this post to install the patched version : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

If the driver is different, or if the patched version is unable to fix the problem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

