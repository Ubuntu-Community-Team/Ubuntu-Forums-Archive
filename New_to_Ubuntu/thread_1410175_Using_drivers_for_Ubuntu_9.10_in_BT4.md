---
title: "Using drivers for Ubuntu 9.10 in BT4?"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by zee999 on 2010-02-18
Hello everyone and thanks for having me.  I've been reading through a lot of posts here and the amount of information shared is unbelievable.  I consider myself extremely green to linux but with the help of reading the forums I'm starting to pickup a few things.

There is one thing I just can't seem to wrap my head around.  I set my system up for triple boot using grub (Ubuntu/BT4/Vista) and things have been going well except for the internal mini pci card's wireless drivers.  In Ubuntu the card is recognized as a Broadcom 4322 (432b, a/b/g/n, rev 01) and required me to download the proprietary drivers to make it functional.  I downloaded the drivers linux STA drivers from broadcom and everything is working good for Ubuntu.  

In BT4 I can't seem to get the card working.  I've tried downloading and installing the drivers from the broadcom site and things just won't work.  I have the mod loaded and have blacklisted the modules that could cause problems but the card just won't come up.

I understand that I can't simply copy the drivers from Ubuntu and move them over to BT4; they kernel sources have to be recompiled under BT4.  Is it possible for me to extract the files from Ubuntu so that I can move them to BT4 and compile them there?

I'm just getting a bit frustrated.  I noticed that in Ubuntu the drivers that are being used are v5.10.91.9 but the drivers that are available from the broadcom site are listed as v5.60.48.36; I'm wondering if the older driver is needed? And that is why downloading the current isn't working?

If anyone has come across a solution on how to get these troublesome cards to work that would be great.

I understand that this card will not be able to monitor or inject.  I just want to be able to connect to my wireless ap.  

Thanks.

---

### Post by cariboo on 2010-02-18
Check see what driver you are using in Karmic(9.10), open a terminal and type:

```
lsmod | grep b43
```

I have a Broadcom 4312 chip in my netbook, it uses the wl(st) driver. Regardless Broadcom isn't well supported in BT4. I have a USB wireless device that I know works, and have used that with BT4. It may be worth your while to buy an inexpensive usb wireless device to use BT4. Make sure it says on the box that it will work with at least Windows/OS X. If you buy one that says Windows only, you won't be able to get it to work.

---

### Post by jeanf73 on 2010-06-13
I have the same problem!  Did you find a solution?  Jean

---

