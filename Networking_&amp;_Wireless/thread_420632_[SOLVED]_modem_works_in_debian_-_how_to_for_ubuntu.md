---
title: "[SOLVED] modem works in debian - how to for ubuntu"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by jludeman on 2007-04-23
I have an older modem on my desktop which is a hardware modem.
Under debian I do the following to make it work.

1. cd /dev
2../MAKEDEV -v /dev/ttys4
3. setserial /dev/ttys4 port 0x**** irq * uart 16550A - port and irq found with lpci -vv uart found with dmesg
4. setserail -g ttys4 - confirms the above

Using the live cd I have two problems:
 ./MAKEDEV fails because of udev
setserial does not exist - I cannot get it without a modem

I'm unsure whether to install Ubuntu to the hard drive because I don't know whether setserial will be available after the install. 

Is setserial available after a hard drive install?
Will makedev work after a hard drive install?

---

### Post by mainely_linux on 2007-04-23
Did you check the output of dmesg?  The live cd is most likely detecting your hardware modem automatically.  MAKEDEV is available, but setserial isnt installed by default.

---

### Post by jludeman on 2007-04-29
I went ahead and installed 6.10. A little research led me to discover tha udev had already symbolically linked my hardware modem to ttyS2. Set pppconfig to ttyS2 and dialed into the ISP no problem.

I was using Debian under the 2.4 kernel before.

---

### Post by jludeman on 2007-11-07
I got this one solved under 7.04. For a detailed explanation see the link below.
[http://ubuntuforums.org/showthread.php?t=587560](http://ubuntuforums.org/showthread.php?t=587560)

---

