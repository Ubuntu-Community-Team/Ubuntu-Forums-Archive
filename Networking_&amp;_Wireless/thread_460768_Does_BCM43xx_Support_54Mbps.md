---
title: "Does BCM43xx Support 54Mbps?"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by MrObvious on 2007-06-01
I was wondering as I've been doing some research into it but no definitive answers as of yet.

---

### Post by Kobalt on 2007-06-01
Suposedly yes. But I never got it passed 11Mb/s on my bcm4311...

---

### Post by mozetti on 2007-06-01
I've only seen reference to the fact that it tops out at 11 Mb/s. But, I may not have seen everything.

---

### Post by MrObvious on 2007-06-01
I've been doing some research into it and apparently the Ubuntu implementation of it only allows for 11 Megs because it's not that well built. The only way to update it is to get the 2.6.21 kernel and build it yourself, which I'm not up for. I'm not really in the mood for building a kernel so I can live with it. However it is annoying. If anyone has any other suggestions please reply.

---

### Post by sinbad#1 on 2007-06-02
Hi used to run windows 2000 with my wireless card and i usually got around 54mb/s now with ubuntu i only get 11mb/s!

---

### Post by kevdog on 2007-06-02
What are you using to detect the speed of your network??

---

### Post by kevdog on 2007-06-02
Using iwlist wlan0 bitrate -- Ive discovered that my wireless network with the bcm43xx driver only runs at 11 Mb/s too!!   That sucks!!

---

### Post by DRHamp on 2007-06-03
I'm running a Netgear WG511T with Atheros AR5212   -- It's a wireless G capable card.

I've only run Feisty on my laptop -- It connects as Wireless b -- 11Mbps.

I suspect that Ubuntu only supports 11Mbps -- I don't know that, but thats the way it appears.

I'm very new to linux/ubuntu -- and there may be a setting that I'm not aware of.

---

### Post by MrObvious on 2007-06-07
I actually contacted some people who write the BCM driver and the Ubuntu version is crapped. So I guess we'll wait until this fall when we get the new Ubuntu.

---

### Post by kevdog on 2007-06-07
Supposedly there is a better working version with upgrades for Fedora.  Debian installation however isnt possible at this time.

---

### Post by chanhdat on 2007-12-31
Hello, I got a 24 Mbps with bcm4309 on my Inspiron 9100 by using[ this]("http://bookofme.googlepages.com/bcm43xx_compwiz18.1-all.deb")
But can not get a 54 Mbps speed. Try some different ways up to now.

---

### Post by lonniehenry on 2007-12-31
I believe that you can get 24 Mbps with installing with restricted drives manager in gutsy.  it used to be limited to 11 with older versions of Ubuntu. You can use ndiswrapper to get 54 Mpbs.

---

