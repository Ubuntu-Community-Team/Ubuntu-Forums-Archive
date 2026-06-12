---
title: "Wireless: Can see networks, but can't connect"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Absurdiverse on 2008-05-28
Alright, I've been struggling with my internet in Ubuntu for the last two days. I'm giving it one more go and if this doesn't work I'm scraping the whole Linux idea completely.

I followed the guide and blacklisted the stock bcx (or whatever they are) drivers and installed Ndiswrapper (to my knowledge). I then installed the drivers for my wireless card. Everything seemed great. I was relieved to find that I finally could see my wireless connection. But! But! I can't connect. To anything. I can't connect when it is secure, unsecure, visible, invisible, WEP, WAP, WAP2, XYZE6! It does it's little 'trying to connect' thing, and nothing. I checked ndiswrapper -l, and it said the device and driver were both installed. I checked lspci and everything seems fine. I really have no idea what to do.

I should note that I do not have a hard connection to the computer with Ubuntu on it at the moment. If you need me to get any information from the terminal I suggest you request it in bulk as I will have to run back and forth between computers to get it to you.

My card is the D-Link DWA542. Someone suggested I use Madwifi, but it doesn't list this as one of their supported cards. Also I think if I can at least SEE the wireless networks around my house then there is some sort of connection going on between Ubuntu and the card.

Any help? Thanks.

---

### Post by ukripper on 2008-05-30
Can you post output of following commands:

```
lspci
```

```
iwconfig
```

```
dmesg | less
```

```
cat /etc/network/interfaces
```

```
cat /etc/modprobe.d/blacklist
```

```
iwscan
```

And finally , are you using WPA/WEP or WPA2?

---

### Post by e78174 on 2008-05-30
I am having the same problem.


e78174@e78174-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

e78174@e78174-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


dmesg | less:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-17-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 13:57:17 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
[    0.000000] Command line: root=UUID=4b2f6984-f4d9-47bb-ae4c-68977bed65ec ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fea0000 (usable)
[    0.000000]  BIOS-e820: 000000003fea0000 - 000000003feac000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003feac000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261792) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
:

e78174@e78174-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

e78174@e78174-laptop:~$ cat /etc/modprobe.d/blacklist
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx



e78174@e78174-laptop:~$ iwscan
bash: iwscan : commande introuvable


I use WPA.

---

### Post by ukripper on 2008-05-30
> **e78174 said:**
> I am having the same problem.



I use WPA.

i can see your wireless card is not configured at all and your chipset is bcm4318.

This guide will work for you, try this [http://ubuntuforums.org/showthread.php?p=4604505#post4604505](http://ubuntuforums.org/showthread.php?p=4604505#post4604505)

---

### Post by e78174 on 2008-05-30
I can connect to the unsecured networks, but not to the secured.

---

### Post by ukripper on 2008-05-30
> **e78174 said:**
> I can connect to the unsecured networks, but not to the secured.

That means your wireless card is working ok. you need to configure your WPA to access your access point. Have you tried network manager?

---

### Post by Absurdiverse on 2008-05-30
Okay, I think it's fairly important that I mention that I have given up on ndiswrapper at the suggestions of a couple users in IRC. I have since moved on to Madwifi with supposed supports my chipset. I also now have a hard connection to the internet so it will be much easier to provide feedback. I have tried to install Madwifi by following this guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#Troubleshooting]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#Troubleshooting") and although I didn't seem to get any errors, it still doesn't seem to be picking up my card.

> ryan@ryan-ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)
02:01.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


> ryan@ryan-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


(This provides an enormous amount of text, is that correct?
[http://pastebin.com/m168fe4b1]("http://pastebin.com/m168fe4b1")

> ryan@ryan-ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


> ryan@ryan-ubuntu:~$ cat /etc/modprobe.d/blacklist
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


> ryan@ryan-ubuntu:~$ iwscan
bash: iwscan: command not found


And currently encryption is off, but I was using WPA/WPA2 (auto).

---

### Post by ukripper on 2008-05-30
Sorry I gave you wrong command before - 

Can you post output of the following:

```
sudo iwlist ath0 scan
```

```
sudo iwlist wlan0 scan
```

---

### Post by Absurdiverse on 2008-05-30
No problem.

> ryan@ryan-ubuntu:~$ sudo iwlist ath0 scan
[sudo] password for ryan: 
ath0      Interface doesn't support scanning.

ryan@ryan-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


---

### Post by ukripper on 2008-05-30
Are you sure that you are able to see available networks through network manager?

---

### Post by Absurdiverse on 2008-05-30
> **ukripper said:**
> Are you sure that you are able to see available networks through network manager?

No. As I said (sorry if you didn't understand what I was trying to say), I gave up on ndiswrapper. And at the urging of several people on the IRC chat I've gone for the madwifi drivers. I did a clean install to make sure I wasn't tripping over myself. So as of now, from a clean 8.04 install, all I've done is tried to install madwifi. I can no longer see any APs in the network manager.

---

### Post by ukripper on 2008-05-30
> **Absurdiverse said:**
> No. As I said (sorry if you didn't understand what I was trying to say), I gave up on ndiswrapper. And at the urging of several people on the IRC chat I've gone for the madwifi drivers. I did a clean install to make sure I wasn't tripping over myself. So as of now, from a clean 8.04 install, all I've done is tried to install madwifi. I can no longer see any APs in the network manager.

Sorry for misunderstanding. Now I can understand why those commands didn't return anything.

Have you tried this guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) 
while installing madwifi drivers?

---

### Post by Absurdiverse on 2008-05-30
> **ukripper said:**
> Sorry for misunderstanding. Now I can understand why those commands didn't return anything.

Have you tried this guide: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) 
while installing madwifi drivers?

Yes, that is the exact guide I followed. I didn't notice any errors, but it doesn't seem to have worked, so perhaps I messed up somewhere.

---

### Post by ukripper on 2008-05-30
> **Absurdiverse said:**
> Yes, that is the exact guide I followed. I didn't notice any errors, but it doesn't seem to have worked, so perhaps I messed up somewhere.

have you done this step at the end:
```
modprobe ath_pci
```

if not then can you do it now in terminal

---

### Post by Absurdiverse on 2008-05-30
> **ukripper said:**
> have you done this step at the end:
```
modprobe ath_pci
```

if not then can you do it now in terminal

Yes, I did that before. I didn't get any apparent errors.
Oh, and I just noticed if I right click the network manager icon in my notification area that I get a 'Edit Wireless Networks' option. I'm not sure if that relates though.

---

### Post by ukripper on 2008-05-30
> **Absurdiverse said:**
> Yes, I did that before. I didn't get any apparent errors.
Oh, and I just noticed if I right click the network manager icon in my notification area that I get a 'Edit Wireless Networks' option. I'm not sure if that relates though.

If you click on that option what happens?

---

### Post by Absurdiverse on 2008-05-30
> **ukripper said:**
> If you click on that option what happens?
A window opens up called Wireless Networks, but there are no networks and I can't seem to add one.

---

### Post by ukripper on 2008-05-30
> **Absurdiverse said:**
> A window opens up called Wireless Networks, but there are no networks and I can't seem to add one.

Can you try once more reinstalling madwifi drivers using the same guide and then we  can go from there

---

### Post by Absurdiverse on 2008-05-30
> **ukripper said:**
> Can you try once more reinstalling madwifi drivers using the same guide and then we  can go from there

Okay. I'm a little iffy on the beginning though. Should I be starting at 'Removing Old Modules'? I sort of skipped the Requirements part because I didn't see anything I needed to do in there.

---

### Post by ukripper on 2008-05-30
> **Absurdiverse said:**
> Okay. I'm a little iffy on the beginning though. Should I be starting at 'Removing Old Modules'? I sort of skipped the Requirements part because I didn't see anything I needed to do in there.

remove old modules otherwise it won't work.

---

### Post by Absurdiverse on 2008-05-30
> **ukripper said:**
> remove old modules otherwise it won't work.

Yes, I did that before. When I try ifconfig ath0 down and ifconfig wifi0 down I get "ERROR while getting interface flags: No such device" Should I continue anyways?

I also get:

> ryan@ryan-ubuntu:~/Desktop/madwifi-0.9.4/scripts$ ./madwifi-unload.bash
FATAL: Module wlan is in use.

Edit: If you need me to I will reformat (for the zillionth time) and we can start from a blank slate.

---

