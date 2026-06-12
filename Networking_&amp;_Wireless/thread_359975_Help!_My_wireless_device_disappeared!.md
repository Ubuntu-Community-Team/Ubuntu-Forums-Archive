---
title: "Help! My wireless device disappeared!"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by InsanePenguin08 on 2007-02-12
So my parents got me the WUSB54GC wireless adaptor for Christmas...  

So I spend a whole lot of time compilining and installing the new drivers...

So I get really excited to use it....

But wait! No! Suddenly it won't show up anymore! I tried:
lsusb;
lsusb -v;
dmesg;
dmesg | tail;

It just seems to have disappeared!  It did show up before, I had just checked lsusb because I was curious, but now it's not there.  Also, I thought I had stepped on it by accident except for the fact that it shows up perfectly in my iMac G5!  

ARGH! To say the least.  Please, for the love of all that is good in this world, help me find my invisible wireless adaptor!

Thanks!
/IP

---

### Post by spd106 on 2007-02-12
Because of the kernel ABI changes you will have to recompile your driver module for the new 2.6.17-11 kernel. You should be able to boot the old kernel from grub in the mean time. Press escape at the grub load screen and select the Ubuntu 2.6.17-10-generic option. 

See [http://www.ubuntuforums.org/announcement.php?f=140](http://www.ubuntuforums.org/announcement.php?f=140)

---

### Post by InsanePenguin08 on 2007-02-12
Okay, well I don't necessarily see what that has to do with my problem because I haven't changed anything at all since I tried the device the first time, which was only a couple of weeks ago.  Am I wrong in thinking that?  Also, how do I make sure to compile the module with the new kernel number?  

If this is the case, why does my USB-wireless mouse and keyboard work just fine?

---

### Post by spd106 on 2007-02-12
Sorry, I was a bit too hasty to blame the recent kernel updates, so I missed the fact that you are enable to see the device with lsusb.

Can you see anything with **sudo lshw -C network**? (Unlikely) 

When it's inserted are there any lights flashing or does it cause any messages in the /var/log/sysylog?

---

