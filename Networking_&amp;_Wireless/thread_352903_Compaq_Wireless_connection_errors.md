---
title: "Compaq Wireless connection errors"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by hajjamm on 2007-02-03
I have a Compaq Laptop and I just installed Ubuntu on it. I'm not that familiar with this OS but I wanna learn about it. It doesn't seem to connect through the wireless connection, it's Broadcom 4318. Please help me through this problem :(

---

### Post by jml on 2007-02-03
Broadcom cards are notorious for being difficult to set up in Ubuntu and in Linux in general.  Broadcom does little to help the Linux community to write the drivers needed to run their cards under Linux.  If you search this forum for Broadcom and Wireless networking, you will find many posts on the topic to help you.  

In general what you will have to do is to download and install (via add-remove programs, or Synaptic,) an application called ndiswrapper.  Your will need to blacklist (ie inactivate) the Broadcom driver installed by default by Ubuntu, (again searching these forums for the term blacklist and Broadcom should help.)  Then you need to install the Windows driver for the Broadcom card.  This is found on the driver CD that came with your laptop.If you no longer have that CD, you can often download the driver from the manufacturer's web site.  Once the card is recognized, then you will need to configure the card using the network utility.

In my experience, success with the Broadcom card can be hit or miss.  If you try these steps and are not successful, you may want to consider getting a PCMCIA card for your laptop, (one that is supported by Ubuntu/Linux) and try again.  Good luck.  It can be quite a challenge to get wireless working, but once you do, its pretty solid.

Joe

---

