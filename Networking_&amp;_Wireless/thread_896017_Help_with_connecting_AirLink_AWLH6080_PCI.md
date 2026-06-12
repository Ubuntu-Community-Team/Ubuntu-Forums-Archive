---
title: "Help with connecting AirLink AWLH6080 PCI"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by jimperphonic on 2008-08-20
Hi everyone,

This is my first post as I'm brand new to the world of Linux. I've used Windows operating systems, unfortunately, for the past 15 years (the past 8 professionally). Needless to say I am accustomed to more than a few headaches. Anyhow, down to business:

I've installed an AirLink Wireless PCI Adapter on my desktop system and had success with it in the Windows XP environment. However, I have since converted the system over to an Ubuntu only boot. There is no Linux driver for the Adapter, but after much research I've found that people are in fact able to get these cards to work. The card is being recognized and it even picks up my router, however since I'm using WPA encription it's just failing to connect to it. I've tried a number of procedures including network manager, ndiswrapper and wpasupplicant all to no avail.

If someone would be willing to do a walk through with me on this one, since I'm a total Linux novice at this point in time, I would greatly appreciate it! 

My terminal window is eagerly awaiting your commands...

Thanks in advance,

B

---

### Post by jimperphonic on 2008-08-21
Anyone care to help me tackle this one?

---

### Post by jimperphonic on 2008-08-21
Still hoping someone would be willing to help me troubleshoot this...

---

### Post by stuartnolan on 2008-08-22
Sorry I can't help with the troubleshooting, but I can tell you what works with Hardy "out of the box" an Airlink AWLH4130.  I too am a first-timer with Linux, but my non-Linux experience goes back to the CPM OS.  Like you, I've been struggling with a Belkin card that is reported in this forum to work using ndiswrapper, Windows drivers etc. After several days of tracing and retracing my steps I decided that the Belkin card might work in some machines, but NOT IN MINE!  Then took coward's way out and installed the Airlink 4130 (recommended in this forum) and all has worked perfectly ever since.

---

### Post by jimperphonic on 2008-08-23
thanks for the response stuartnolan! i'm about to take the coward way out as well. i've been able to get all of my systems online except for the one with the airlink awlh6080. it's been extremely frustrating to say the least. i continue to work with it, but with no success. 

i guess it's time to decide if i want to pursue other cards or not...it's to the point to where it's not worth the wasted time.

---

### Post by rezerected on 2008-08-24
FWIW, I've been having the same problems with both the USB and Cardbus adapter.

The hardware is detected and the card can pick up networks, but the only way I can get it to work is if I don't use any wireless encryption at all, which obviously is not going to be a smart workaround.

I'm wishing for someone to come out with a fix, but most likely I'll just have to buy another card.  Good thing the AirLink101 cards are cheap!

---

