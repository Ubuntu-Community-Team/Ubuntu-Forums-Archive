---
title: "Atheros card sometimes not detected on bootup"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Tundro Walker on 2007-10-23
I browsed some of the Atheros posts (card not detected, not working, etc), but they seem to be having issues just getting the card to work.

My problem is ... my computer doesn't detect my card at boot sometimes.  When it is detected, wireless works flawlessly, though.

Here's my card from the "lspci" query...

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
**00:0b.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)**
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
```So, sometimes I boot, and the cards detected and wireless works fine.  Other times, it's not detected, and I do "iwconfig" in console, all I see is... 

```
lo        no wireless extensions.

eth1      no wireless extensions.
```(When the card is detected fine, I see the following with "iwconfig")

```
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MyNet"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:84:A3:59
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-57 dBm  Noise level=-94 dBm
          Rx invalid nwid:15267  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```Now, I've messed with WPA and stuff enough to get the card to auto-hook to the net once the card is detected.  So, that's not a problem.  It's just my computer's randomness at detecting the card sometimes.  Might get detected at first boot.  Might require a reboot (or two in rare cases) for it to get detected.  It's annoying.  But other than that, wireless is working great.

So, I guess have several questions I'm hoping someone can answer

1) why is my computer randomly detecting / not-detecting my wireless Atheros card (when everything else, printer, gfx card, sound card, etc all seem to be detected fine, first time, every time)?  EDIT: I should re-phrase this...the card is "detected" fine..."lspci" always shows the card has been found even when "iwconfig" isn't showing the "ath0" entry.  So, it's like some kind of networking script isn't picking it up or initializing it.  Card's detected, just sometimes not initialized (?)

2) Is it some kind of tweak I need to do to a config file to get it to always detect the card on boot/reboot?

3) If there's no tweak I can do, is there some kind of console command or script I can run to have it try to re-detect the wireless card w/o having to reboot the whole darn machine?  (I'd be willing to live with this much of a solution.)

Any help is greatly appreciated, fellow Linux / Ubuntu-ers!

---

### Post by craigflynn on 2007-11-26
I have the same issue here, sometimes requiring multiple reboots before the card/router hoo up. Strangely , if i boot into xp, thn reboot back into Ubuntu, everything works fine ? Coincidence ?  I m using the same card as above, has a solution to this problem been found ? I have searched but not seen anything.

---

### Post by kevdog on 2007-11-26
Try loading the driver manually when it doesnt work.

sudo modprobe ath_pci
sudo ifconfig ath0 up  (might try wifi0 if this doesnt work)

Then see if the interface is displayed with
iwlist scan

---

### Post by cool_penguin on 2007-11-28
Hi Guys, 

I am using Ubuntu Gusty 7.10 and i have exactly the same problem on my Acer Travelmate 2310 which has in inbuilt Atheros wifi card. 

Any help from you guys will be greatly appreciated.

Cheers,
Harry

---

