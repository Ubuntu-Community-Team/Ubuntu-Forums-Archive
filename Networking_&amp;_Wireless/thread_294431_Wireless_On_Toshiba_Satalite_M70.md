---
title: "Wireless On Toshiba Satalite M70"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by Dacky1 on 2006-11-06
Does anybody know how to get wireless working on a Toshiba satalite M70? I'm running Ubuntu Dapper, through the ethernet cable the net works fine, but I just cannot get onto wireless at all, I can through on XP but I want to get rid of XP totally and just use Ubuntu but the wireless is stopping me doing this.
your help would be much apprecited.

---

### Post by dmizer on 2006-11-06
well, first of all, we will need to know what card is in your computer.  to do that, just post the output of:
```
lspci
```
that will give us more than just the card manufacture, it will tell us what chipset ... which is what we really need to know in order to figure out how to get  you working wirelessly.

---

### Post by jakethesnake on 2006-11-06
I'm having issues getting my toshiba satellite laptop to run wireless internet too. 
Are you running an atheros AR5001X for your wireless? Just curious that's what my satellite came with.

---

### Post by Dacky1 on 2006-11-07
Does this give you the info you need?
Intel(R)PRO/Wireless 2200 BG Network Connection.
This is what I found under the network adaptors in Windows XP.

---

### Post by Dacky1 on 2006-11-08
Can anybody help?

---

### Post by dmizer on 2006-11-08
according to the wiki: [http://www.ubuntuforums.org/showthread.php?t=294431](http://www.ubuntuforums.org/showthread.php?t=294431)

your card should just work.

post the output of the following:
```
iwconfig
```
```
lspci
```
```
lsmod | grep ipw2200
```
and post the contents of: /etc/networking/interfaces

any additional information about your network will be helpful (ie: wep? wpa?)

---

### Post by Dacky1 on 2006-11-08
Hi dmizer,
I'll do it when I get home, I'm at work right now.

---

### Post by Dacky1 on 2006-11-08
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
0000:06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:04.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

sudo lsmod | grep ipw2200
ipw2200               107308  0
ieee80211              37064  1 ipw2200


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Using a Netgear wgr614 v6 router with a wepkey.

cheers

---

### Post by dmizer on 2006-11-08
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
looks like that's your problem.  your wireless adapter is eth1, but it's not configured.  it's there and active, and the driver looks to be installed and working correctly, it just doesn't know how to connect to your network because you haven't told it how.  

have you tried to configure your adapter in network manager?  system > administration > networking?  if so, then you'll probably just have to manually enter settings in your interfaces file.

---

### Post by Dacky1 on 2006-11-09
I have it set on Automatic, it detecs my router as it's name, I have the wep key put in and the other items set to Auto, I'll try input it manually and see how that goes.
I'll keep you informed.

---

