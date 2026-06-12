---
title: "Preparing to go wireless"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by will_s2 on 2015-04-22
Looks like I will be getting a ASUS RT-AC68U Dual Band Wireless AC1900 Router                                                and an ASUS USB-AC55 Dual Band Wireless AC1300 USB 3.0 Adapter                                                ( fibre will be available in the next 8 weeks ) and I was wondering how these will go with Ubuntu 14.04 LTS. Now I tried wireless before and couldnt get it working and finally gave up and have an ugly cat cable that connects........and now I want a nice simple wireless connection. 

And before I get these devices I want to find out if they work in Ubuntu, how easy they are to install and other tips even if a different network adapter  would work better...........and the thing is I am not much better then a novice when it comes to linux. Basically its my secured banking PC........and other important stuff



btw: when the fibre is finally tuned on I want to be ready to get everything working as smooth as possible and as early.   Have been talking to others about providers etc

---

### Post by ajgreeny on 2015-04-22
What chipset does the adapter use?

Let's see the output of **lsusb** in terminal with the adapter attached, or if you haven't got it yet, ask the supplier if they know what it is.

---

### Post by will_s2 on 2015-04-23
[I]5th generation 802.11ac chipset gives you dual-band 2.4 GHz / 5 GHz for up to super-fast 867 Mbps
256QAM technology increases wireless-N data rate from 300 Mbps to 400 Mbps for 33% faster performance
Selectable 5 GHz /2 .4 GHz dual bands increase signal clarity for better HD multimedia
USB 3.0 connection for high-performance wireless networking with desktop and notebook PCs[/I]

have googled and googled and asked and received this reply from dealer.....maybe go to another dealer

I noticed they they have use only for Win7, Win8 and Win 8.1


maybe go with something different...any ideas on a high speed wireless adapter that is is easy to install on Linux ?

---

### Post by ajgreeny on 2015-04-24
That is a fairly expected answer from a dealer but is not any help to us, l'm afaid.
Often wireless adapters will work OTB using the kernel drivers and can be exchanged after purchase relatively easily, though that my be a warranty problem, of course.
Alternatively you could look into a mini USB adapter with known linux support.

---

### Post by will_s2 on 2015-04-25
well with ultra fast internet speeds I want an adapter that will provide very fast wireless performance for both windows and ununtu

even on the asus site it doesnt name the chipset and only mentions windows support



so do you know a brand or specific product that works well with linux.......

---

### Post by Bucky Ball on 2015-04-25
Most things Realtek or Broadcom work fine. A matter of finding which chips are in what dongles. Often the brand of the USB dongle has nothing whatever to do with the manufacturer of the wireless chipset inside it.

If you want to know what wireless cards and dongles work with Ubuntu, why not do a little research and let your fingers do the walking:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

