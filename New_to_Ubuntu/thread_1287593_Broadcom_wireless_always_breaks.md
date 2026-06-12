---
title: "Broadcom wireless always breaks"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-10-10
I was running Ubuntu 9.04, then JoliCloud and my wireless worked just fine.  As with almost every other time I have tried to install a beta version of Ubuntu, I had trouble with the Broadcom wireless drivers in my system this time.  

1)  When I boot from a Karmic live USB, I can enable the restricted hardware for my wireless card, and I can connect to networks.

2)  After a clean install from the SAME USB drive, there are no restricted hardware drivers available.

WHY DOES THIS KEEP HAPPENING TO ME!!!   Isn't the live USB the same as the install?

I don't have a wired connection, so I can't connect other than through the live USB.

What can I do?

---

### Post by Bartender on 2009-10-10
Replace that crap Broadcom card with an Intel card.  It's not hard, nor very expensive.

---

### Post by brandoncolorado on 2009-10-10
> **Bartender said:**
> Replace that crap Broadcom card with an Intel card.  It's not hard, nor very expensive.

It is harder on my netbook, and it is frustrating because I bought the netbook from HP with linux pre-installed.

---

### Post by sandyd on 2009-10-10
try doing
```

sudo apt-get install bcm-fwcutter

```
select "yes" when it asks if you wanna download firmware.

---

### Post by brandoncolorado on 2009-10-11
> **carlee said:**
> try doing
```

sudo apt-get install bcm-fwcutter

```
select "yes" when it asks if you wanna download firmware.

Thanks, I'll give that a try.

---

### Post by anewguy on 2009-10-11
That assumes that without the wireless working you still have a hard wired connection.  If not, please let us know.

Dave :)

---

### Post by brandoncolorado on 2009-10-11
> **anewguy said:**
> That assumes that without the wireless working you still have a hard wired connection.  If not, please let us know.

Dave :)

Unfortunately, this netbook does not have a wired connection.  I would hate to have to buy a USB ethernet for this.

---

### Post by anewguy on 2009-10-11
Do you have a CD drive you can attach to the netbook?

Do you have another computer (doesn't have to be Linux) with which you can access the internet?

Dave :)

---

### Post by brandoncolorado on 2009-10-11
> **anewguy said:**
> Do you have a CD drive you can attach to the netbook?

Do you have another computer (doesn't have to be Linux) with which you can access the internet?

Dave :)

I do have another computer with internet access.  I have a USB drive I can use to shuttle files.  I guess my biggest problem is finding out where to download the files (usually I use synaptic).

---

### Post by brandoncolorado on 2009-10-11
*UPDATE*

I was able to work around this problem.  For anyone else who encounters the similar problem, I was able to get wireless to work in Karmic beta by upgrading from Jaunty.  Whereas the Karmic installation will not install the broadcom drivers, for some reason the Live Karmic and the upgraded Karmic will support the broadcom without any additional steps.

Thanks!

---

### Post by Jack-87 on 2009-10-11
> **anewguy said:**
> That assumes that without the wireless working you still have a hard wired connection.  If not, please let us know.

Dave :)
 I to have a similar issue i am running ubuntu remix on my acer aspire one which has a broadcom wifi card (i switched stock card so osx86 would have wifi) and i am unable to see wireless networks even after activating the broadcom drivers. Any ideas that might help?

---

### Post by Jack-87 on 2009-10-11
Okay i found an extremely simple solution to getting my broadcom wifi card to work. 

**NOTE:**You do in fact need internet connection via Ethernet or the use of a device such as [this one]("http://www.dlink.com/products/?pid=346") which takes wifi signal and turns it into Ethernet (Pretty cool stuff I picked it up a few days ago for the hell of it already came in handy). 

*[SIZE="1"]So this may not be any use to the OP since he has no source for internet other then wifi. (luckily looks like he found a solution that worked for him)[/SIZE]*

1. Go to System>Administration>Software Sources
2. Under the Update Tab Place check mark next to Unsupported updates (jaunty-backports) then hit Close>Redo
3. When complete Update Manager will pop up you may close it.
4. Go to System>Administration>Synamptic Package Manager
5. Search and install  *linux-backports-modules-jaunty* from the package list
6. Reboot
7. Go to System>Administration>Hardware Drivers
8. Select the Broadcom Wifi driver and click Activate if there is two choices pick the B43 option. (I had to do it twice it didn't stick the first time)

Your Broadcom Wifi card should be fully functional now clicking on list of networks up on top of the screen next to the clock should reveal your near by wireless networks.

---

