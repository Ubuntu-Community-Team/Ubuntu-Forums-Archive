---
title: "No Sound"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Myket on 2010-04-15
Recently my sound went out and now i cant get it to work at all. ive done my share of searching the forums to find a solution but so far everything ive tried hasnt worked. can someone help walk me through this? thanks ahead of time

---

### Post by ttshivers on 2010-04-15
Myket,

run these codes so we can see more information about your hardware and whats wrong with your sound.

You will need to copy and paste this code into the terminal.

     Code:

```
lspci > ~/Desktop/lspci.txt
 aplay -l >> ~/Desktop/soundinfo.txt
 alsactl -v >> ~/Desktop/soundinfo.txt
 uname -a >> ~/Desktop/soundinfo.txt 
```
 
The terminal is accessable through Applications -> Accessories -> Terminal.

Then, just attach soundinfo.txt and lspci.txt (their on your desktop) to this forum

---

### Post by sydbat on 2010-04-15
> **ttshivers said:**
> Myket,

run these codes so we can see more information about your hardware and whats wrong with your sound.

You will need to copy and paste this code into the terminal.

     Code:

```
lspci > ~/Desktop/lspci.txt
 aplay -l >> ~/Desktop/soundinfo.txt
 alsactl -v >> ~/Desktop/soundinfo.txt
 uname -a >> ~/Desktop/soundinfo.txt 
```
 
The terminal is accessable through Applications -> Accessories -> Terminal.

Then, just attach soundinfo.txt and lspci.txt (their on your desktop) to this forumNo need to save as a text file. That's just adding steps.

Run the above commands (without the "txt" part) then copy and paste them here using the [CODE] tags.

---

### Post by Myket on 2010-04-15
God i feel like such a noob. umm hope this is what u guys are looking for the Ispci.txt reads:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

and the soundinfo.txt reads:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
alsactl version 1.0.18
Linux Myke 2.6.29-1-netbook #0array1 SMP Mon Feb 23 15:02:03 MST 2009 i686 GNU/Linux

---

### Post by ttshivers on 2010-04-16
This sounds like a similar problem that another user is also having [http://ubuntuforums.org/showthread.php?t=1454478](http://ubuntuforums.org/showthread.php?t=1454478)

---

### Post by lidex on 2010-04-16
> **Myket said:**
> Recently my sound went out and now i cant get it to work at all. ive done my share of searching the forums to find a solution but so far everything ive tried hasnt worked. can someone help walk me through this? thanks ahead of time

If you've 'done your share of searching', then you'll know we need some info and shouldn't have to ask for it. Not the psychic forum here. And we'll just guess what you tried already while we're at it.

Do this. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

