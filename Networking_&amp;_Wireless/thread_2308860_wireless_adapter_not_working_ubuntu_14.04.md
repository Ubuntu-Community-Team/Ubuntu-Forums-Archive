---
title: "wireless adapter not working ubuntu 14.04"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by karra88 on 2016-01-06
I have Lenovo Ideapad Z560 laptop and all of a sudden my wlan stopped working. I have checked with the command "lspci" and there was no listing of wireless interface at all.
Does this mean there is a hardware problem and do i need to change my network interface card ? Is there any way to check the hardware problem ?

I have even tried some random things but nothing worked out. Help me out.

---

### Post by slickymaster on 2016-01-06
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by kc1di on 2016-01-06
please run the following command in a terminal ```
rfkill list all
```
post results here.

---

