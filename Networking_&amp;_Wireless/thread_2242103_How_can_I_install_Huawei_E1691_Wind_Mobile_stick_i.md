---
title: "How can I install Huawei E1691 Wind Mobile stick in ubuntu 12.04?"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by user_linux on 2014-08-30
Hello there,
I am trying to install this broadband internet stick on mu laptop. I have checked that I have usb_modeswitch but for some reason not able to see my broadband stick detected in the networks icon. pls help!
Thank you.

---

### Post by varunendra on 2014-09-02
GSM/3G modem sticks often need multiple unplug -> wait -> replug cycles once they get stuck. It is not uncommon for them to fail to work in the first attempt if you don't give them enough time after plugging in (can be upto 30-40 seconds).

Please take a look at this checklist by praseodym : [http://ubuntuforums.org/showthread.php?t=1831649](http://ubuntuforums.org/showthread.php?t=1831649)

If everything looks okay as per the checklist, unplug the modem (if it is plugged in) > wait about 10 seconds > replug it > wait about 30 seconds > open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands :
```
lsusb
dmesg | tail -40
uname -mr
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

