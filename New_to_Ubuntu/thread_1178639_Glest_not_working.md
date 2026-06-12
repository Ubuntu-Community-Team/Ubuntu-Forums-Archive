---
title: "Glest not working???"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Aen2lt on 2009-06-04
OK! so i added the glest game to my applications and a couple other games and all of them are very slow and jumpy.  I have been told this could be because my video card doesn't have a driver... if anyone can give me some help on how to fix this that would be great.  I am new to ubuntu and programming but trying to learn!

---

### Post by durand on 2009-06-04
Go to System > Administration > Hardware Drivers and activate the ones you need.

---

### Post by Aen2lt on 2009-06-04
its blank and says "no proprietary drivers are in use on this system"

---

### Post by durand on 2009-06-04
Open a terminal (Applications > Accesories > Terminal). Type lspci and paste the output here.

---

### Post by Aen2lt on 2009-06-04
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0c.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
00:0c.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
00:0c.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:0c.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
00:0c.4 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
00:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller (rev 01)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:13.0 USB Controller: NEC Corporation USB (rev 41)
00:13.1 USB Controller: NEC Corporation USB (rev 41)
00:13.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
06:00.0 Network controller: RaLink RT2600 802.11 MIMO

---

### Post by durand on 2009-06-04
Hmm, you have an ATI graphics card. I have no experience there so maybe someone else will be able to help..

---

### Post by Aen2lt on 2009-06-04
yes i hope so

---

### Post by neo.patrix on 2009-06-05
Hi,

a) You can check AMD/ATI website to see if your card falls under "Legacy" category. 

b) Are you using Jaunty?

c) What does output from command "fglrxinfo" say? 

Glest is a 3D game, which means you will need a proprietary driver most probably supplied by ATI directly or Ubuntu Restricted (better option).

Please check [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

Since ATI Graphic Card & Driver stuff is ever very hot topic on Ubuntu Forums , you can surely find lot of threads related to it.

---

