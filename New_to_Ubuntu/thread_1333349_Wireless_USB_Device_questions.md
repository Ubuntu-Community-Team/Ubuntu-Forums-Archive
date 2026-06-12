---
title: "Wireless USB Device questions"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by ubume2 on 2009-11-21
I have intermittent wireless internet connection on 8.04. I use a Belkin 5FD7050 v 4000 usb device on my desktop. From lsusb it is:  **ID 050d:705c Belkin Components**.  
  On 8.04 I had to add a script to /etc/rc.local to get an automatic startup(following howto's by kevdog & wieman). I never could get gnome network manager to work.  When I used it the system would freeze. 

After the computer is shutdown for a while and booting 8.04, it is hit and miss whether I have an internet connection.  If I go to 9.04 and 9.10 and then boot to 8.04, I then can usually get a connection.  When **I DO** get a connection, I have a solid connection. When I don't get a connection the device does not show up on **lsusb** ,and **lshw -C network** does not show my eth1 wireless.

It seems that my usb device is "lazy" or "sleepy" when it comes to 8.04.

On 8.04, I never could get gnome network manager to work. Usually froze the system.

**Are there known drivers that might conflict with my driver?  What would I need to blacklist?**

---

### Post by ubume2 on 2009-11-22
bump. 

> **ubume2 said:**
> **Are there known drivers that might conflict with my driver?  What would I need to blacklist?**

---

### Post by S1lverado on 2009-11-22
Ive been reading a help document, WifiDocs/Driver/Ndiswrapper, found herein on the site and it too speaks of blacklisting.  A "why explaination" as to why this is necessary would have been helpful.
I cant imagine why some other device would use the bcm43* driver.

Im so new my umbilical cord has yet to dry up.

> ... I had to add a script to /etc/rc.local to get an automatic startup(following howto's by kevdog & wieman).a link to this howto may be just what I need to get my rtl8187 wlan driver working.  Although, this particular driver Im led to be believe is "native" with 9.04.  Nonetheless it, Starbase PT-H9D doesnt work.  I have the CD with a driver and what is identified as an outdated driver, but unlike Windows, it wont work as is.  I suppose becasue the kernel has a newer driver but why wont Ubuntu recognize the device if a latest driver is within the kernel.  

I may never get the cord cut.

---

### Post by ubume2 on 2009-11-22
> **S1lverado said:**
> Ive been reading a help document, WifiDocs/Driver/Ndiswrapper, found herein on the site and it too speaks of blacklisting.  A "why explaination" as to why this is necessary would have been helpful.
I cant imagine why some other device would use the bcm43* driver.

Yes, I just blacklist. Don't know why. Can't find an explanation. I have two 900 page manuals on linux and Ubuntu. Nothing! I found the device driver for my usb device by using modprobe -r [device name]. I had a connection. After I modprobed, I lost connection instantly. Luckily I read the manpage on modprobe and got the connection back.  Good luck on broadcom devices.

I started with Ubuntu 6.04? and wireless support was terrible.  It isnt too bad on 9.04 or 9.10. Wireless support hasn't been Ubuntu's strong suit, but it is improving dramatically.

I still am wondering if there is another driver in there that [sometimes] conflicts with my zd1211rw.

Edit: After getting no real response on this, and posting on another linux forum, it seems that getting wireless sometimes is just plain luck.  8.04 is a dramatic improvement over Dapper. Jaunty improves over Hardy, and Karmic is even better.  Will eventually transition totally to Karmic or the next LTS.  Messing around with the kernel is above my head, and will let the developers handle it. Mark this as solved, even though I really do still want to know.

---

