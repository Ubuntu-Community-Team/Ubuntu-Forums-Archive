---
title: "Need Help Getting WiFi to Work"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by redwinedrummer on 2007-07-28
**This post could be related to an Ubuntu bug filed at**: lo        no wireless extensions.

eth1      no wireless extensions. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello guys,

Hope you don't mind another amidst all the "How to get WiFi to work" threads.

I recently bought an Acer Aspire 4520G laptop. It's pre-loaded with Vista, but I want Ubuntu as my primary OS. Ubuntu installed successfully, but my laptop only has its bare features working. Bluetooth, wireless internet, webcam and audio don't work. One problem at a time, and I hope you can help me with my wireless internet first.

I've spent hours sifting through the forums and even tried a madWiFi fix here: [http://www.stchman.com/ath_drv.html]("http://www.stchman.com/ath_drv.html")
I am using an Atheros AR5006E6 card. It's strange that Ubuntu's Restricted Drivers Manager and "lspci" detect my card, but "ifconfig" and "iwconfig" do not.

ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:00:6C:35:C8:AD  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe35:c8ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3094526 (2.9 MiB)  TX bytes:558197 (545.1 KiB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


```

iwconfig
```

lo        no wireless extensions.

eth1      no wireless extensions.

```

The wired adapter is detected, but the wireless isn't.

Making Ubuntu see my card is one problem, and making it actually work is another. I hope there's something we could do soon. Any help is appreciated. 

Thank you very much!

---

### Post by kevdog on 2007-07-28
Im not sure but you might want to try ndiswrapper.  I looked on the madwifi compatibility chart, and didnt see your model number listed: [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros).  I can only guess that your model isnt supported by the drivers (or only at least partially  -- hence being able to see but not connect to the network).

---

### Post by redwinedrummer on 2007-07-28
Oh, I'm sorry that was a typo.

I'm using an Atheros AR5006E**G**, not E6.

Does that improve anything? If I'm not mistaken, it's in MadWifi's list.

Hope this helps.

Using Feisty Fawn 64-bit, by the way.

---

### Post by kevdog on 2007-07-28
At least the documentation hints that 64 bit will work -- I really have no idea (64 is a lot buggier than 32).

Did you read the section about order of module insertion:
> 
Chipset:	AR5006EG = (AR2423)
Chip:	AR2423 (802.11a+b+g)
URL:	[www.atheros.com/pt/bulletins/AR5006EGBulletin.pdf](www.atheros.com/pt/bulletins/AR5006EGBulletin.pdf)
Supports:	IEEE 802.11a, IEEE 802.11b, 802.11g
Device Information:	TBD
Notes:	works with madwifi-r2153-20070224
Notes:	Works on Toshiba Satellite A135
Notes:	Had to change order of module insertion. Works when order is:modprobe wlan_scan_sta,modprobe wlan_wep,modprobe ath_pci

Of course this would imply that you were compiling and installing from source rather than using the built-in drivers

---

### Post by redwinedrummer on 2007-07-28
Hello,

I tried what the Wiki suggested, but didn't improve. I even modified my "/etc/modules". In the guide I mentioned in my first post, I can't even get past the first part, and cannot proceed to installing wpasupplicant because the system still refuses to detect my card.

Do you think installing a 32-bit Feisty would help? Not much would be lost since I've only had Feisty on this Acer for a few hours.

Thanks again.

---

### Post by kevdog on 2007-07-28
Although I fear you will probably have to go back and install the 32bit version, I would first try downloading and then  compiling and installing the madwifi drivers from svn.  (SVN is the most recent unstable version -- under development).  I dont have a madwifi card (broadcom here), but when I tried helping someone last week, I downloaded the svn source, compiled, and installed the drivers on my computer (overwrote the proprietary drivers that were currently installed).  Again I dont know if they work, although the guy said they did, but he didnt have a 64 bit OS version.  If youve compiled things before, you could probably get everything to a point to determine if it was working or not in about 20-30 minutes (so not much effort is what Im trying to say).

---

### Post by redwinedrummer on 2007-07-28
Hello,

I checked the SVN version, but it was only 0.9.3. The latest one is 0.9.3.1 ([http://svn.madwifi.org]("http://svn.madwifi.org")). I reverted my Feisty back to 32-bit but didn't change much. Same things work, same things don't work. Even disabled the restricted drivers. If there's a more update set of drivers, please do point them to me.

I'm starting to think that installing Linux on this laptop is a bad idea (only had success in desktops). I'm seeing a lot of hardware trouble since lspci says so

lspci
```

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 055c (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
01:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0428 (rev a1)
07:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)


```

Plagued with hardware incompatibilities, apparently.

Thanks.

---

### Post by kevdog on 2007-07-29
I feel your frustration, but bail on the madwifi then and go the ndiswrapper router. I think that should work. Make sure to blacklist or unload the madwifi drivers.  Here's some instructions to get you going on ndiswrapper.
Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```
I cant remember the exact output but make sure you dont get any errors.

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by redwinedrummer on 2007-07-29
Hello,

Thank you very much for those detailed instructions.

I am not sure if I removed MadWiFi properly. I only used "sudo make uninstall" in the MadWiFi folder. Seemed to work. If blacklisting were necessary, please do tell me how I can do that.

Everything went fine with the instructions until I typed dmesg. This is what I got. The entire output is too long, so I'll just include what I think is related. If I missed anything, just tell me.

```


[   20.948000] ath_hal: module license 'Proprietary' taints kernel.
[   20.948000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.992000] Linux video capture interface: v2.00
[   21.172000] wlan: 0.8.4.2 (0.9.3.1)
[   21.236000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.252000] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   21.252000] usbcore: registered new interface driver uvcvideo
[   21.252000] USB Video Class driver (v0.1.0)
[   21.272000] ath_pci: 0.9.4.5 (0.9.3.1)
[   21.272000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 17
[   21.272000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LK3E] -> GSI 17 (level, low) -> IRQ 22
[   21.272000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   21.276000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

.
.
.

[ 1775.852000] ndiswrapper version 1.47 loaded (smp=yes)
[ 1775.884000] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded
[ 1775.884000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[ 1775.884000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LK3E] -> GSI 17 (level, low) -> IRQ 22
[ 1775.884000] ndiswrapper (ZwClose:2246): closing handle 0xf78a70e8 not implemented
[ 1775.884000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[ 1775.888000] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001389, count: 4, return_address: f9854064
[ 1775.888000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xdfec9e00
[ 1775.888000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x28
[ 1775.888000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf97b3000
[ 1775.888000] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf97b3000
[ 1775.888000] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[ 1775.888000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 1775.888000] ndiswrapper (mp_halt:258): device f7815c00 is not initialized - not halting
[ 1775.888000] ndiswrapper: device eth%d removed
[ 1775.888000] ACPI: PCI interrupt for device 0000:07:00.0 disabled
[ 1775.888000] ndiswrapper: probe of 0000:07:00.0 failed with error -22
[ 1775.888000] usbcore: registered new interface driver ndiswrapper

```

Hope this helps.

---

### Post by kevdog on 2007-07-29
Kind of a stab in the dark, but add the to the /etc/modprobe.d/blacklist file

blacklist ath_pci
blacklist ath_hal

Reboot and then check dmesg.  Tell me what happens.  Lets say you still get the same errors with the ath part (top part of what you posted).  I would then remove them manually with:
sudo rmmod ath_pci
sudo rmmod ath_hal

---

### Post by redwinedrummer on 2007-08-01
Hello!

Sorry for the late reply, I've been busy, but there has been major progress!

We've been having trouble because we've been working at the wrong Atheros model. I booted into the pre-loaded Vista and checked my hardware settings. Ubuntu and Vista were telling a different story. Ubuntu reported an AR5006EG, but Vista reported an AR5007EG. I checked the MadWiFi compatibility list immediately and there were a set of instructions. I follow the trail and it seems that the AR5007EG is so new that HAL and MadWiFi cannot use them yet. So ndiswrapper was used. I downloaded the drivers, redid the procedure and now the wireless is now working.

As expected, there is no encryption report yet. As of now, the wireless is working very well without a password. That's a big step.

I followed the guide I included in my first post that was supposed to enable the security encryptions, but did not work. Are there any other ways to work around?

Thank you very much! Faith has been restored in my Linux laptop.

---

### Post by noob12 on 2007-08-01
Before proceeding, install the wpasupplicant package

```
sudo aptitude install wpasupplicant
```

This is needed if you use WPA, and even if you use WEP locally you may roam to places using WPA and will need it for that.

Once you've installed, try the normal Network Manager GUI and post here for further help.

---

### Post by redwinedrummer on 2007-08-01
Hello,

Yes, I have installed wpasupplicant and followed all the steps in the [http://www.stchman.com/ath_drv.html]("http://www.stchman.com/ath_drv.html") guide, but did not change anything. There are no WPA entries. Only WEP.

---

### Post by noob12 on 2007-08-01
In Network Manager, put the interface in Roaming mode.  Then when you select the AP from the list  with signal bars, you should get a dialog which allows you to select WPA and the authentication mode.

---

### Post by redwinedrummer on 2007-08-01
Hello,

There doesn't seem to be any "blue bars." I tried reinstalling wpasupplicant, but didn't change anything. I can only access my configurations via the System--> Administration--> Network GUI.

---

### Post by noob12 on 2007-08-02
I'm not sure you put the interface in roaming mode.  Equivalently, you can remove mention of the interface in /etc/network/interfaces.

---

### Post by redwinedrummer on 2007-08-02
Hello,

The wireless device has been on roaming mode, and I have commented out all entries in my etc/network/interfaces file. No improvement.

When I boot Ubuntu without the splash, I can see that my wlan0 supports encryptions. I checked my modules file and perhaps wpasupplicant needs to be added there?

Thanks.

---

### Post by noob12 on 2007-08-02
Because wpasupplicant is not a kernel module you shouldn't list it there.  We need another peek at where you really are.  Can you please post the outputs of these.  Sorry for all of these at once, but I hope it will reduce the round-trips.

```

lshw -C network

ndiswrapper -l

ifconfig -a

iwconfig wlan0

iwlist scan

cat /etc/modules

cat /etc/modprobe.d/blacklist

cat /etc/modprobe.d/ndiswrapper

ps -ef | grep wpa

```

---

### Post by kevdog on 2007-08-02
Perhaps this link will help you, this is how I got mine up and running:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by redwinedrummer on 2007-08-03
Of course, no problem. I understand. There's so much to look out for in LInux that I needed help in terms of the commands to use to check the settings. Here they are.

lshw -C network
```
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth1
       version: a2
       serial: 00:00:6c:19:1e:a2
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=192.168.1.21 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
       resources: iomemory:f2488000-f2488fff ioport:30f8-30ff iomemory:f2489c00-f2489cff iomemory:f2489800-f248980f irq:21
  *-network
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@07:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:99:80:82
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=,11/15/2006,5.1.1.9 latency=0 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:f2000000-f200ffff irq:16
```

ndiswrapper -l
```

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

```

ifconfig -a
```
eth1      Link encap:Ethernet  HWaddr 00:00:6C:19:1E:A2  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe19:1ea2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:892268 (871.3 KiB)  TX bytes:187981 (183.5 KiB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43176 (42.1 KiB)  TX bytes:43176 (42.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7E:99:80:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:f2000000-f2010000
``` 

iwconfig wlan0
```
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

```

cat /etc/modules
```
fuse
lp
sbp2
ndiswrapper

```

cat /etc/modprobe.d/blacklist
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

```

cat /etc/modprobe.d/ndiswrapper
```
alias wlan0 ndiswrapper

```

ps -ef | grep wpa
```
aj        8586  6464  0 16:51 pts/0    00:00:00 grep wpa

```

---

### Post by redwinedrummer on 2007-08-03
Kevdog,

Thanks for the link, but I've already tried that, but didn't help. There still no "blue bars" for me, and consequently, no network manager (like the one in the link) and no encryption.

---

### Post by noob12 on 2007-08-03
Please add the line **blacklist ath_pci** to your /etc/modprobe.d/blacklist.

Also, if there is a hardware switch for your wireless, make sure it is turned on.  Also check the BIOS to make sure wireless is enabled.  Your scan and iwconfig results indicate that your radio is OFF.

After you've done those things, and noting that the BIOS check necessitates a reboot, please include the output of **dmesg** on the following boot.

---

### Post by redwinedrummer on 2007-08-03
Hello,

Added ath_pci to the blacklist. Nothing.

My device does have a hardware switch, but it doesn't work in Linux. The LED is extremely faint that I have to cover it with my hand to see it. Pressing it doesn't seem to make a difference. I think my device is working since I can connect to the internet without encryption. There's no BIOS option.

The output is too long, so I'll just add anything that's relevant. Tell me if I missed anything.

dmesg
```
[   20.972000] usbcore: registered new interface driver uvcvideo
[   20.972000] USB Video Class driver (v0.1.0)
[   21.384000] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   21.424000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   21.548000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 16
[   21.548000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 16 (level, low) -> IRQ 23
[   21.548000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   22.868000] ALSA /home/aj/Desktop/realtek-linux-audiopack-4.06a/alsa-driver-1.0.14-4.06a/pci/hda/../../alsa-kernel/pci/hda/patch_si3054.c:244: si3054: cannot initialize. EXT MID = 0000
[   23.052000] fuse init (API version 7.8)
[   23.128000] lp: driver loaded but no devices found
[   23.204000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   23.288000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   23.288000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 23
[   23.288000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LK3E] -> GSI 23 (level, low) -> IRQ 16
[   23.288000] ndiswrapper (ZwClose:2467): closing handle 0xf7fcfae8 not implemented
[   23.288000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   23.700000] ndiswrapper: using IRQ 16
[   24.200000] wlan0: ethernet device 00:19:7e:99:80:82 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   24.200000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   24.208000] usbcore: registered new interface driver ndiswrapper
[   24.248000] Adding 1381548k swap on /dev/disk/by-uuid/d5505157-d66c-4650-8b52-5810f86bbb1a.  Priority:-1 extents:1 across:1381548k
[   24.516000] EXT3 FS on sda5, internal journal
[   24.812000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.868000] NTFS volume version 3.1.
[   24.908000] NTFS volume version 3.1.
[   24.944000] NTFS volume version 3.1.
[   25.444000] NET: Registered protocol family 17
[   27.156000] Using specific hotkey driver
[   27.220000] ibm_acpi: ec object not found
[   27.268000] ACPI: AC Adapter [ACAD] (on-line)
[   27.288000] No dock devices found.
[   27.312000] input: Power Button (FF) as /class/input/input5
[   27.312000] ACPI: Power Button (FF) [PWRF]
[   27.312000] input: Power Button (CM) as /class/input/input6
[   27.312000] ACPI: Power Button (CM) [PWRB]
[   27.324000] input: Lid Switch as /class/input/input7
[   27.324000] ACPI: Lid Switch [LID]
[   27.332000] input: Sleep Button (CM) as /class/input/input8
[   27.332000] ACPI: Sleep Button (CM) [SLPB]
[   27.384000] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[   27.384000] ACPI: Video Device [Z004] (multi-head: yes  rom: no  post: no)
[   27.408000] ACPI: Battery Slot [BAT1] (battery present)
[   27.492000] wmi_add device=c19a4000
[   27.492000] calling WQBA
[   27.512000] pcc_acpi: loading...
[   27.748000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (version 2.00.00)
[   27.748000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[   27.748000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[   27.748000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   32.520000] ppdev: user-space parallel port driver
[   35.132000] apm: BIOS not found.
[   35.380000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   35.540000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   35.540000] NFSD: starting 90-second grace period
[   37.024000] Bluetooth: L2CAP ver 2.8
[   37.024000] Bluetooth: L2CAP socket layer initialized
[   37.028000] Bluetooth: RFCOMM socket layer initialized
[   37.028000] Bluetooth: RFCOMM TTY layer initialized
[   37.028000] Bluetooth: RFCOMM ver 1.8
[   40.016000] NET: Registered protocol family 10
[   40.016000] lo: Disabled Privacy Extensions
[   40.016000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.260000] eth1: no IPv6 routers present
[  113.944000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by noob12 on 2007-08-03
OK.  Now having done that, I'm looking for a change in:
```

iwconfig
iwlist scan

```

Also please post the output of
```

cat /sys/class/net/*/device/rf_kill

```

---

### Post by redwinedrummer on 2007-08-03
iwconfig

```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The iwlist scan showed strange behavior. I ran it first and it showed this:

iwlist scan 1
```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:DF:E7:F4
                    ESSID:"Perez Family Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
```

It seems to have connected to our router. But then I ran it again to make sure

iwlist scan 2
```

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

```

cat didn't find any /sys/class/net/*/device/rf_kill

---

### Post by noob12 on 2007-08-03
Momentarily forgot we were working with ndiswrapper (hence the **cat** finding nothing).

Can you please enable ESSID broadcast on your AP?

---

### Post by redwinedrummer on 2007-08-03
SSID broadcast has been enabled with my router (Netgear WNR854T) ever since. It's a draft-N router, but I set it to run in 54mbps a/b/g compatibility mode. Not sure if SSID and ESSID are the same, though.

I'm baffled why iwlist scan found the network at first then disappeared. It might be possible that it was because I disabled roaming and manually entered the network details for testing. But I put it back to roaming and rebooted. The iwlist scan I posted was after that reboot.

---

### Post by noob12 on 2007-08-03
Oh, and just noticed something else. Radio tuner seems to be sitting on the wrong frequency.  Turning on your ESSID broadcast may help this.

You can also try this

```

sudo iwconfig wlan0 freq 2.437G
sudo iwconfig wlan0 channel 6

```
and rescan.

---

### Post by redwinedrummer on 2007-08-03
I don't think there's an ESSID broadcast for my router. Only SSID. I performed the manual reconfiguration you posted, and it work... for a while.

I rebooted after and a scan was successful.

iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:DF:E7:F4
                    ESSID:"Perez Family Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  

```

But 5 minutes later, I rescanned. Disappeared. Nyargh. I wonder what Gutsy can do to address these hardware problems in October.

---

### Post by noob12 on 2007-08-03
Rebooting would have undone the manual configuration.  We can get these to run automatically though.  Can you rerun the manual configuration and see if this fixes things, then actually try to connect?

If that works, we can at least set that up to run automatically.

---

### Post by redwinedrummer on 2007-08-03
I see. I'm sorry, I didn't see rebooting would undo the changes. Although I ran the scan right after, it didn't find anything. 

I'll test it again first thing in a few hours and so you also won't wait for a response in vain. It's currently 1:49AM here. I'll just reply tomorrow. Troubleshooting such is stressful business. Hehe.

I'll get back to you ASAP. Thanks for all the help!

---

### Post by noob12 on 2007-08-03
Maybe because you're tired, but I thought you said it worked for awhile after running the commands.  Then you rebooted.
> I performed the manual reconfiguration you posted, and it work... for a while.

Anyway, yes.  Resume when you're fresh.

---

### Post by redwinedrummer on 2007-08-03
Hello,

I redid everything, and here are the steps I took for clarification.

1. Boot Ubuntu. Run iwlist scan for testing (no configuration yet)
2. iwlist scan successful
3. Commands were manually inputed
4. iwlist scan successful
5. Unplug LAN cable to isolate wlan0*
6. After a few minutes, iwlist scan fails.

*I use a wired LAN connection in the mean time because I have to turn the encryption off in my router everytime (WPA-TKIP is used). A lot of people use the router and changing router settings will have to cut connections. And as posted previously, wireless works well with encryption turned off, but if turning off encryption is necessary, then let it be so.

---

### Post by kevdog on 2007-08-03
Try renaming your essid on the router to a name without spaces -- Ive seen this cause problems with some people.

Can you let me in on the manual configurations you are trying??

---

### Post by redwinedrummer on 2007-08-04
Tried renaming the router SSID and made the manual configurations. So far so good! iwlist scan has been consistentently successful.

Kevdog, what do you mean with "let you in?" If you meant what commands I'm using, they're the ones posted by noob12

```

sudo iwconfig wlan0 freq 2.437G
sudo iwconfig wlan0 channel 6

```

---

### Post by noob12 on 2007-08-04
When iwlist scan starts showing "no scan results" does **iwconfig** again show a frequency that is not 2.437Ghz ?

I just noticed another thing.  In posting #25, your ps listing showed that wpa_supplicant wasn't running.  If wpa_supplicant is installed it normally gets started when the interface comes up via /sbin/ifup or when wireless gets enabled by NetworkManager.   When you right click on the Network Manager icon in the panel, do you see an Enable Wireless line?  If so, and can you make sure the check mark is on on that line?  If not click it.

We should be seeing **ps -ef | grep wpa** show wpa_supplicant.

---

### Post by kevdog on 2007-08-04
So does that mean you can connect with WPA??

Another configuration that helped me (some but not totally) from dropping connections:
sudo iwconfig wlan0 mode Managed

---

### Post by kevdog on 2007-08-04
Can you also tell me the type of WPA you are using??

WPA 1 or 2?
Cipher Type: TKIP or AES or both
WPA-PSK??

Sometimes these settings are also shown in 
iwlist scan

so if you could post that too it would be great!

---

### Post by noob12 on 2007-08-04
OK.  This thread is getting long.  If  the AP of interest is the one listed in post #25,  It is WPA1, TKIP, PSK.

---

### Post by redwinedrummer on 2007-08-04
Kevdog,
My device has been in managed mode and as you posted, I renamed my SSID and the connection has been stable. So far so good. It seems to get connected (even my Netgear control panel in 192.168.1.1 reports my laptop connectin), but no internet access.

I'm using WPA1-PSK (TKIP). I don't use higher encryption methods (WPA2 / WPA+WPA2) since it causes problems with other wireless devices. All Atheros models in other laptops.

noob12,

iwlist scan consistently does a successful scan, but iwconfig does report a different frequency. iwlist reports 2.437Ghz, while iwconfig reports 2.412Ghz.

iwlist scan
```

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:DF:E7:F4
                    ESSID:"PerezFamilyNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 

```

iwconfig
```

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Regarding wpa_supplicant, I don't recall seeing wpa_supplicant as the system starts (verbose boot), but there is a line that states wlan0 supporting encryptions. And yes, ever since the SSID was renamed, "Enable Wireless" appeared, and it is checked.

ps -ef | grep wpa
```
aj        8024  6440  0 12:50 pts/0    00:00:00 grep wpa

```

Here's confirmation that wpa_supplicant is installed.

aptitude show wpasupplicant
```

Package: wpasupplicant
State: installed
Automatically installed: no
Version: 0.5.7-0ubuntu2
Priority: important
Section: net
Maintainer: Reinhard Tartler <siretart@ubuntu.com>
Uncompressed Size: 655k
Depends: libc6 (>= 2.5-0ubuntu1), libdbus-1-3 (>= 0.94), libncurses5 (>= 5.4-5),
         libreadline5 (>= 5.2), libssl0.9.8 (>= 0.9.8c-1), lsb-base (>= 3.0-6)
Recommends: dhcp3-client
Suggests: libengine-pkcs11-openssl, guessnet, iproute

```

Can we force wpa_supplicant to run at start up?

---

### Post by kevdog on 2007-08-04
Not only is this thread getting long, its being updated at such a slow pace I can hardly remember what was done compared to the last time I read it.

Anyway I'll cut and paste this for me just to refer too

```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:DF:E7:F4
                    ESSID:"Perez Family Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK
```

Im assuming the ESSID is no longer "Perez Family Network"

Here is something we can try to thoroughly debug WPA connectivity.  Everything will have to be done at them command line, if this works then it demonstrates WPA does in fact work and we can move onto using an automated interface such as NetworkManager, WICD, etc.

Do the following to create /etc/wpa_supplicant.conf
```

gksu gedit /etc/wpa_supplicant.conf
```

Inside the file put the following (notes follow below):

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="YOUR_ROUTER_SSID"
       scan_ssid=0
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="ASCII_PASSPHRASE"
}

```

***Notes
ssid of router -> name of router must be in quotes, example:
ssid="Linksys"

psk -> ASCII password must be in quotes, dont have a password with special characters or spaces, example:
psk="JohnDoePassword"

Then at command line enter these sequentially:

```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
```

Hopefully at the end you will be presented with a local IP address.  That is what you want.  Submit any errors you get along the way

---

### Post by redwinedrummer on 2007-08-04
Yes, I ended up with an IP address.

I had errors in the *killall* command: no process to kill. Both wpa_supplicant and dhclient. And rm did not find any dhclient.pid Also in *ip route flush*: nothing to flush.

Everything else proceeded smoothly, except for the *sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd*. It took a very long while and after screens of code, the terminal stops and repeats itself after every ~2 minutes.

```

wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
]RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8

```

I launched another terminal and proceeded. Everything else went well. I ended with a local IP address

---

### Post by noob12 on 2007-08-04
I think I'm just interfering.  I'll leave you in kevdog's very capable hands.  Too confusing with both of us in the mix.  It looks like you're getting very close now.

---

### Post by redwinedrummer on 2007-08-04
Alright, thank you very much, noob12! Appreciate all the help. If you have something in mind, I can try it out.

Thanks again!

---

### Post by kevdog on 2007-08-04
I dont like when noo12 exits the thread -- he offers some very good insights into how things work.

Dont worry about some of the errors from some of the commands, some of the things are redundant, the major problem (or maybe its not) is with the wpa_supplicant command.

Change the following procedure to this,

```
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf 
```

This basically will eliminate the debug messages and start the process in the background.  I want to know if you can connect in one screen.  Also lets try converting your password to hex (even though this probably has nothing to do with it). You do this by the following method:

Use the following command (' ' single quotes required):

```
wpa_passphrase 'your_essid' 'your_ascii_key'
```

Resulting in an output like...
> 
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}

Your hex password is the value listed by psk.  So change your /etc/wpa_supplicant.conf file to have the following:

```
psk=HEX_PASSPHRASE for example:
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
```

Sorry I dont know a lot about those errors you are getting that you described below -- I just know that its not normal to get these.

---

### Post by redwinedrummer on 2007-08-04
Hello,

I did some research on this problem (wpa_supplicant looping in an error) and traced the debugging information. It seems like wpa_supplicant is having trouble associating itself with ndiswrapper, hence the infinite loop. "Association request to the driver failed" Here are some relevant literature: [http://hostap.epitest.fi/bugz/show_bug.cgi?id=134]("http://hostap.epitest.fi/bugz/show_bug.cgi?id=134") and [http://lists.freebsd.org/pipermail/freebsd-net/2006-August/011265.html]("http://lists.freebsd.org/pipermail/freebsd-net/2006-August/011265.html") You might be able to make something out of these.

Also, I checked the syntax of wpa_supplicant itself. I hope you don't mind, but I typed *-Dndiswrapper* instead of *-Dwext* since the driver we're using is ndiswrapper.

Alright, did all the commands. Converted the string to hex and replaced the psk variable in the wpa_supplicant.conf file.

PS
I also made changes in the router itself. Through the course of our troubleshooting, we saw that even if we force the device's operating frequency via *iwconfig wlan0 freq XXXG*, the device is still running on the wrong frequency. So I set my router to run at Channel 1, 2.412Ghz to adjust to the device. Not the other way around.

---

### Post by kevdog on 2007-08-04
I think technically its supposed to be wext but I think this is a mute issue:

From ndiswrapper website:
> Note: With ndiswrapper version 1.12 and older, use -Dndiswrapper instead of -Dwext

Remind me quick what chipset you are trying to work with (Broadcom, atheros, etc).  I noticed a common theme in all the threads saying wpa was having problems associating with the driver.  Perhaps we could look for a different windows driver for your card!!

For my information:
Is the card working at all?  And you are using ndiswrapper version 1.47 correct??

---

### Post by redwinedrummer on 2007-08-04
Hello,

I am using an Atheros AR5007EG device with Nvidia PCI adapters. Yes, the card is working. In fact, I can use it to surf the web (in Ubuntu) with encryption disabled. And yes, ndiswrapper 1.47.

Alright, will use -Dwext next time, but either way, wpa_supplicant ends up with an infinite loop.

---

### Post by kevdog on 2007-08-04
I found this link from the ndiswrapper website that I think describes your card, it lists a link to some drivers:
```

#
Laptop: Acer Aspire 5570Z

    *
      Chipset: Atheros AR5007EG (rev 01)
    *
      PCI ID: 168c:001c
    *
      Driver: ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/802ABG_Atheros_v5_1_1_9.zip
    *
      ndiswraper version : > 1.45
    *
      other : need to uninstall all madwifi kernel module before use ndiswrapper
    *
      other : if you can’t get any AP signal, try to enable wifi radio through wlan switch (it’s look like nothing happened when you try to enable through wifi, because the LED is not compatible with linux(i’m using ubuntu 7.04), but if you try ‘iwlist wlan0 scan’ you’ll see some AP information
```


Maybe you could try the link!

---

### Post by redwinedrummer on 2007-08-04
Hi,

Sorry to burst the bubble, but that's the Windows driver I'm already using. =( The LED issue is consistent, too.

Uh-oh. We have a problem. Since we were on the topic of ndiswrapper's version, I just checked mine and it said 1.38. For some weird reason, 1.38 is installed, not 1.47. I distinctly remember downloading and compiling the 1.47 one. In fact, I downloaded 1.47 again and the file is a duplicate, meaning the file has been there. I reinstalled 1.47 and will also reinstall the driver. So strange.

I'll get back to you ASAP.

---

### Post by kevdog on 2007-08-04
Hey, since you have an unencrypted connection, install the svn version of ndiswrapper  Here are some instructions:

Here are some instructions from a previous post of mine:
Then do the following at the command line:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install subversion build-essential linux-headers-`uname -r`

```
Subversion is the utility that we can use to download the svn version of ndiswrapper.  The other two packages are so we can compile from source.

Ok lets grab the ndiswrapper svn sources and compile (but not install them):
```

cd ~
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper ~/ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make
```

Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

Ok that should have about killed the old ndiswrapper version.  Now lets install the new version:
```
cd ~/ndiswrapper_svn
sudo make install
```

Timeout:
Check if everything went OK
```
ndiswrapper -v
```
This should return version 1.48rc1 or something similar.  If not stop and do not proceed.

If everything is good, proceed according to the regular instructions!!!

---

### Post by redwinedrummer on 2007-08-04
Hello,

Before we try using the SVN version of ndiswrapper, here's an update after installing the newest stable versions of both ndiswrapper (was 1.3x now 1.47) and wpasupplicant (was 0.5.5 now 0.5.8 ). I compiled wpasupplicant only with the relevant drivers

```

CONFIG_EAP_PSK=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_NDISWRAPPER=y
CONFIG_WIRELESS_EXTENSION=y

```

Did all the steps discussed and here's the result of the wpa_supplicant command. iwlist scan finds the access point.

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line 1: Invalid configuration line 'ctrl_interface=/var/run/wpa_supplicant'.
ap_scan=1
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=18):
     50 65 72 65 7a 46 61 6d 69 6c 79 4e 65 74 77 6f   PerezFamilyNetwo
     72 6b                                             rk              
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='PerezFamilyNetwork'
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

```

I hope we're making progress. 

Let's try the SVN approach another time, if you don't mind. I'll just  take a break. It's almost 1AM. I'll get back to you soon.

Thanks!

Btw, I only remove my router's encryption for testing. I wouldn't want to permanently remove encryption.

---

### Post by kevdog on 2007-08-04
You are going hard core with the compiling...but I like this.  I think you may however want to compile the source again.  I pulled this from the ndiswrapper web site that you should include (at a minimum) these options:

CONFIG_DRIVER_WEXT=y
CONFIG_CTRL_IFACE=y

Because the second configuration wasnt included, may be the reason you are getting this error:
```
Line 1: Invalid configuration line 'ctrl_interface=/var/run/wpa_supplicant'.
```

Im going to try to compile myself and see what I can find..Nothing like breaking a good network configuration for me!

---

### Post by redwinedrummer on 2007-08-04
Hello,

I recompiled wpa_supplicant with the missing interface and ran everything again.

wpa_supplicant just keeps on looping at the end.

```

WPA: Key negotiation completed with 00:14:6c:df:e7:f4 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:14:6c:df:e7:f4 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8

```

So near, yet so far!

---

### Post by kevdog on 2007-08-04
Not meaning to keep spinning wheels, but why dont you just installed the latest developmental version.  I managed to compile wpa_supplicant, but I too was getting some different errors.  Im not sure why?? Reverted back to latest developmental version -- all good.

Can you post your wpa_supplicant.conf file??

---

### Post by redwinedrummer on 2007-08-05
Alright, I recompiled wpa_supplicant and installed 0.6. Also installed the RC version of ndiswrapper and reinstalled the Windows driver of my device. Still the same. Argh. Still loops at the end.

```

wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8


```

---

### Post by kevdog on 2007-08-05
Hey at least you compiled it right!!  Id still try a different driver if you can find one, and beyond that -- I really at odds how to help you.  

Have you checked dmesg for any errors??

---

### Post by redwinedrummer on 2007-08-05
Yep, they compile okay.

Here's my relevant dmesg

```

[   23.120000] ndiswrapper version 1.48rc1 loaded (smp=yes)

[   23.288000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded

[   23.288000] ndiswrapper (ZwClose:2247): closing handle 0xf78538a8 not implemented

[   23.712000] ndiswrapper: using IRQ 22

[   23.916000] wlan0: ethernet device 00:19:7e:99:80:82 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   23.920000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

Sigh. Oh well. We're at the end of our wits and we've done so much. It's alright.

Thanks anyway for all the help, noob12 and kevdog! I really appreciate it. After this, I'll move on to addressing the other problems of this laptop: audio, webcam and microphone. I've installed the latest ALSA, configured it and the associated driver, and nothing. But that's another topic. I'll see what I can do.

Once again, thank you very much! Really appreciate it.

If there are any other ideas, thread is still open. Or alternatively, message me.

'til next time!

---

### Post by kevdog on 2007-08-05
Can you post your wpa_supplicant.conf file??

---

### Post by redwinedrummer on 2007-08-05
Here,

```

crtl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
             ssid="PerezFamilyNetwork"
             scan_ssid=0
             proto=WPA
             key_mgmt=WPA-PSK
             pairwise=TKIP
             group=TKIP
             psk="chinadrum"
}

```

---

### Post by kevdog on 2007-08-05
Try something as basic as follows (an example of course) Im getting desperate:
ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
 }

---

### Post by redwinedrummer on 2007-08-06
Tried it. Nada. =|

---

### Post by audrix on 2007-10-07
Hi I have a Toshiba Satellite U300 dual-core with an Atheros AR5006EG under Gutsy (beta)
I tried your procedure and I was able to have my wireless car detected by network-manager but I am not o view any WLANs in my area :(

Does anybody can help me?

Audrey

---

### Post by audrix on 2007-10-07
sorry I mistaped: I am not able to view any WLANs in my area...

---

### Post by kevdog on 2007-10-07
Can you post
lshw -C network
iwlist scan
ifconfig

---

