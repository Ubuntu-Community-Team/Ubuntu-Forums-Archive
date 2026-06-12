---
title: "Need help connecting to wireless- jaunty, bcm4328, macbook 4.1"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by confused_person on 2009-07-24
Hi there, I'm a complete linux/ubuntu newbie here (just installed it 2 days ago) and I'm not especially computer-savvy anyway so I don't really know what I'm doing...

Currently I'm connected without any problems using an ethernet cable. But of course, laptops portable and I'd really like to be able to use wireless.

I've been researching how to for hours and hours to no avail (although admittedly I don't always understand the pages). Everyone is suggesting different things and I can't really find one coherent (at least for me) explanation.

What I've tried so far:

-Manually adding the wireless network information and password into network connections. It doesn't connect to it when I unplug ethernet.

-Downloaded the program "wifi-radar to see if it could detect the network automatically. However, the program itself refuses to start in GUI (no error messages- just nothing happens) and if I try to run it via terminal I get the message "No wifi-device found. Exting." (I'm supposing this lack of device is the main problem, but I don't know what to do from there)

-Downloaded ndiswrapper; however, attempts to find these mysterious INF files were fruitless and clicking on "configure network" yields error message "could not find a network configuration tool". 

Some background information:

-Ubuntu version: 9.04 Jaunty Jackalope
-Wireless brand: Broadcom BCM4328
-Router: Linksys WRT54G
-Laptop: Macbook 4.1

I'm totally new at this so GUI-based suggestions (or very spelled-out terminal ones) would be most helpful. Thanks for your patience!

---

### Post by LookTJ on 2009-07-24
Did you try enabling the restricted driver?

---

### Post by confused_person on 2009-07-24
> **LookTJ said:**
> Did you try enabling the restricted driver?

According to system->administration->hardware drivers, my broadcom STA wireless driver is activated but not in use. I'm not sure if that answers your question though.

---

### Post by LewRockwell on 2009-07-24
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857)

[http://ubuntuforums.org/showthread.php?t=1134631](http://ubuntuforums.org/showthread.php?t=1134631)

.

---

### Post by confused_person on 2009-07-24
> **LewRockwell said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/365857)

[http://ubuntuforums.org/showthread.php?t=1134631](http://ubuntuforums.org/showthread.php?t=1134631)

.

Oh my goodness! This will hopefully be the solution to my problem- many thanks :D Silly question, though: how do I turn the wireless radio on/off? My macbook doesn't have a physical wireless switch like my last laptop did and I'm not sure how to do it in ubuntu yet.

---

### Post by LewRockwell on 2009-07-24
mac no switchy...

.

---

### Post by confused_person on 2009-07-24
> **LewRockwell said:**
> mac no switchy...

.

Uh oh, is there any way to enable/disable via gui/terminal? Or if that's not possible either, is there a way to work around that step and still get it to work?

---

### Post by confused_person on 2009-07-26
Update: This solved my problem completely without having to deal with my nonexistent wireless switch: [http://www.bluebottle.net.au/blog/2009/broadcom-bcm4328-on-ubuntu-904-jaunty](http://www.bluebottle.net.au/blog/2009/broadcom-bcm4328-on-ubuntu-904-jaunty)

---

