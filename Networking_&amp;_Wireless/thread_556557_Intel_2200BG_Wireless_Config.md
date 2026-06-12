---
title: "Intel 2200BG Wireless Config"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by Neondog82 on 2007-09-21
Hello everyone. I am kind of new to Ubuntu. I had installed it on my laptop before but after an update the OS crashed so I quit using it. Well I am back and determined to make Ubuntu work this time. Currently my problem is getting the WiFi to work. I have read numerous threads on how to try and fix it but I am still coming up short. So I decided to post my own thread to see if personalized help would work out. Currently I am using a Sony VGN-FS550 with a Intel 2200BG wireless card. Also I am using Ubuntu 7.04. I can see all the wireless AP out there but I can not connect to them. I can not even connect to unsecured ones. So after some research I found that I needed to edit my /etc/network/interfaces file. After doing this it still fails to work. Most of the time when reading post on fixing it the things they say to do are not dumbed down enough for me since I am new at this. If anyone could help me I would much appreciate it. Below is my interfaces file.

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid Neondog82
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 6ca766a3cb04b2496f52526ec2***************************
```

I removed the last part of my WPA PSK but it was compiled via some command I forgot in the terminal window.

Thank you in advance,
Neondog82

---

### Post by HokeyFry on 2007-09-21
did you install ndiswrapper already? if you did what is the output of
```
ndiswrapper -l
```

if you didnt, dont install it thru the reops, install it from source, which the howto in my sig explains how to

---

### Post by Neondog82 on 2007-09-21
Thanks for the help. i tried to do what you said but got what you see below. Also will i need change my interfaces.inf back to the way it was?

```

neondog82@Linux:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up rsync (2.6.9-3ubuntu1.1) ...
dpkg: error processing rsync (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
Setting up network-manager (0.6.4-6ubuntu7) ...
dpkg: error processing network-manager (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (= 0.6.4-6ubuntu7); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rsync
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by noob12 on 2007-09-21
If you are using the regular edition of Ubuntu 7.04, then you have the ipw2200 driver for this card and you shouldn't need to install any other driver.  It should just work.

If you are using NetworkManager (NM) to manage the wireless, it will maintain keys (using gnome-keyring) automatically. Just comment out the lines for that device from /etc/network/interfaces entirely.  This puts it in "roaming" mode where it is managed by NM.

The first time that you connect to a network you will need to enter the key and store it in your keyring.

I've used the 2200 on a Fujitsu laptop, with NM, and WPA and it was reliable and stable for me.

---

### Post by Neondog82 on 2007-09-21
exactly how do you comment out what ever you are talking about? I tried to connect to my AP with NM and put in my WPA PSK and it does not work. I got it to connect to the AP once, but no internet. I can even get it to connect to some of the surrounding unsecure networks. I am pretty sure that i am using the ipw2200 driver.

---

### Post by noob12 on 2007-09-21
To comment out a line in **/etc/network/interfaces**, just start the line with a # sign.

Can you post the output of this:

```

lspci -nn

sudo lshw -C network

```

---

### Post by Buffalo Soldier on 2007-09-21
Intel 2200 wireless is fully supported out-of-the-box and yes, it truely just-work :) No need for ndiswrapper and all that stuff. And it works perfectly with the default installed Network-Manager. And both WPA and WEP encryption works fine too.

BUT, seeing that you've done some manual tweaking and changes to your config files... there are somethings that you need to do now.

If nm-applet not managing your network connections, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let Network Manager handle them.

```
sudo gedit /etc/network/interfaces
```

Example:> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp

---

### Post by Neondog82 on 2007-09-21
```


neondog82@Linux:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
06:03.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
06:03.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e]
06:03.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller [104c:ac8f]
06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
06:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 04)
neondog82@Linux:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@06:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:bf:b6:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:b0106000-b0106fff irq:22
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@06:08.0
       logical name: eth0
       version: 04
       serial: 00:01:4a:16:49:21
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.2.104 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:b0107000-b0107fff ioport:2000-203f irq:20
neondog82@Linux:~$ 

```

---

### Post by noob12 on 2007-09-21
Yep.   You have the 2200 and the ipw2200 driver is on it.

Comment out the section you have for it from /etc/network/interfaces and NM should handle it.  Also, you don't have an eth2, ath0, or wlan0 so you can just remove those as well.  They're just costing boot time determining the device isn't there.

Be sure to keep the lo (loopback) section around though.

---

### Post by Neondog82 on 2007-09-22
Below is what my /etc/netowrk/interfaces file looks like, and still no dice. Do i need to do anything special like kill NM and restart it? How come before NM use to show all the wireless AP's when I left clicked on it and now it just shows wired connection and manual config? I tried restarting the computer with the wired connection unplugged, and the restarted NM after logging in but it still does not work. Is my interfaces file setup right? Should I just do yet another clean install of 7.04 since I have messed with so much stuff trying to get it to work? Should I manually build NDSIwrapper like mentioned in the second post? People keep saying i don't need NDSI with the IPW2200 but it keeps getting brought up time after time. Please let me know what I can do.
```

# The loopback network interface

auto lo
iface lo inet loopback

# This is the wireless connection

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid Neondog82
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 6ca766a3cb04b249************************************************
```

---

### Post by noob12 on 2007-09-22
You need to comment out all the lines related to eth1 in order for NM to start managing it in conjunction with eth0.  After that will say "roaming mode" in the GUI for both the wired and wireless connecctions.  Note that if you use the GUI to do that you will lose the entries, so you may want to make a backup copy of your wireless information in case you go back to using a manual config.

So 

```

# Make a backup copy
cp /etc/network/interfaces /etc/network/interfaces.backup

# edit it
sudo gedit /etc/network/interfaces

```

Remove or comment out all of the entries, except that for loopback, so yours should look like this

```

# The loopback network interface

auto lo
iface lo inet loopback

# This is the manual config for the wireless connection
# When commented out like this, it will be managed by NetworkManager in
# roaming mode.
#auto eth1
#iface eth1 inet dhcp
#wpa-driver wext
#wpa-ssid Neondog82
#wpa-ap-scan 1
#wpa-proto WPA
#wpa-pairwise TKIP
#wpa-group TKIP
#wpa-key-mgmt WPA-PSK
#wpa-psk 6ca766a3cb04b249************************************************

```

---

### Post by Neondog82 on 2007-09-23
I managed to kind of fix it. I did a clean install since I had messed with so many things. After that it still was not working. So i went into my router and turned the encryption off, and it connected. Following that I turned on the WPA2 w/ AES and it connected on its own. I am not sure what the problem was, but obviously it did not like just plain old WPA, either that or changing things around in my router fixed the problem. Anyways I just wanted to thank you to everyone that helped me out.

Peace and hair grease,
Neondog82

P.S. I did not comment out my /etc/network/interfaces nor did I install ndiswrapper. I seems to have worked with just a clean install.

---

### Post by noob12 on 2007-09-23
Great.  Yeah on a fresh install you will have more benign entries in /etc/network/interfaces.  If you want full roaming functionality in NM, you will still need to remove or comment out those sections (or set the interface to roaming in the GUI, which will remove them).   

I'm not sure how ndiswrapper came up.  The 2200 is supported by the ipw2200 driver that ships with Ubuntu, which is what I stated before.

---

### Post by Neondog82 on 2007-09-23
What do you mean by full roaming capability? currently under NM i can select what ever wireless network I want to connect to? I did not manually config my current wireless connection to my AP.

---

### Post by michaelramm on 2007-09-27
I was having the same problem with my ThinkPad T43 with the Intel PRO 2200bg card. I mistakingly added the ndiswrapper because I have misread the Broadcom ethernet port. So I too reinstalled the system and it worked out of the box. I did not have to walk through the encryption like Neon did. I kept my WPA2 (AES) on the whole time and it worked (in fact I am typing this response on the wireless!).

Thanks for the help with this n00b and Neon. I was getting frustrated (be it from my own mistake) with trying to get it to work.

Michael

---

