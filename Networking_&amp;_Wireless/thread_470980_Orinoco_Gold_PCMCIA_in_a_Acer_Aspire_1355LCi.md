---
title: "Orinoco Gold PCMCIA in a Acer Aspire 1355LCi"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by silkmaze on 2007-06-11
I want to try out Ubuntu on my on my Aspire 1355LCi laptop. I am sure everything will work, from what I have heard and read about the latest Ubuntu version. The only thing I haven't been able to find out anything about is whether it will work flawlessly with my Orinoco Gold PCMCIA wireless card.

At the moment I have Suse 10.1 running on the laptop, and after trying, in vain, to get it to work with the on-board Realtek RTL8180L wirless chipset, I got myself the Orinoco. I pushed into the slot and Suse immediately "saw" it and got on with setting it up. A couple of clicks later and I was online.

Am I going to have a similar experience with Ubuntu, push in the installation CD/DVD, bootup and install the system then get online immediately? Or will it have a problem with the Orinoco?

Thanks.

P.S. Laptop configuration - CPU - AMD XP-M, HDD - 60GB, Graphics - ATI Mobility Radeon 9200, RAM - 1GB, Wireless (built-in) Realtek RTL8180L, PCMCIA - Orinoco Gold (Agere Systems)

---

### Post by cantormath on 2007-06-11
> **silkmaze said:**
> I want to try out Ubuntu on my on my Aspire 1355LCi laptop. I am sure everything will work, from what I have heard and read about the latest Ubuntu version. The only thing I haven't been able to find out anything about is whether it will work flawlessly with my Orinoco Gold PCMCIA wireless card.

At the moment I have Suse 10.1 running on the laptop, and after trying, in vain, to get it to work with the on-board Realtek RTL8180L wirless chipset, I got myself the Orinoco. I pushed into the slot and Suse immediately "saw" it and got on with setting it up. A couple of clicks later and I was online.

Am I going to have a similar experience with Ubuntu, push in the installation CD/DVD, bootup and install the system then get online immediately? Or will it have a problem with the Orinoco?

Thanks.

P.S. Laptop configuration - CPU - AMD XP-M, HDD - 60GB, Graphics - ATI Mobility Radeon 9200, RAM - 1GB, Wireless (built-in) Realtek RTL8180L, PCMCIA - Orinoco Gold (Agere Systems)

I have that card and it seems to work great out of the box.  If you have issues with the ati card you might want to checkout envy to install the drivers.....google it.  I recommend installing all the video/audio/dvd codecs manually, but if you are lazy you can use Automatix2 or EasyUbuntu, I usually recommend  Automatix2.

---

### Post by chili555 on 2007-06-11
Unless I am mistaken, this is a Prism2/2.5 card. There is a slight problem in that orinoco *and* hostap *and* prism2 drivers load. If you do *lsmod | grep prism* and then add whatever you found to */etc/modprobe.d/blacklist* like this:```
blacklist prism2_cs
```Then, after a reboot, the card will work perfectly.

You may find the module is prism2_pci or prism2_whatever; just blacklist whatever you find.

---

### Post by silkmaze on 2007-06-11
Yeah, if I remember rightly it is a prism 2.5 chipset. Yes I am lazy, and have no idea of how Ubuntu installs so I will be using Automatix2 (whatever that is).

---

