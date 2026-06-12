---
title: "How to configure my dell wireless card"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by oby1 on 2010-05-04
Hi Guys,

I am relatively new to linux. I just installed Ubuntu 10.04 but I can't seem to get wireless internet access. I use a dell inspiron 1525, and with Broadcom Corp BCM 4312 802.11b/g card. I havent found any posts that make sense to me, and the ones I have tried have not worked. Please Help. I can't use my OS without internet.

---

### Post by oby1 on 2010-05-04
> **oby1 said:**
> Hi Guys,

I am relatively new to linux. I just installed Ubuntu 10.04 but I can't seem to get wireless internet access. I use a dell inspiron 1525, and with Broadcom Corp BCM 4312 802.11b/g card. I havent found any posts that make sense to me, and the ones I have tried have not worked. Please Help. I can't use my OS without internet.

thanks

---

### Post by Hospadar on 2010-05-04
What is probably most likely to work:

1) get a network connection somehow - either an ethernet cable, or borrow a usb wifi card from someone (a card that works with ubuntu right out of the box), or whatever.  It might be possible that you don't need a network connection, and you can use the software on the ubuntu cd.  Try sticking in an ubuntu cd after you boot up, Go to System-Administration-Software Sources  in one of these tabs there should be a checkbox that will enable use of the cd as a software source (I'm not sure that will actually help, just a guess, probably worth trying if a network connection is not an option)

2) Go to the driver manager, this is a tool for installing hardware drivers that are not installed by default (generally for legal reasons, sometimes because there may be an option between different hardware drivers), you'll find it in System-Administration-Hardware Drivers.  When you open it up, it should do a little scan and let you know that there are some drivers available.  One of these will probably be the broadcom STA driver (which is developed and released by broadcom), that would be your first choice.  There is also an open source driver available (I forget it's name), which works fine too, but I heard it was a little slower in some cases.  I'd try the STA driver first, and if it doesn't work, try the other.  You will probably have to/want to restart after installation.

If the hardware driver manager doesn't help, we'll need to dig a little deeper.  If you still don't have success after steps one and two, try running (and posting the output of) the following commands when run in a terminal (Applications-Accesories-Terminal, you should be able to copy-paste the whole block, if  not, do them one at a time,  the stuff after '#' are comments, you can paste them in with the command or not, the terminal will ignore them):
```

sudo lshw -C network #display info about networking hardware
lspci  #PCI bus information
ifconfig #general networking info
iwconfig #wireless-specific network info
lsmod  #information about which kernel modules (drivers are kernel modules) you have loaded

```

---

### Post by Megaptera on 2010-05-04
I know this talks about Dell Minis but I've used it on my Dell laptop with 9.10 and 10.04 with no probs a simple effective solution on my system.
Don't forget to reboot afterwards though

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

