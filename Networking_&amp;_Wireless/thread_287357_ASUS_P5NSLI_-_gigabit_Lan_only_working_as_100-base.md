---
title: "ASUS P5NSLI - gigabit Lan only working as 100-base"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by lordofduct on 2006-10-28
I've got the ASUS P5NSLI, that is with the nForce 570 chipset running a Pentium D processor. The board has onboard gigabit Lan through the Marvell 88E8001 chipset. I also have a Pci-e 1X gigabit NIC in the machine (sorry I have no idea who makes it or anything). Both of which work and all, just only in 100-base. Obviousily I am hooked to a gigabit switch (it's a netgear 16-port switch) and all the machines except my laptop and cable modem are all gigabit (my bedroom computer, this ubuntu machine and a thin client). The bedroom machine which runs Windows connects to the switch as gigabit (it is based on the same chipset as well... it is the asus nforce 490 chipset board that support Code2duo).

I've read around the web and this forum and only find posts and sites about how they are having trouble with ubuntu recognizing and using the Lan. But like I said it works, it just doesn't use gigabit. Does anyone know what may be up?

This is using the latest stable Edgy Eft release on a

ASUS P5NSLI
2.66Ghz Pentium D processor
1GB (2X512MB) DDR2 667
80GB WD SataII
3x 500GB WD SataII drives (fake Raid5)
MSI GeForce 6200

---

### Post by lordofduct on 2006-10-28
Oh I should add, I did have Dapper on this for a couple weeks and washed it for Edgy. When it was Dapper the Gigabit worked for about 2 days and for some reason stopped working on both the Pci-e card and the on board... wtf?

---

### Post by lordofduct on 2006-11-09
Bump

I'm still having problems with this.

Ubuntu recognizes the onboard device, the device manager shows it and considers it a gigabit LAN card. It is a 88E8001 10/100/1000 Mbit card, but for some reason ubuntu only lets it run at 100Mbit (my network has a gigabit switch, and I am talking to computers all running at gigabit speeds). I also have a second card in a PCIe 1X slot that is a SysKonnect SK-9E21D 10/100/1000Base-T, it too is recognized, works but only runs at 100Mbit. I run edgy and have latest upgrades and kernel. Why isn't this working on either card?

---

### Post by lukeo on 2007-02-03
I'd like an answer to this too, can't find much information. My Abit AN8 (Nforce 4 chipset) while the network card works under 6.10 it's so slow, barely getting 7MB a sec. Dual booting XP I get 320mbits or about 40MB a second, this is killing me for transferring large files around.  

Pretty common chipset, any solutions to this?

---

### Post by lukeo on 2007-02-04
Bump! Nforce 4 and it's gigabit network card is pretty common, surely someone here has  solution? tips? advice? repositories? commands? etc etc...

Would be nice to have a full speed network!

---

### Post by lukeo on 2007-02-07
So no one else in the world has there Nforce 4 chipset gigabit lan only running at 100mbits or so? When on the same system dual booting I get 1000mbits. I am not talking about the connection speed reported by device manager or the network icon, it reports a gigabit 1.0Gbps speed, the actual transfer rate is below 8MB/s a second. Same machine, dual booted to Windows XP scores 40-50MB/s. 

I'd like some feedback on this issue if anyone has a solution? Is it driver related? Kernel related? I have no idea I am just throwing out thoughts. Google searching doesnt reveal much, and all the Tutorials just say "Nforce 4 network card works in Ubuntu"... they don't say it works properly or at it's correct transfer speed.

---

### Post by lukeo on 2007-02-11
...

Come on guys, surely you would want your gigabit network to actually work at gigabit speeds? Or is everyone content with slower than 100mbit? Or does everyone else card's on the Nforce 4 chipset actually do gigabit speeds and we are just missing something?

Tips! Help!

Google as I said says nothing much on the subject other than Nforce 4 networking controller is supported. These forums don't seem to have much that is easily brought out in the search either.

---

### Post by lukeo on 2007-02-13
bump...

---

### Post by se1kid on 2008-04-07
Hi - did you get anywhere with this? I've got the same problem with 7.10 and a Marvell 88E8001 chipset. works fine at 100Mb/s, doesn't work at 1000Mb/s.

---

