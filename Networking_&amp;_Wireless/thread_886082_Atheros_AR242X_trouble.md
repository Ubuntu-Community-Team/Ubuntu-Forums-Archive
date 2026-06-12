---
title: "Atheros AR242X trouble"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by david_boring on 2008-08-10
I just switched from Vista to Ubuntu about 4 weeks ago and my wireless card (Atheros AR242X) has been completely nonfunctional since. I've been working on this for a while now and have followed a lot of advice on this forum and others, but still no luck. I've tried updating madwifi and even attempted using the ndiswrapper.

I'm really not sure what to do anymore and any help is appreciated.

---

### Post by chili555 on 2008-08-10
Check here: [http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

---

### Post by david_boring on 2008-08-10
Thanks for the reply.

I've actually tried that before and it didn't work. I just attempted it again and everything seemed to work until the last line "sudo modprobe ath_pci" and the terminal doesn't return anything. I rebooted and still no wireless.

---

### Post by chili555 on 2008-08-10
When the terminal doesn't return anything, that means the command was accepted and there are no errors or warnings to report. Please do:```
sudo modprobe ath_pci
iwconfig
```Do you have an interface now, hopefully *ath0*? Now do:```
sudo iwconfig ath0 essid <your_essid>
sudo iwconfig ath0 key <any_encryption_here?>
sudo dhclient ath0
```Here is an interesting bit from the README:> First, run "modprobe ath_pci" or the equivalent using "insmod".  When
the driver is successfully loaded it creates two devices, named "wifi0"
and "ath0".  The output from iwconfig should look like this:

    lo      no wireless extensions.
    
    wifi0   no wireless extensions.
    
    ath0    IEEE 802.11b  ESSID:""
            Mode:Managed  Channel:0  Access Point: Not-Associated
	    Bit Rate:0 kb/s   Tx-Power:50 dBm   Sensitivity=0/3
	    Retry:off   RTS thr:off   Fragment thr:off
	    Power Management:off
	    Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
	    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
	    Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This driver uses wifi%d only as a placeholder for the physical device, 
and will create one wifi device for each wireless NIC in the system.  
These wifi devices will reject ifconfig and iwconfig commands.  The wifi
interface indicates the existence of a physical MadWifi device, but it
is not of any functional interest other than as the starting point for
VAP creation via wlanconfig (see Virtual AP section below).

By default, an ath%d Managed mode interface is also created.  This
device is a "virtual ap" (VAP) of the wifi%d physical device, and is
configurable by the standard networking tools  - ifconfig, iwconfig,
iwpriv. Let us know.

---

### Post by david_boring on 2008-08-11
Hmm, no errors, but still didn't seem to work. I'm using Wicd (one of my many attempts at a fix) if that matters. Also, my card is listed as DISABLED.

Below is the output from iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Also, I just remembered that in one of my fix-attempts, I blacklisted (/etc/modprobe.d/blacklist) ath_pci following some tutorial (probably to install ndiswrapper), but now I'm unable to *un*blacklist it, even though I'm the administrator on this computer. That's probably one of the problems, right?

---

### Post by chili555 on 2008-08-11
> That's probably one of the problems, right? It's certainly a prime suspect. Let's try to fix it.```
sudo su
```Were you asked for a password?```
gedit /etc/modprobe.d/blacklist
```Find and remove *ath_pci* and/or *ath-pci*. Proofread, save and close.> ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Looks like it's all ready to go, actually.> Hmm, no errors, but still didn't seem to work.What was the result of the dhclient command?

---

### Post by david_boring on 2008-08-11
Well, as I suspected, I'm an idiot and forgot one of the most obvious things: I was using wifi0 as my interface instead of ath0 in my Wicd preferences. I changed that, and it worked.

Thanks a lot for your help.

---

### Post by chili555 on 2008-08-11
We've all done it. Glad it's working.

---

### Post by xnaturalxloserx on 2008-08-15
Hello,

I'm new to Ubuntu and I just got a new laptop and installed Ubuntu on it and I LOVE it. The laptop is a HP Pavilion dv6000 with an Atheros AR242x wireless network card. Anyhow, I'm having a hard time getting any kind of wireless to work on Ubuntu. There's a wireless switch in the front of the laptop that is supposed to turn blue when it's turned on but with the switch in either position, it's never blue, just always red. I don't know if that's affected by the drivers or what, but like I said, I cannot get this wireless to work.

I'm still really new to Linux and all the commands, but if someone can make a list, step by step of how to get my wireless to work, I will pretty much, more or less, worship you.

Thank you so much,
Jason

---

### Post by Chibone on 2008-08-16
Did you check out the second post in this thread, click the link, then scroll down to post 4 and follow the directions?

---

### Post by uhappo on 2008-08-21
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```


sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/

make
sudo make install
sudo modprobe ath_pci
sudo reboot

```

WLAN working very beatifully, same as desktop effects!!!
WUHUU!!!

---

### Post by gabriel.pelmus on 2009-01-11
Hello,
I'm working for over 3 weeks now to get my wireless card going.Until now with no results. I think I followed every tutorial and forum on the Internet about Atheros wireless card on ubuntu.I have an Asus X51H notebook,KUbuntu 8.10 and I have a home wireless network with essid WLAN encrypted wpa2 with key: casutadinpadure. At this moment iwconfig shows me this:

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ifconfig shows me this:

ath0      Link encap:Ethernet  HWaddr 00:15:af:3f:38:8e  
          inet6 addr: fe80::215:afff:fe3f:388e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1d:60:50:e1:3f  
          inet addr:192.168.0.124  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe50:e13f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22365744 (22.3 MB)  TX bytes:1238178 (1.2 MB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3448 (3.4 KB)  TX bytes:3448 (3.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-3F-38-8E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:37678 (37.6 KB)
          Interrupt:17 
in hardware drivers I have :

Support for 5xxx series of Atheros 802.11 wireless LAN cards
Support for Atheros 802.11 wireless LAN cards
the last one is currently active and in use.I tried the first one but still couldn't get a connection or even find the network. When I scan for network I get the following:
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

pan0      Interface doesn't support scanning.

Another notebook running Vista can connect to the network.I hope someone knows what can I do to get this thing running.Thanks!

---

### Post by 9ine0h5ive on 2009-01-11
hmmm I had the same problem when I switched over to ubuntu but i found another solution [COLOR="Blue"][here]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/")[/COLOR]

---

### Post by gabriel.pelmus on 2009-01-11
This seamed to work after installing wicd.Thanks!Now I have 2 more problems:
1. when I try to connect to the wireless network(I made it unsecured), wicd gets stuck to obtaining IP
2. when I hit refresh button it says no wireless connections found, and I have to restart my computer in order for wicd to find my wireless network again
does anybody have any idea on how I could solve this?
I also noticed that wicd can't find wireless network if my network cable is unpluged.Help!

---

