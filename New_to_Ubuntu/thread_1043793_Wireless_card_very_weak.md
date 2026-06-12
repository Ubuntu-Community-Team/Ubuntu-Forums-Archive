---
title: "Wireless card very weak"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Xtrme_XJ on 2009-01-18
I am new to Linux, just switched from XP. My wireless card was working in XP fine and I had full strength, Now in Ubuntu I am only getting between 40% and 55% strength and I can tell that my internet is moving really slow.

Any ideas on what I can do to fix this?

---

### Post by handydan918 on 2009-01-18
Since Uri Gellar quite hanging out here, no one else seems to be much good at mind reading, so if you want to post some system specs (lspci is a good start,,,) maybe one of us mere mortals can help..



):P

---

### Post by Xtrme_XJ on 2009-01-18
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
```

hope this helps

---

### Post by handydan918 on 2009-01-20
Have you tried enabling the restricted software repositories? I think that RAlink card uses a proprietary driver.

---

### Post by Xtrme_XJ on 2009-01-20
Yes I did try that

---

