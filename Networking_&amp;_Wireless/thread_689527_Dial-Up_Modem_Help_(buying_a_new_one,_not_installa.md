---
title: "Dial-Up Modem Help (buying a new one, not installation difficulties)"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by danny86 on 2008-02-06
Hello everyone! First I want to thank you for even reading this post in the first place. I am a complete newbie when it comes to Linux and Ubuntu. Recently I have had an old desktop pc given to me and I have decided I would like to try out the whole open source thing and see how it works out for me. My question for all of you is I need to purchase a new dial-up modem because the current one in it no longer works. Seeing as how I am going to install Linux on the computer I was wondering what would be the best PCI modem I can purchase for it that I can use with Ubuntu and has drivers that hopefully runs on V92. I already checked with my ISP and their dialup software works with Linux, so my only issue right now to trying to decide on the best modem for the job. Thank you again for taking the time to help someone still stuck in the slow speed dial-up stage of life.

---

### Post by jan quark on 2008-02-07
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

[http://ubuntuforums.org/showthread.php?t=497181](http://ubuntuforums.org/showthread.php?t=497181)

I think an intel modem wouldn't be a bad idea because the drivers are prepared in a deb package. only double-click and they install

but I am not an expert in this field :)

[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)

---

### Post by Bartender on 2008-02-07
The best, most trouble-free, modem is not PCI.  Scrounge up a serial external modem like a US Robotics 5686.  The US Robotics full-hardware internal should work in Linux but I've read lots of posts claiming that it gave them trouble.

---

### Post by strangerep on 2008-02-07
> **Bartender said:**
> The best, most trouble-free, modem is not PCI.  Scrounge up a serial external modem like a US Robotics 5686.  The US Robotics full-hardware internal should work in Linux but I've read lots of posts claiming that it gave them trouble.

The Dynalink E-modem II and E-modem III work perfectly. I've used the former on both
old and new boxes, and the latter on my newer box.
(I.e., they're full hardware external serial modems.)

To the OP: Cough up the (modest) extra money for a full hardware external serial
modem. The internal jobbies cause no end of grief because they usually require
drivers to be installed.

You said you're a Linux/Ubuntu newbie. That means you'll probably have a bit of
difficulty to install and configure. But if you have a full hardware external serial modem,
at least you'll know that any such problems are not caused by it.

---

### Post by Bartender on 2008-02-09
danny, you didn't say where you're from.  Here in the US of A, it's relatively easy to find used external hardware modems.  A brand new US Robotics external is ridiculously expensive.  I've scrounged up a half dozen of them from eBay and craigslist for no more than about $12 each.
I suspect it may not be that easy if you live in Nepal, or some other lovely corner of the planet that isn't as "developed".
If you can get your hands on a serial modem but have a computer with USB, one of [these]("http://www.directron.com/sbtusc1m.html") works dandy.  Don't worry that it doesn't say "compatible with Linux", I've got one and it's recognized automatically by modern Linux kernel.

---

