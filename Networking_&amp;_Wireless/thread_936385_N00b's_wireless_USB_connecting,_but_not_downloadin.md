---
title: "N00b's wireless USB connecting, but not downloading"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by stoogiebuncho on 2008-10-02
I'm a n00b, so I'll apologize for that upfront.  I've tried posting about this problem in the absolute beginners forum, but have not had any luck getting people to respond ([http://ubuntuforums.org/showthread.php?p=5895537#post5895537](http://ubuntuforums.org/showthread.php?p=5895537#post5895537)).

I just installed Xubuntu on my parent's laptop.  They have a CompUSA Wireless USB Adapter that worked perfectly right away.  (lsusb lists it as Bus 002 Device 005: ID 148f:2573 Ralink Technology, Corp).  The next day it still worked, but started dropping the connection from time to time.  It would always pick it back up.

The next day it still says it's connected and the signal is strong, but it won't download anything.

I have not tried ndiswrapper or the rt73 driver from serialmonkey, because I haven't been convinced by what I've read that they would help in this case, and since they involve a lot of changing settings in the command line, I'm afraid I wouldn't be able to change things back if it made things worse.

I finally tried a strange sounding fix by robokiller ([http://ubuntuforums.org/showthread.php?t=757607](http://ubuntuforums.org/showthread.php?t=757607)) and set the bit rate to fixed at 11M.  This worked, until I unplugged the USB wireless adapter and plugged it back in.  Now it's back to intermittent connectivity, and sometimes it won't connect at all.  And for some reason, Xubuntu is now using the usb driver for the device instead of the rt73usb driver.

It also seemed to be disconnecting my parent's cordless phone whenever I tried to connect, but that could be a strange coincidence.

I've done a lot of Google searching, and I'm willing to try some of the installation guides like ndiswrapper or serialmonkey's driver, but everything I can find say that this is supposed to work out of the box, so I want to get a second opinion before I try anything too serious.

My parents would probably also be willing to buy a new USB Wireless adapter if they knew that it would work without all the hassle.  They're not that expensive.

Thanks for taking the time to read this.  I really appreciate the Ubuntu community.

---

### Post by Jackie999 on 2008-10-02
I have 2 usb wireless devices. The AWUS036H (rtl8187) and the F5d8053 v3 (rt2870)
Both of them work intermittantly..and I'm beginning to wonder if it's just a fact of life with linux/wireless.  The number of posts going through this networking&wireless forum says it all. I don't think anyone could recommend a foolproof fix..short of running a cable.
I was just reading another post where somebody mentioned a lamp interferring and causing dropping of signal. When you mentioned the cordless phone I wondered if you've stumbled on your answer.

---

### Post by stoogiebuncho on 2008-10-03
Ouch.  That's rough on the laptop community.  But thanks for your response, it's good to hear if only to know that it's not something I'm doing to screw things up.

I've heard that a lot of these problems are fixed in 8.10, which is due to be released at the end of this month.  I usually wait a little while to upgrade to let them work the kinks out, but maybe I'll be an early adapter this time and see if it helps the wireless situation.

---

