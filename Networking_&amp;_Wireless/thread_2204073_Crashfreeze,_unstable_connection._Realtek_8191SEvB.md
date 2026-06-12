---
title: "Crash/freeze, unstable connection. Realtek 8191SEvB, Kubuntu 12.04.4, Thinkpad X200s"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by Alex_Lockhart on 2014-02-06
I've been running Ubuntu on my Thinkpad X200s since the Maverick Meerkat. It's been great, but wifi has often been a little spotty. I figured that just comes with the territory. But ever since upgrading to 12.04 almost two years ago, I've had intermittent problems. It first appeared as hard crashes, with a gob of text on the screen, looking like I'd dropped to terminal, but it looked like a memory dump. This is a hard crash - CapsLock doesn't even work, rebooting only with a 5 second press on the power button. It was intermittent and I couldn't tell what was going on, so I just kept restarting and didn't worry too much about it.

I hoped that upgrades would solve what appeared to be a bug, but nothing changed until 13.10, when the crashes turned to a screen lock - no terminal-style memory dump anymore. It was still as hard crashed and unresponsive, but whatever was on the screen at the time was frozen. I don't have another computer, so couldn't try to ssh in or whatever. I just kept rebooting, but it was constant enough to make me want to throw the computer out the window. I downgraded to 12.04.3 (didn't want to drop back to an unsupported version) by complete wipe and reinstall (my home partition is separate so I can keep userspace constant) and got the old terminal-style memory dumps back.

During this whole time, wifi connections have been unstable - dropping, failing to connect, etc. I had a few little external wifi cards around, and used them with varying success - they were all better than the card in the laptop, but never got a solid connection. Since getting an Android phone over a year ago, I've often been tethering it - basically using it as a USB wifi card. I think our router is fine - we have two Android phones, an iPhone, three MacBooks, and a Windows laptop in the house, and they all have solid wifi. Doing research led me to switch from NetworkManager to wicd, which helped. But now I often get the dreaded "Bad Password" problem. I kept reading all kinds of stuff on the various problems I was having, but couldn't get a solid connection. Switching the router from WPA2-PSK to WEP didn't help so I switched back.

I decided it might be hardware related, so I had to try to fix it. I looked through dmesg but couldn't make heads or tails of anything. I tried lots of stuff I saw on forums, to no avail. I can't even remember all the stuff I've been through, but it's consumed hours. Lately it's been pretty stable - crashes only once a week or so, and wifi usually works OK, only occasional drops and fiddling. But last night, the wifi wouldn't connect - the "Bad Password" error again - so I got a driver from Realtek (the 8192 that also covers my 8191SE card) [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true"), the one for kernel 2.6.24 and later. I compiled and installed the driver, and when I rebooted, I was back into super-crash land. Several reboots got me, at best, to the desktop before crashing, sometimes with a screen freeze and sometimes with a terminal memory dump. I took a picture of the screen in the terminal memory dump.

My Thinkpad has a hardware wifi switch, so I switched it off and now I'm stable again, connected to wifi via my Android phone like before. That means my system info can't show some of the otherwise-helpful stuff - like scanning the wireless network.

Here's the info on my system. Help! And TIA!!

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

```

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04e8:6863 Samsung Electronics Co., Ltd 
```

```
$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```

```
$ lsmod | grep "rtl"
rtl8187                57035  0 
eeprom_93cx6           12767  1 rtl8187
rtl8192se              93999  0 
rtlwifi               118767  1 rtl8192se
mac80211              506862  3 rtl8187,rtl8192se,rtlwifi
cfg80211              205774  3 rtl8187,rtlwifi,mac80211

```

(The rtl8192 and rtl8187 are from the two USB sticks that I've been popping in and out - they're not connected now.)

```
$ dmesg | grep "rtl"
[    9.896118] rtl8192se 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.896125] rtl8192se 0000:03:00.0: setting latency timer to 64
[   10.098003] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  688.864260] rtl8192se 0000:03:00.0: PME# disabled
[  688.913130] rtl8192se 0000:03:00.0: PCI INT A disabled
[  689.888323] rtl8192se 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  689.888333] rtl8192se 0000:03:00.0: setting latency timer to 64
[  689.905138] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 3224.263496] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 3224.949724] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3323.343749] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 3324.041988] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3559.647843] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 3560.338579] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3565.183817] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 3565.881057] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3666.330313] ieee80211 phy2: hwaddr 00:a1:b0:79:7c:c5, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 3666.352341] rtl8187: Customer ID is 0x00
[ 3666.352431] Registered led device: rtl8187-phy2::radio
[ 3666.352489] Registered led device: rtl8187-phy2::tx
[ 3666.352553] Registered led device: rtl8187-phy2::rx
[ 3666.353884] rtl8187: wireless switch is on
[ 3666.354555] usbcore: registered new interface driver rtl8187
[ 3667.113401] ieee80211 phy3: hwaddr 00:a1:b0:79:7c:c5, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 3667.133238] rtl8187: Customer ID is 0x00
[ 3667.133324] Registered led device: rtl8187-phy3::radio
[ 3667.133383] Registered led device: rtl8187-phy3::tx
[ 3667.133437] Registered led device: rtl8187-phy3::rx
[ 3667.134078] rtl8187: wireless switch is on

```

(Again, lots of stuff from the rtl8187 USB dongle I was playing with.)

```
$ sudo lshw -C network
[sudo] password for alex: 
  *-network DISABLED      
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:2b:d8:02
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
  *-network DISABLED
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 00:24:2c:ac:89:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-58-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f2500000-f2503fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:34:34:6b:6f:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.231 link=yes multicast=yes

```

```
$ lsb_release -d
Description:    Ubuntu 12.04.4 LTS
```

```
$ uname -a
Linux Kubuntu-Thinkpad 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ sudo service networking restart
stop: Unknown instance: 
networking stop/waiting
```

EDIT: Here's the photo of the screen during the terminal-style memory dump:

---

### Post by varunendra on 2014-02-07
Hello Alex, Welcome to the forums !

How much memory your system has? If it is less than 2GB, I would strongly recommend Xubuntu instead of default Ubuntu. Even with 2GB RAM, my i3-2330 based laptop is nearly 'Crawling' at the moment (my additional RAM module crapped out).

As for the wireless issue, your lsmod + dmesg clearly show almost a 'War for Resources' currently. Please confirm which one you want to make work - the internal PCI card or one of the USB ones? For now, please disconnect the USB ones, reboot the PC and run "wireless_script" on it. Steps to download and run wireless_script can be found in the "Wireless Script" link in my signature below. Post back the report this script generates.

If we couldn't make it work, we can disable its driver (so it doesn't conflict with others) and try one of the USB ones. Or we can do so right away if you prefer any of the USB ones.

Oh, and in the meanwhile, check the output of "iwconfig" command. If it shows "Power Management" to be "on", try this -
```
sudo iwconfig wlan0 power off
```
Then see if it makes the connection more stable. Of course change "wlan0" with "usb0" or whatever your working connection is listed as.

---

### Post by Alex_Lockhart on 2014-02-07
Thanks for the help!

1. My system has 4GB memory, and it's always seemed plenty fast. Opening 100 tabs in Firefox will eat up the memory and slow it down, but otherwise it's always snappy. Core 2 Duo Penryrn 1.86GHz, 800MHz memory, Seagate hybrid HDD with 8GB flash to feel like SSD in most used apps. It's not a new, powerful system, but it's not slow, and I can't imagine I'm having resource problems.

2. I never had any hint of instability (no crashes, freezes, soft lock, etc) for about 18 months before upgrading to 12.04. My hardware has stayed the same the whole time. This is why I never thought it could be hardware-related until recently, when I swapped around versions (always clean install) with no change.

3. I want the internal PCI card to work. The only reason I plugged in the USB dongles is because I kept getting connection dropped, "Bad Password", and general failure to connect while using the internal PCI card. The USB dongles always worked better, but I can't remember if it seemed to crash less when using them.

4. It crashed again last night, and I haven't plugged in any USB wifi dongles since then. I'm on the internet by tethering my Android phone, which (I think) the system sees as a wired network rather than a wireless. I ran the script - it's great, thanks!

```


*************** info trace ***************

***** uname -a *****

Linux Kubuntu-Thinkpad 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Lenovo Device [17aa:20ee]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:e020]
    Kernel driver in use: rtl8192se

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04e8:6863 Samsung Electronics Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes

***** lsmod *****

rtl8192se              93999  0 
rtlwifi               118767  1 rtl8192se
mac80211              506862  2 rtl8192se,rtlwifi
cfg80211              205774  2 rtlwifi,mac80211

***** nm-tool *****

***** NetworkManager.state *****

***** NetworkManager.conf *****


***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 192.168.42.129

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B5184945312BE0F016AC596
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.2.0-58-generic SMP mod_unload modversions 
parm:           fwlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           swlps:using linked sw control power save (default 1 is open)
 (bool)

filename:       /lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     953878FB72AD1AAE531C0BD
depends:        mac80211,cfg80211
vermagic:       3.2.0-58-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0bda:0x8171 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

***** dmesg *****

[   14.614278] rtl8192se 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.614286] rtl8192se 0000:03:00.0: setting latency timer to 64
[   14.689689] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.131880] IBM TrackPoint firmware: 0x0e, buttons: 3/3

****************** done ******************


```

5. Yes, power management is already off. I think it's been that way every time I've run iwconfig, over many many times in the past years as I've been trying to get it to connect.

6. I've seen rfkill report the wifi is hard blocked before. Remember I have a hardware switch to turn off the Wifi - and it's off now. Currently, turning it off keeps it from crashing all the time - like a few minutes after bootup. So that hard-blocked the bluetooth, but somehow didn't hard-block the wifi. WTF, hardware switch?

7. I don't use NetworkManager, I used wicd. It has helped me connect much more often, but I still don't have a good wifi connection. Hence the lack of output from the NetworkManager part of the script.

8. I did just download and make/install a new driver for my PCI card. Since then it's been crashing all the time unless I switch off wifi with the hardware switch. I much prefer the internal PCI card and would love to make it work. But I think it obviously needs a better driver - whatever it had before (worked "out of the box" on install) at least wasn't crashing all the time. I do need to at least disable the current driver, but that won't help it work.

Thanks for the help!

---

### Post by Alex_Lockhart on 2014-02-08
Ba-dump Bump!

Anyone want to take a crack at this, now that I've got the results of the almighty wireless_info.txt in my above post? TIA!

---

### Post by varunendra on 2014-02-09
Sorry for not being able to reply earlier.

I think a reasonable strategy for troubleshooting the problem would be -

Test Memory to make sure it is stable > Try some tweaks with current driver > (if no improvement) Try a newer version of the driver > (if no improvement) Blacklist the native driver and try the USB ones > Try a later version of the USB drivers if needed.

But given the fact that the system has been crashing, more or less always, with all versions of Ubuntu, it makes me skeptical about the hardware too. It is very highly unlikely that these drivers (the native ones) can cause system freeze or crashes.

Also, unless you are ultra sure that wicd is helping the connectivity, I'd suggest to reinstall Network Manager (apt-get install network-manager-gnome) and purge wicd (apt-get purge wicd).

To test the memory, boot the computer > press & hold 'Shift' (or 'Esc' in some systems) key to get Grub menu > select memtest+ and run it overnight. Recommended duration is 24 hrs., but 5-6 hrs. should be sufficient to prove that the memory is reasonably stable (my 4GB Irvine module passed 6+ hrs. still caused problems 2-4 times a day when under load).

It may also be interesting to see your overall hardware specs, especially Video driver in use (I guess it should be i915, but maybe different). To post that info, post back the output of -
```
sudo lshw -numeric -sanitize > Desktop/lshw.txt
```
This will dump the output of "lshw" into a text file "lshw.txt" on your desktop. Post back the contents of this file.

---

### Post by Alex_Lockhart on 2014-02-10
No need to apologize. All help is good help! I just thought that if I kept the thread on the first page, someone else might want to chime in.

I've never done a memtest, so I'll run that tonight and report back with the results. Does it just run for as long as you let it go, and then stop when you tell it to stop? And report errors if and when it finds them?

Yes, I'm also pretty skeptical of the hardware. It didn't crash with all versions - just when I upgraded to 12.04. Before that, I ran 10.10, 11.04, and 11.10 and never had a crash. Since 12.04 it's been crashing, sometimes lots and sometimes once a month or less. The reason I'm skeptical of the wireless card first is because the screen when it crashes mentions it several times. You can see it in the image I posted with the OP. Also, having the hardware wireless switch off recently seems to help.

But the crashing may have started around 12.04 just because some part of the hardware was also starting to give errors at that time. The system was over 3 years old when I upgraded to 12.04, but I had upgraded the memory myself about 18 months earlier. Anyway, it's old enough that some piece of hardware could be making it crash. I plan to keep the laptop for another year or more, so it would be great if I can get it to stop crashing!

Here's what I know about wicd in contrast to NetworkManager. When I was researching the spotty wifi connection, many forum posts suggested switching to wicd. When I did, it seemed to connect more often and was more stable. I didn't keep statistics but it felt much better. I'll be happy to switch back to see if it helps. Hell, I'll be happy to try a fresh install of 13.10 again to see if it helps, even though it didn't before!

Here's the output of the lshw command you asked for:

```

computer
    description: Notebook
    product: 7465CTO ()
    vendor: LENOVO
    version: ThinkPad X200s
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ThinkPad X200s frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 7465CTO
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 6DET60WW (3.10 )
          date: 09/17/2009
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     L9400  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     L9400  @ 1.86GHz
          slot: None
          size: 1866MHz
          capacity: 1866MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: burst internal write-back unified
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron Technology
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub [8086:2A40]
          vendor: Intel Corporation [8086]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller [8086:2A42]
             vendor: Intel Corporation [8086]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller [8086:2A43]
             vendor: Intel Corporation [8086]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f2400000-f24fffff
        *-communication:0
             description: Communication controller
             product: Mobile 4 Series Chipset MEI Controller [8086:2A44]
             vendor: Intel Corporation [8086]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:44 memory:f2826800-f282680f
        *-communication:1
             description: Serial controller
             product: Mobile 4 Series Chipset AMT SOL Redirection [8086:2A47]
             vendor: Intel Corporation [8086]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 07
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:1830(size=8) memory:f2624000-f2624fff
        *-network DISABLED
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection [8086:10F5]
             vendor: Intel Corporation [8086]
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:46 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937]
             vendor: Intel Corporation [8086]
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938]
             vendor: Intel Corporation [8086]
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939]
             vendor: Intel Corporation [8086]
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:18a0(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293C]
             vendor: Intel Corporation [8086]
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f2826c00-f2826fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller [8086:293E]
             vendor: Intel Corporation [8086]
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:f2620000-f2623fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1 [8086:2940]
             vendor: Intel Corporation [8086]
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:c0200000-c03fffff ioport:c0400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2 [8086:2942]
             vendor: Intel Corporation [8086]
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:f2500000-f25fffff ioport:c0000000(size=2097152)
           *-network DISABLED
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller [10EC:8172]
                vendor: Realtek Semiconductor Co., Ltd. [10EC]
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=3.2.0-58-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:2000(size=256) memory:f2500000-f2503fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4 [8086:2946]
             vendor: Intel Corporation [8086]
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:f0000000-f1ffffff ioport:f2900000(size=1048576)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934]
             vendor: Intel Corporation [8086]
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18c0(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935]
             vendor: Intel Corporation [8086]
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18e0(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936]
             vendor: Intel Corporation [8086]
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1c00(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293A]
             vendor: Intel Corporation [8086]
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f2827000-f28273ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge [8086:2448]
             vendor: Intel Corporation [8086]
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller [8086:2917]
             vendor: Intel Corporation [8086]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929]
             vendor: Intel Corporation [8086]
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:1c48(size=8) ioport:183c(size=4) ioport:1c40(size=8) ioport:1838(size=4) ioport:1c20(size=32) memory:f2826000-f28267ff
           *-disk
                description: ATA Disk
                product: ST95005620AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SD24
                serial: [REMOVED]
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000d6ca4
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 9534MiB
                   capacity: 9534MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-11-04 10:55:41 filesystem=ext4 lastmountpoint=/ modified=2013-11-04 11:07:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2014-02-06 21:24:55 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: [REMOVED]
                   size: 4768MiB
                   capacity: 4768MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: [REMOVED]
                   size: 447GiB
                   capacity: 447GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-06 22:22:01 filesystem=ext4 lastmountpoint=/home modified=2014-02-06 21:25:06 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2014-02-06 21:25:06 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller [8086:2930]
             vendor: Intel Corporation [8086]
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f2827400-f28274ff ioport:1c60(size=32)
  *-battery
       product: 42T4646
       vendor: SANYO
       physical id: 1
       slot: Rear
       capacity: 28800mWh
       configuration: voltage=14.4V
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=[REMOVED] link=yes multicast=yes

```

As you expected, it's the i915 display driver. Is that known to cause problems?

---

### Post by varunendra on 2014-02-10
> **Alex_Lockhart said:**
> I've never done a memtest, so I'll run that tonight and report back with the results. Does it just run for as long as you let it go, and then stop when you tell it to stop? And report errors if and when it finds them?
Yes, it keeps running, testing the memory in various ways and reporting Success or Fail on "Passes" it has completed (each pass consists several tests). When a Pass fails, either it reports the "Fail" in its summary table or just hangs on that screen. A Fail may also cause it to crash (thus rebooting the system) which is in itself a serious warning about the integrity of the memory.

However, nothing in the lshw output seems suspicious to me. The memory brand is good and its frequency pretty much the standard for DDR3.

The "Unclaimed" display adapter is something unexpected, because it should have had a driver associated which is not. But the primary display has the driver i915 associated and it is quite a decent driver in my personal experience (but then I have a fairly different display - Intel HD 3000 that is embedded in i-series 2nd gen CPUs).

By the way, the last network interface - "usb0" (using rndis_host driver) - is it one of your USB adapters? The rndis_host driver may conflict with the rtl8192se and may cause troubles like you are having.

---

### Post by Alex_Lockhart on 2014-02-10
Just about to run the memtest and saw your reply. Thanks!

I'll just run it until I want to use the computer sometime tomorrow, probably over 10 hours. Hopefully that's enough to find something if it's wrong.

I'm running an external monitor (Samsung SyncMaster 2233, cheap old 21" 1080p display) plugged into the VGA port on the laptop. Could that be the "Unclaimed" display? I don't think so - it's talking about display adapters, not actual displays - but it's worth noting.

I'm pretty sure that last network interface "usb0" with rndis_host driver is my Samsung Galaxy II Android phone, tethered to the computer to provide internet. The network (wicd now, but also NetworkManager when I was using that) calls it a wired ethernet device, not a wireless one. I haven't plugged in any of my USB wifi dongles since last bootup.

I'll have more to say after the memtest!

---

### Post by Alex_Lockhart on 2014-02-10
Did the memtest. I was away from the computer for over 10 hours, and when I got back it was frozen. I left it for another hour or two before getting out the camera and taking a picture of the screen before rebooting. It's attached below.

It says it's been running for under 2 hours, 88% tested, 100% passed, in the middle of some test. It also says at the bottom "Pass complete, no errors, press ESC to exit" but the computer was frozen hard - capslock wouldn't come on, had to hold down the power button 5 seconds to get it to reboot. So it really appears to have frozen during the memtest. But the cursor in the upper left was still flashing. Weird.

I think we have a culprit for the crashes! So should I now run the memtest with only one stick at a time, to see if it's just one that makes it crash? And if that works, then try running the computer with only the one stick of 2GB  that didn't crash? 

Here's the "screenshot" photo. Figured out how to attach and thumbnail it here.

[ATTACH=CONFIG]250255[/ATTACH]

---

### Post by varunendra on 2014-02-10
It was interesting to see that it is actually a **DDR2 - 533** MHz running at 1066MHz, probably an overclocking trick by introducing an x2 multiplier within the RAM module.

Not sure about how the vendors achieve it, but I do know that such kind of overclocking (if it indeed is that) requires more than normal voltage for normal operation and is usually more prone to failure.

But not going into details of things that I don't properly understand myself, the bottomline is - YES either RAM module(s) or the motherboard's capability to support it may be failing. As such -
> **Alex_Lockhart said:**
> So should I now run the memtest with only one stick at a time, to see if it's just one that makes it crash? And if that works, then try running the computer with only the one stick of 2GB  that didn't crash?
..would be a good idea.

But considering the fact that it may also be due to insufficient power supply (to keep up with the RAM's demands), I'd suggest to do the test with both modules one-by-one. It is possible that each module may pass the test when running alone, while only failing when being used simultaneously. In that case, it is most probably a problem at motherboard's end, for which there may or may not be a fix.

For my own reference (and so that I can remember), here is an external link to a similar problem : [https://www.overclockers.com/forums/showthread.php?t=648071](https://www.overclockers.com/forums/showthread.php?t=648071)

Some explanations for a better interpretation of what you saw -
> **Alex_Lockhart said:**
> It says it's been running for under 2 hours, 88% tested, 100% passed, in the middle of some test. It also says at the bottom "Pass complete, no errors, press ESC to exit" but the computer was frozen hard - capslock wouldn't come on, had to hold down the power button 5 seconds to get it to reboot. So it really appears to have frozen during the memtest. But the cursor in the upper left was still flashing. Weird.
[LIST]
[*]In 10 hours, it should have passed more than 4 passes, probably more than 8, judging by the speed of your CPU/RAM.
[*]The "Pass %" field at the top shows the progress of the current pass. It seems your system froze near the completion of the 2nd Pass.
[*]The "Test %" field below that shows the progress of the current test. There are several tests in one Pass.
[*]The "Test #" field shows the number of test being carried out. The tests with higher number have higher complexity and take more time than simpler ones.
[*]The "Pattern" shows what kind of data the memory is being tested with. Something I don't understand much but maybe we also don't need to.
[*]The cursor at the top-left corner almost always keeps flashing, unless the whole program has crashed, so that's normal. The test failed - no doubt about it.
[/LIST]

Now the failure of the test doesn't necessarily mean that the memory is faulty. It may also be a failure of some other part of the motherboard, like overheating of an I/O controller or some power controlling component etc. But since it is a laptop, we don't have much scope to test/tweak various things within a home environment.

So while you should know above, I think all you can practically try now is to try the same tests with both modules - using only one module at a time, and report back.

- If one module passes but the other fails, discard the faulty module.
- If both modules pass when used individually, then our chances to be able to use them both depends upon how much manual control your laptop's BIOS offers over related settings.
- If both modules fail, then most probably the motherboard is faulty, not much hope in that case.

---

### Post by Alex_Lockhart on 2014-02-10
> It was interesting to see that it is actually a **DDR2 - 533** MHz running at 1066MHz, probably an overclocking trick by introducing an x2 multiplier within the RAM module.

I think that's what DDR means - Double Data Rate. Isn't it because they double the clock rate? I thought that was how all DDR works. That was my understanding, but I'm no expert.

Certainly, the next step is as you said, to run the test again with each module one by one and see what happens. Hopefully it's a problem with just one stick of RAM; that's cheap and easy to replace. I read that forum post, it's interesting.

Thanks for the explanation of memtest. I'm not sure how much control my BIOS gives me over memory settings. I used to do a lot of tweaking and overclocking of all kinds of stuff back in the Athlon/Pentium 4 days, with self-built desktops. But hardware is now so fast that I just get whatever laptop seems to fit my needs and don't poke around under the hood much. Maybe I'll have to see what happens if I fiddle with memory settings. First the memtest tonight. Thanks again for your help!

---

### Post by varunendra on 2014-02-11
> **Alex_Lockhart said:**
> I think that's what DDR means - Double Data Rate. Isn't it because they double the clock rate?

No, Double Data Rate doesn't mean double Clock Rate. It doubles the data rate not by doubling the clock rate, but by using "Double Pumping" technique in which data is sent on both rising and falling phases of a clock cycle.

1066 MHz is the starting frequency range of DDR3 RAM, and as per my limited knowledge, this frequency is achievable in DDR2 only by overclocking. But I don't have any authentic source to confirm this (actually didn't try to find one :P). More at wikipedia : [https://en.wikipedia.org/wiki/DDR_SDRAM](https://en.wikipedia.org/wiki/DDR_SDRAM)

For reference, the (stripped) output of "lshw -C memory" from my laptop (with only one RAM module currently, a Hynix 2GB DDR3-1333 MHz) is -
```
 *-memory
       description: System Memory
       physical id: 3f
       slot: System board or motherboard
       size: 2GiB
     *-bank:0
          description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: HMT325S6CFR8C-H9
          vendor: Hynix/Hyundai
          physical id: 0
          serial: 00000000
          slot: ChannelA-DIMM0
          size: 2GiB
          width: 64 bits
          clock: **1333MHz** (0.8ns)
     *-bank:1
          description: DIMM [empty]
          product: [Empty]
          vendor: [Empty]
          physical id: 1
          serial: [Empty]
          slot: ChannelB-DIMM0
```

When running memtest+, it shows the same frequency and capacity (writing by memory, didn't reboot to confirm, but performed a test just a few days ago and am pretty sure about this. A quick test on a virtual machine confirms the freq. reported by memtest).

---

### Post by Alex_Lockhart on 2014-02-11
Ran memtest last night with only one stick of memory. I labeled them A  and B so I could keep track. Stick A ran memtest for almost 7 hours  before freezing, same as before with both sticks (only longer time). I  took another photo "screenshot" in case you want to see it, at the  bottom.

Thanks for explaining the DDR thing. I remember now  reading tech articles when it came out years ago about how it was  "double-pumped" at the same clock speed. Yes, I understand now what you  said about my chip somehow being double-clocked inside the chip. I  didn't catch that difference before when looking at the memtest screen -  that memtest says it's DDR2 and lshw says it's DDR3.

Yes, it's  very odd, and I'm sure there's an explanation for it, which we may not  need to know. However, looking at the Wikipedia pages  [https://en.wikipedia.org/wiki/DDR2_SDRAM#Chips_and_modules](https://en.wikipedia.org/wiki/DDR2_SDRAM#Chips_and_modules) and  [https://en.wikipedia.org/wiki/DDR3_SDRAM#JEDEC_standard_modules](https://en.wikipedia.org/wiki/DDR3_SDRAM#JEDEC_standard_modules) it looks  like there's overlap between DDR2 and DDR3 - they both have a 6400 and  8500 level. For the 8500 that I have, a DDR2 module has a 133Mhz memory  clock and 266Mhz bus clock. For the DDR3 module, it's a 133Mhz memory  clock and 533Mhz bus clock. So...which do I have? The sticker on the RAM  module says PC3-8500, and it seems memtest agrees because it reports a  533Mhz RAM clock. But these are just guesses.

Anyway, the important thing is that it failed.  And it might be significant that it took much longer before it failed  than when I ran the test with both modules. I'm about to run memtest  again with the other stick B in there by itself and see what happens.

Either  way, I'm looking at some new hardware. I'm not sure if I'd rather see  the memory fail and just replace that, or the motherboard/power supply  fail and need a whole new laptop. A new computer is great, but I was  really planning to keep this one for another year, until the Haswell  ultrabooks with IPS displays start showing up on the used market for cheap. We'll see.  Thanks for your help!


[ATTACH=CONFIG]250271[/ATTACH]

---

### Post by Alex_Lockhart on 2014-02-11
Well, that was fast! Running stick "B" of memory by itself got to the hard lock freeze in only 46 minutes. "Screenshot" photo is below again.

I was a bit surprised that, when I put stick B in the other slot (leaving the slot where stick A had been empty), I got a 3-beep error code on boot. Apparently, the board doesn't like to see that slot empty. Not really that surprising, I guess - maybe that's common. I can't remember from my desktop hacking/overclocking days whether that's normal for motherboards to need slot 0 filled or they won't boot.

So, both memory sticks failed when tested by themselves. Do you think it means anything that the test ran for much different times before failing? Certainly if I had to pick one or the other memory stick, I'd go with stick A which ran for almost 7 hours before failing instead of stick B with 46 minutes. But if they both failed when run by themselves, does that mean they're both bad? Or does it mean my motherboard/power supply is having problems?

I poked around in my box of computer stuff and found some memory sticks I could throw in there and test, if it would help diagnose what's happening. Here's my options:
[LIST]
[*]Two sticks of 512MB PC2-5300 that came out of my wife's old Macbook when I upgraded it to 4GB. I could also pull the two 2GB sticks of PC2-5300 out of that computer since she no longer uses it. But these are both much slower than the specified speed. Can the motherboard just step down to run slower memory?
[*]One stick of 2GB PC3-10600 that came out of my wife's new Macbook Pro when I upgraded it to 8GB. The same speed problems apply here - can the motherboard run fast memory at slow speeds?
[/LIST]

Oh, and since I'm no longer suspicious of the wifi adapter, I turned it back on and tried to connect. It timed out while trying to get the IP address, so I plugged in the USB dongle with the RTL8187 chipset. It works fine. Still using wicd, haven't switched back to NetworkManager as you suggested. I'll probably do that soon but right now I just want to figure out and fix the memory crashing problem. Actually, once I get the memory fixed and the system doesn't crash, I'll probably just go back to 13.10.

So, what's my next step? Run some more tests with other memory sticks of the wrong speed? Look in the BIOS to see if there are any settings I could try to make it work? Buy some hardware?

Here's the "screenshot". Thanks again!

[ATTACH=CONFIG]250273[/ATTACH]

---

### Post by varunendra on 2014-02-11
> **Alex_Lockhart said:**
> ....However, looking at the Wikipedia pages  [https://en.wikipedia.org/wiki/DDR2_SDRAM#Chips_and_modules](https://en.wikipedia.org/wiki/DDR2_SDRAM#Chips_and_modules) and  [https://en.wikipedia.org/wiki/DDR3_SDRAM#JEDEC_standard_modules](https://en.wikipedia.org/wiki/DDR3_SDRAM#JEDEC_standard_modules) it looks  like there's overlap between DDR2 and DDR3 - they both have a 6400 and  8500 level. For the 8500 that I have, **a DDR2 module has a [COLOR="#FF0000"]133Mhz memory  clock and 266Mhz bus clock[/COLOR]. For the DDR3 module, it's a 133Mhz memory  clock and 533Mhz bus clock**. So...which do I have?

The part highlighted above is for DDR2-533, or PC2-4200 *(take another look at the tables)*. The I/O bus clock is 533 MHz for both DDR2 and DDR3 variants of PC-8500.

The fact that it is labelled as PC3-8500 suggests that it may be a DDR3 module, but so far I have no solid clues to be sure of what it internally is. If I believe that the FSB (is controlled by the motherboard, RAM module can only support or not support it) is same as "Memory Clock" (I really am lost here), then I is a DDR2 module.

But the physical difference can't be denied, and now that you have them in hand, it is easy to verify. Just count the pin-count on any side of the key notch. As shown in [this figure]("https://upload.wikimedia.org/wikipedia/commons/9/95/Laptop_SODIMM_DDR_Memory_Comparison_V2.svg"), the side with lesser pins has a **count of 36 for DDR3**, while it is **just 20 for DDR2**.

And IF it turns out to be DDR2, then this may be a more important fact pertaining to my belief that it may be an insufficient power issue (or a faulty supply/filter component like some capacitor due to too much stress) -
> However, the original DDR technology tops out at a clock rate around 200 MHz (400 MT/s). Higher performance DDR chips exist, but JEDEC has stated that they will not be standardized. These modules are mostly manufacturer optimizations of highest-yielding chips, **[COLOR="#FF0000"]drawing significantly more power than slower-clocked modules[/COLOR]**, and usually do not offer much, if any, greater real-world performance
(from [https://en.wikipedia.org/wiki/DDR2_SDRAM#Debut](https://en.wikipedia.org/wiki/DDR2_SDRAM#Debut)).

Another fact that the test continued for 7 hours this time also suggests that it may be a problem on motherboard's side (although most often easily fixable). This time the memory controller chip (or other components in the memory power supply section) wasn't stressed as much as it was with both modules simultaneously.

But let's hope it is just your module "A" causing the problem (even in case of over-stress on power supply module, one of the modules may be culprit), because no matter how easy it may be to just replace a memory controller or a capacitor, it would cost you money - a significant amount because they charge more for laptops, while in case of a faulty module, it is as simple as discarding one and running with only the other one. 2 GB is plenty for Xubuntu. :)

**EDIT:**
Oops! Looks like I took too much time to compose this post. Noticed your next post only after posting mine (26 minutes later :P).

Anyway, I still think it is okay to go with a single module (the module "A"). A 7 hour successful run is in itself an assurance of a pretty usable memory at the least :)

---

### Post by varunendra on 2014-02-11
> **Alex_Lockhart said:**
> Do you think it means anything that the test ran for much different times before failing?
To me, it means the faulty one "module 'B'" stressed the memory controller module too much and now either it's capacitor(s) have dried up, or the controller chip/mosfets is/are weared out. So they are still working, but with sub-par efficiency.

> **Alex_Lockhart said:**
> I poked around in my box of computer stuff and found some memory sticks I could throw in there and test, if it would help diagnose what's happening. Here's my options:
[LIST]
[*]Two sticks of 512MB PC2-5300 that came out of my wife's old Macbook when I upgraded it to 4GB. I could also pull the two 2GB sticks of PC2-5300 out of that computer since she no longer uses it. But these are both much slower than the specified speed. Can the motherboard just step down to run slower memory?
[*]One stick of 2GB PC3-10600 that came out of my wife's new Macbook Pro when I upgraded it to 8GB. The same speed problems apply here - can the motherboard run fast memory at slow speeds?
[/LIST]
Selection or compatibility depends first on the memory type. You obviously can't fit a DDR2 in a DDR3 slot, or vice-versa.
If yours are DDR2 modules (check with the link in my previous post), then the 512(x2) module may work, but sometimes the BIOS (or the motherboard components - I'm not sure, but it happens) doesn't support a much different frequency even if it is a lower one from the same class of memory.

Same goes for the PC3-10600 module, even though it is just one level higher than what you have (IF it is indeed a DDR3). But if my guess about wearing out of motherboard components is correct, this will almost certainly fail miserably, even if that frequency was originally supported by the BIOS/Motherboard. More frequency = more stress at the controller = more chance of failing.

So the next steps should be -
Confirm your module type (is it DDR2 or DDR3?) > test the optional modules that you have available > switch to them if more successful, otherwise stick to the module 'A' unless it is no less irritating.

If the problem persists or worsens, maybe consult a local repair guy and see if he is confident at fixing it.

---

### Post by Alex_Lockhart on 2014-02-12
> **varunendra said:**
> 
But the physical difference can't be denied, and now that you have them in hand, it is easy to verify. Just count the pin-count on any side of the key notch. As shown in [this figure]("https://upload.wikimedia.org/wikipedia/commons/9/95/Laptop_SODIMM_DDR_Memory_Comparison_V2.svg"), the side with lesser pins has a **count of 36 for DDR3**, while it is **just 20 for DDR2**.

This. All the rest of it gets confusing, since I don't know much about specific timings, voltages, JEDEC standards, etc. But the physical difference is obvious. Well, it will be, as soon as I shut down and pull the cover off!

Those other two modules I have are clearly physically different - one is DDR2 and one is DDR3. So one of them will physically fit and the other won't. Whether they will work or not is a totally different question, and I don't have much hope or attachment to that idea. I just thought I'd throw it out there.

So, I'll open it up and see what I have and try whichever of the other two modules works. Maybe first I'll look in the BIOS settings to see how much I can adjust memory settings, since I may need to. That is, if it will even boot with the modules of different speed.

Also, if one chip is bad and the other is good, I'll be replacing it. No need to go limping around with 2GB and giving up my beloved KDE for XFCE just because one memory stick failed, when I can get a new one for $22. In the meantime, I'll see if and how often it crashes. It's been great these past few days - only one crash about 4 days ago. I can live with that while a new memory module is on its way. I just can't live with what it was doing a month ago - crashing at least once a day!

On another note, I installed NetworkManager again and removed wicd. It connected to the wifi using the built-in card (RTL8191), which is better than wicd did earlier today. But it seems flaky - pages sometimes load and sometimes don't, even though it says it's still connected. Just like before! Probably soon it will drop, or refuse to connect after waking from sleep, etc. That can all be sorted out once it's not crashing.

More updates to come. I'll probably run memtest again tonight for fun. Thanks for your patience and help!

---

### Post by varunendra on 2014-02-12
You're always welcome. :)

> **Alex_Lockhart said:**
> pages sometimes load and sometimes don't,....<snip>.... That can all be sorted out once it's not crashing.
This ^ I'll be eagerly waiting for.

---

### Post by Alex_Lockhart on 2014-02-12
OK, some new developments:

The memory I have is indisuptably DDR3, with 36 pins on the shorter end of the slot. Also the slot on the laptop motherboard is clearly printed "DDR3 1.5V". So why would memtest keep reporting it as DDR2?

I ran the memtest again last night with just "module A" out of curiosity. It failed (again by freezing hard) but this time after only 2:49. So I'm not convinced it's a good solid memory module. I may keep doing this occasionally to see how it changes.

I put in the other 2GB stick of DDR3-1333 PC3-10600 that came out of my wife's MacBook Pro when we upgraded hers to 8GB. It booted, I poked around in BIOS and found no real memory settings. I ran memtest for a few minutes. It called it DDR2 at 533/1066 MHz, just like the other modules. IIRC, the Core2 Duo CPU has the memory controller integrated into the chip now instead of on the "Northbridge". So is the CPU just dictating settings to the memory and then the memory has to do it? At any rate, somehow, the memory controller is underclocking this memory. Isn't that usually good for stability? Again, the BIOS has no info or control over the memory settings, so I can't get a report of the voltage or timings. "Screenshot" below is with the one new stick doing memtest. Also I put the memory section of the current output of lshw for reference:

```

     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron Technology
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)

```

[ATTACH=CONFIG]250294[/ATTACH]

Right now I'm running my own "module A" plus the new 2GB DDR3-1333 stick. No crashes so far! Tonight I'll run memtest for as long as it will go using only that new faster stick. I can also pull the other matching 2GB stick out of my wife's MacBook Pro (leaving her with 8GB instead of 10GB - she won't mind) and run both of the faster sticks in my computer. If that will memtest for hours and hours, I think I'll just do that. Maybe I need to read up on this kind of underclocking.

Back to the network, I remembered that I had adjusted the MTU settings in NetworkManager before but couldn't remember what I'd done. Some Googling led me to set the MTU for this connection at 1392. Since then, it's been solid. The connection hasn't dropped, and pages all keep loading. Here's what it was doing before that: Facebook and Google+ pages would keep having their messenger apps say they couldn't connect, and Dropbox would spin and spin also trying to connect. During this time no pages would load. Then suddenly they would all come back and pages would load, for one minute or less, before going back to no connection for 10-20 minutes. During all this time, NetworkManager reported it was constantly connected. Anyway, setting the MTU down to 1392 seems to have fixed it - everything connects and is fast all the time. I still haven't done much suspend/resume to see how it comes back - that also used to be a common problem. This is all with the internal RTL8191 PCI card - no USB dongles. Comments?

---

### Post by varunendra on 2014-02-12
> **Alex_Lockhart said:**
> So why would memtest keep reporting it as DDR2?
I can only guess - it is probably because it is unable to determine the "Memory Clock", and so is judging on the basis of the FSB frequency. I can't say it is technically okay or a bug in the program.

> I ran the memtest again last night with just "module A" out of curiosity. It failed (again by freezing hard) but this time after only 2:49. So I'm not convinced it's a good solid memory module.
It is also possible that all the modules are okay, and it is just one of the controllers (frequency, or some component(s) in PWM (Pulse Width Modulation) module). Your test results with the 1333 MHz modules should hint or confirm that.

> IIRC, the Core2 Duo CPU has the memory controller integrated into the chip now instead of on the "Northbridge". So is the CPU just dictating settings to the memory and then the memory has to do it?
Exactly, I had overlooked the CPU specs earlier until now, and just by looking at its L2 cache, I don't need to look it up. It's definitely one of those that have 'On-chip' memory controllers. Although that doesn't mean the PWM section, just the memory I/O (and probably frequency too) controller. The PWM section is still on the motherboard.

> Isn't that usually good for stability?
Yes, underclocking usually makes things more stable. And even if your BIOS had the options to control frequency/voltages etc. (laptop BIOS almost never have, for a good reason), it was best to not touch them in case of DDR3, as they are very sensitive to over/under-voltage.

Just curious here - did you check "lshw" with the 1333MHz module alone? Does it report its actual specs when used alone or its 'Effective' specs due to downclocking?

> Anyway, setting the MTU down to **[COLOR="#FF0000"]1392[/COLOR]** seems to have fixed it - everything connects and is fast all the time. I still haven't done much suspend/resume to see how it comes back - that also used to be a common problem. This is all with the internal RTL8191 PCI card - no USB dongles. Comments?
Sure! Are you sure it is 1392? Because as far as I know, and has been my belief so far, 1492 is what is supposed to be most compatible MTU size, since it is the default for windows. Of course lower values should be even more promising as long as the size is a compatible one. I read a couple of times on how to calculate a suitable MTU size, but it was either a bit complex, or involved so many factors that I couldn't memorize it. I vaguely remember it to be probably a multiple of 8 + 4 bits, but not sure.

Unless you report back that it is actually 1492, I think I've just found another promising value to experiment with - 1392 :P

---

### Post by Alex_Lockhart on 2014-02-12
> **varunendra said:**
> 
Just curious here - did you check "lshw" with the 1333MHz module alone? Does it report its actual specs when used alone or its 'Effective' specs due to downclocking?

No, I didn't boot with only the one 1333MHz module. Once I confirmed that it worked and ran memtest for a few minutes, I put in my old "module A" also and booted up. Then I ran the lshw. My snippet above shows both sticks, the new Nanya (rated for 1333MHz) and the old Micron. But since I ran memtest with only the new Nanya module, and it reported the same speeds, I can't imagine that lshw would show anything different if I booted up with only that module. I'll try it if you want, but I really think that the memory is just following the settings given by the memory controller and thus both are running at the same speed. From my memory of hacking desktop parts together years ago, this is the expected behavior - memory will always run at the settings given by the memory controller. At least that's how it worked 8 years ago.

> 
Sure! Are you sure it is 1392? Because as far as I know, and has been my belief so far, 1492 is what is supposed to be most compatible MTU size, since it is the default for windows. Of course lower values should be even more promising as long as the size is a compatible one. I read a couple of times on how to calculate a suitable MTU size, but it was either a bit complex, or involved so many factors that I couldn't memorize it. I vaguely remember it to be probably a multiple of 8 + 4 bits, but not sure.

Unless you report back that it is actually 1492, I think I've just found another promising value to experiment with - 1392 :P

Yes, I'm sure that I have it set currently at 1392. I can't link the reason for that - it was just one of several forum posts I read while Googling around for MTU settings. And yes, I did read plenty about how to find the "ideal" MTU for a given situation. Something about running lots of ping/traceroute/something from the shell, examining the results, doing the math you described with bits and bytes, and getting a number. I didn't worry about that and just used a value somebody reported to be good. I did also see people saying 1492 would be good, but I picked 1392 for some reason.

It did just do its trick where it stopped transferring data (FB messenger, Dropbox, pageloads all quit) even though NetworkManager said it was connected fine. I manually disconnected and reconnected in the NM GUI, and that got it back immediately. This was just once about an hour ago, after hours of working great. Not a big deal, but that's still not how it should be.

---

### Post by varunendra on 2014-02-12
> **Alex_Lockhart said:**
> ..Then I ran the lshw. My snippet above shows both sticks

Yeah, I had noticed that, I meant maybe in some other attempt.. but nevermind. And yes, I'm also aware that the memory operates at what is supported or 'forced' by the controller, that's how BIOS overclocking settings work. But It is not uncommon for the programs to get confused when something is reported wrongly at the BIOS level. That combined with the fact that a higher spec'd memory operates at lower speeds when used in parallel with a lower speed one - I was probably being optimistic. :P

Still, just for the sake of knowledge/experience, if it is not costing you much time, I suggest try it anyway. Both "lshw" and -
```
sudo dmidecode -t memory
```
..although both seem to report the 'Effective' speeds/specs (probably there's no way to report the 'Rated' specs?), but you have an opportunity in hand to confirm that.

---

### Post by Alex_Lockhart on 2014-02-13
> **varunendra said:**
> 
Still, just for the sake of knowledge/experience, if it is not costing you much time, I suggest try it anyway. Both "lshw" and -
```
sudo dmidecode -t memory
```
..although both seem to report the 'Effective' speeds/specs (probably there's no way to report the 'Rated' specs?), but you have an opportunity in hand to confirm that.
I may yet do that. Right now, however, I'm about to go to bed, so I'm going to take the other Nanya 2GB DDR3-1333 module out of my wife's computer and put it into mine. Then I'll run memtest overnight with both of the faster memory modules. It will be interesting to see how long they last. It could really shed some light on why memtest has been failing with my other modules. I hope!

I did run dmidecode just to see what it outputs. Very detailed! I noticed that it said the memory capacity is 8GB; 4GB per slot. What!? I was sure that 4GB total was the most I could use! Some Googling lets me know that both are, in a way, true. Lenovo rates the laptop for 4GB max, but the Intel chipset can handle 8GB max. Many people on forums have put 8GB in these laptops with no problems. I remember that, in 2009 when this computer was new, 4GB memory modules were rare and expensive, and not many people were running 64-bit operating systems (thanks for letting us down, Microsoft!) So I think that had something to do with Lenovo stating the laptop was only rated for 4GB total. Anyway, the important part is that I thought I had maxed out the memory when I installed 4GB, and now a big reason why I wanted to upgrade this old laptop is because I'm running into the memory limits and wanted at least 8GB. So now I can have what I want for only $80! However, if using the old memory from my wife's MacBook Pro will keep my computer from crashing, I'll just wait. Prices always go down.

For your curiosity, here's the info from the current dmidecode. This is with one Nanya DDR3-1333 and one Micron DDR3-1066. Tomorrow I'll have the results of memtest on both of the faster Nanya chips together. I'm hopeful!
```

# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
        Error Detecting Method: None
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 4096 MB
        Maximum Total Memory Size: 8192 MB
        Supported Speeds:
                Other
        Supported Memory Types:
                DIMM
                SDRAM
        Memory Module Voltage: 2.9 V
        Associated Memory Slots: 2
                0x0008
                0x0009
        Enabled Error Correcting Capabilities:
                Unknown

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM Slot 1
        Bank Connections: 0 1
        Current Speed: 42 ns
        Type: DIMM SDRAM
        Installed Size: 2048 MB (Single-bank Connection)
        Enabled Size: 2048 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM Slot 2
        Bank Connections: 2 3
        Current Speed: 42 ns                                                                                                                                                                                                                                                   
        Type: DIMM SDRAM                                                                                                                                                                                                                                                       
        Installed Size: 2048 MB (Double-bank Connection)                                                                                                                                                                                                                       
        Enabled Size: 2048 MB (Double-bank Connection)                                                                                                                                                                                                                         
        Error Status: OK                                                                                                                                                                                                                                                       
                                                                                                                                                                                                                                                                               
Handle 0x0020, DMI type 16, 15 bytes                                                                                                                                                                                                                                           
Physical Memory Array                                                                                                                                                                                                                                                          
        Location: System Board Or Motherboard                                                                                                                                                                                                                                  
        Use: System Memory                                                                                                                                                                                                                                                     
        Error Correction Type: None                                                                                                                                                                                                                                            
        Maximum Capacity: 4 GB                                                                                                                                                                                                                                                 
        Error Information Handle: Not Provided                                                                                                                                                                                                                                 
        Number Of Devices: 2                                                                                                                                                                                                                                                   
                                                                                                                                                                                                                                                                               
Handle 0x0021, DMI type 17, 27 bytes                                                                                                                                                                                                                                           
Memory Device                                                                                                                                                                                                                                                                  
        Array Handle: 0x0020                                                                                                                                                                                                                                                   
        Error Information Handle: No Error                                                                                                                                                                                                                                     
        Total Width: 64 bits                                                                                                                                                                                                                                                   
        Data Width: 64 bits                                                                                                                                                                                                                                                    
        Size: 2048 MB                                                                                                                                                                                                                                                          
        Form Factor: SODIMM                                                                                                                                                                                                                                                    
        Set: None                                                                                                                                                                                                                                                              
        Locator: DIMM 1                                                                                                                                                                                                                                                        
        Bank Locator: Bank 0/1
        Type: DDR3
        Type Detail: Synchronous
        Speed: 1066 MHz
        Manufacturer: 830B            
        Serial Number: 7C516417        
        Asset Tag: 1105
        Part Number: NT2GC64B88B0NS-CG 

Handle 0x0022, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0020
        Error Information Handle: No Error
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: None
        Locator: DIMM 2
        Bank Locator: Bank 2/3
        Type: DDR3
        Type Detail: Synchronous
        Speed: 1066 MHz
        Manufacturer: 802C            
        Serial Number: E82F1066        
        Asset Tag: 0929
        Part Number: 16JSF25664HZ-1G1F1

```

---

### Post by varunendra on 2014-02-13
Yup, as you and I both expected, only the 'Effective' specs.

Looks like the "Part Number" is the only clue that may help looking up their 'Rated' specs and other details online, if one is really curious to find out.

---

### Post by Alex_Lockhart on 2014-02-13
OK, I ran memtest last night with both of the "new" faster modules. Turns out one is a Nanya and one is a Hynix, but otherwise all specs are identical. Why would Apple put one stick from each company in their MacBook? Weird...

Anyway, the memtest froze hard again, after 4:26 this time. Does this mean anything? Now I have lots of memtest data about various modules. I haven't yet run these two faster sticks by themselves for a long time, but I think I'll try that next. Here's the photo of the screen:
[ATTACH=CONFIG]250312[/ATTACH]

I'm tempted to make a spreadsheet with this info, so I can try to organize it and draw some conclusions. Unless this means something to you - I'm guessing this helps confirm that my memory controller or power supply is compromised?

I also think that I'll just run with this new memory in the system for awhile and see how it behaves. If it starts doing its crash-dance again, I'll try again to fix something. If not, then I'll say that I fixed it.

Meanwhile, the network has been behaving pretty good so far using the internal PCI card (with the new driver I installed last week). I do like NetworkManager better than wicd; the interface is better and it handles multiple cards and switching from wired to wireless more seamlessly. And if it will stay connected, I'll be very happy!

Should I mark this as [SOLVED] ? At the moment I'm not aware of anything that needs doing, aside from running some more memtest with the new modules by themselves. Even that's just to collect more data for curiosity's sake.

Here's an idea: Is there a forum full of hardware experts who can help me interpret all these memtest results? I apologize for posting in a networking/wireless forum with a memory problem, but before I posted, my suspicions were with the wireless hardware and/or software.

Again, thanks for all your help. It's been a week of pushing buttons and running tests, and I've learned a lot.

---

### Post by varunendra on 2014-02-14
All the modules failing in more or less the same way is screaming to me that the "problem is anywhere but the RAM modules".

We should also keep in mind that when a system is working intensively, many of its parts are stressed. So while the probability of a RAM controller/PWM controller module being faulty is high, it can be something else as well - including a faulty Power Supply module. In fact it can be anything that may get overheated or otherwise out-of-sync after 3-4 hrs of continuous stress.

It is just that the components supplying/filtering the power to other components tend to suffer this kind of problem more frequently. If it were a Desktop, I would have tried a tested SMPS first. But since it is a laptop, we don't have much options here, not even the BIOS options to tweak things to improve stability at the cost of performance.

> **Alex_Lockhart said:**
> Meanwhile, the network has been behaving pretty good so far using the internal PCI card (with the new driver I installed last week). I do like NetworkManager better than wicd; the interface is better and it handles multiple cards and switching from wired to wireless more seamlessly. And if it will stay connected, I'll be very happy!

Should I mark this as [SOLVED] ?
Yeah if the wireless is working nicely now, that should be done. We have already made it quite off-topic now. :P

> Here's an idea: Is there a forum full of hardware experts who can help me interpret all these memtest results? I apologize for posting in a networking/wireless forum with a memory problem, but before I posted, my suspicions were with the wireless hardware and/or software.
There are many (just search for your memory problem and pick anyone that looks good), but I don't have personal experience with any of them and can't say what is the general behaviour there. Although those that usually come up in search results look good in both aspects (knowledge + general behaviour).

If you use IRC, you may also try the channel #hardware.

---

### Post by Alex_Lockhart on 2014-02-14
> **varunendra said:**
> All the modules failing in more or less the same way is screaming to me that the "problem is anywhere but the RAM modules".
Yeah, I think you've gotta be right. The only unanswered question is why some fail faster than others. But really, until I've done maybe 10 or 20 tests of each configuration and mapped all the results, there's no need to look further. None of them gave an actual memory error, the test always just froze - that is a significant fact. The test never ran longer than 7 hours, but a few times it ran long enough to do several passes successfully. So, as you said, it all points to the problem somewhere besides the RAM modules.

Yes, power supplies are usually the first to fail, specifically by capacitors leaking and changing value. If this were small electronics (not SMD), I'd be tempted to start testing the resistors and capacitors to find which one(s) have gone out of spec, finding a replacement on Digikey, and soldering it all up. But it's a laptop - not even the best techs with the best equipment do that stuff. If some aspect of the motherboard or power supply circuitry is failing, you just replace the whole thing. And with a 5 year old system, that means the whole laptop, not just a new motherboard.

I'll plan to replace the laptop, but as long as it's not crashing more than once a week, I'm not in any hurry. The important thing here is that I know, very specifically, why it's crashing, and what I can do about it. That is a huge step forward!

> Yeah if the wireless is working nicely now, that should be done. We have already made it quite off-topic now. :P
Done! Yes, the wireless has been working great since I went back to NetworkManager and set the MTU down to 1392. I'm not certain that it's "fixed" and won't start being flaky again. But I'll tell myself that the new driver I installed (just before starting this thread) in combination with the lower MTU is the change that fixed the wireless. And if it starts being flaky again, I can post a new thread. This one will be only about the wireless, I promise! :D

Thanks again for your help and sticking with me when it veered off into the wilderness of memtest. It's been a huge help. If you're not being paid for your time, you should find a way to turn your skills into money!

> There are many (just search for your memory problem and pick anyone that looks good), but I don't have personal experience with any of them and can't say what is the general behaviour there. Although those that usually come up in search results look good in both aspects (knowledge + general behaviour).
Thanks. If it starts crashing again, I'll run a bunch of memtest and find a forum that looks good. Maybe I should start reading the Thinkpad forums to see if others have this problem and what they do about it. For now, I'm happy it's working!

I'm off to spend a long weekend with my wife in a little cabin on a lake in the snowy mountains. No electricity or phone service. It'll be a nice break. See you around!

---

### Post by varunendra on 2014-02-14
> **Alex_Lockhart said:**
> I'm off to spend a long weekend with my wife in a little cabin on a lake in the snowy mountains. No electricity or phone service. It'll be a nice break. See you around!
Perhaps the Best Idea of The Month! Have a nice weekend !! :)

> If you're not being paid for your time, you should find a way to turn your skills into money!
"Good Idea" -- I keep telling this to myself. Hope someday I'd be able to overcome my laziness and turn this into reality.. <sigh!> :P

---

