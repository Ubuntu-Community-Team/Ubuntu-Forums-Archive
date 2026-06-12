---
title: "Please Help I Have tried to fix this myself for months!!"
date: 2015-06-26
forum: Networking &amp; Wireless
---

### Post by Matthew_Pacheco on 2015-06-26
Hi everyone I am new and have been trying to learn as much as I can with Google,Youtube,and trial and error. I have been able to figure most things out myself and i getting used to using the terminal and basic commands. One thing i haven't been able to figure out is my WiFi issue. I have a Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter. It does not show me any available networks no matter what i try. I have bought another wireless adapter but i want to still try to fix this if possible. Thank you in advance.

---

### Post by Bucky Ball on 2015-06-26
Welcome. Okee doke. Let's have a look and see what driver and other things you have happening for that card already. Unplug the wireless USB dongle, reboot, open a terminal at the desktop and:

```
sudo lshw -C network
```

Post the output of that here, please.

Which release number are you using (14.04, 15.04, etc.) and what is the make/model of your machine? Is it VERY new?

---

### Post by Matthew_Pacheco on 2015-06-26
The output of command sudo lshw -C network
 [FONT=monospace][/FONT]
```


 [FONT=monospace][COLOR=#000000]~$ sudo lshw -C network [/COLOR]
[sudo] password for kubuntu15:  
  *-network                
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 06 
       serial: d0:27:88:4e:15:a4 
       size: 1Gbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet 
physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverver
sion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.42.0.97 late
ncy=0 link=yes multicast=yes port=MII speed=1Gbit/s 
       resources: irq:24 ioport:e800(size=256) memory:fafff000-faffffff memor
y:faff8000-faffbfff 
  *-network 
       description: Wireless interface 
       physical id: 1 
       bus info: usb@2:1.6 
       logical name: wlan0 
       serial: 1c:65:9d:64:0c:20 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unas
sociated

[/FONT]

```   
I have a Gateway model ZX4951 all in one desktop. Its not new i think i got it in 2011.

---

### Post by Bucky Ball on 2015-06-26
With the USB dongle out, please, as requested. Pull the dongle, reboot, run the command. Thanks.

```
description: Wireless interface
physical id: 1
bus info: **usb**@2:1.6
```

 Copy/paste the output of the command I gave to a text file and then get online with the USB dongle to post the info if you like. 

Terminal output between code tags, please. (See last link in signature below.) ;)

* Update, just read your first post again. Ah, my mistake. Ok, you are trying for to get another dongle going. Will think. :-k

What you could do in the meantime is get the SSID or your router/access point and its IP address, click the Network icon, edit the wireless entry and add the correct details manually. Even though you appear to have the wrong driver installed:

driver=r8712u

... you never know. Again, is this wireless device VERY new? Did you 'Try Ubuntu' prior to installing and did it work then? Have you tried any other releases, i.e. 14.04 LTS? 

Please answer. Thanks.

* Just had another thought. Are you pulling the WORKING wireless dongle and rebooting with the other one plugged in and not just swapping them over in a running boot? Perhaps the wrong driver for the not working dongle is the right driver for the working one (and the non-working driver is trying to use it). Start fresh from a boot with the faulty one in so there is no confusion, thanks. Switch the machine off completely and do a full cold boot with the non-working dongle in, then run that command again. ;)

---

### Post by Matthew_Pacheco on 2015-06-26
I'm kind of confused. I do have another wireless adapter but it is not plugged in at this time. I'm using an ethernet cable to connect to the internet. The realtek adaptor is built in. My desktop is a all in one.

---

### Post by Bucky Ball on 2015-06-26
Ok, so you want to get the internal wireless happening. Sorry. Probably me that's confused! Trying to do too many things at my end again. :)

If it is the internal wireless, yes, switch the machine off, unplug cable and USB dongle (are you trying to get online with the cable in?), boot up and run that command again, with no cable and no wireless USB dongle plugged in, thanks. 

```
sudo lshw -C network
```

Let's see what we get. Copy the output then plug the cable in to post if you need.

---

### Post by Matthew_Pacheco on 2015-06-26
The output of command [FONT=monospace][COLOR=#000000]sudo lshw -C network [/COLOR][/FONT]
```
 [FONT=monospace][COLOR=#000000]kubuntu15@Gateway:~$ sudo lshw -C network                                    [/COLOR]
[sudo] password for kubuntu15:  
  *-network                
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 06 
       serial: d0:27:88:4e:15:a4 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet 
physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverver
sion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no 
multicast=yes port=MII speed=10Mbit/s 
       resources: irq:24 ioport:e800(size=256) memory:fafff000-faffffff memor
y:faff8000-faffbfff 
  *-network 
       description: Wireless interface 
       physical id: 1 
       bus info: usb@2:1.6 
       logical name: wlan0 
       serial: 1c:65:9d:64:0c:20 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unas
sociated

[/FONT]
   
```
Did what you said. i turned off off the computer and unplugged it. Rebooted without the ethernet or the other wireless adaptor and ran the command.

---

### Post by Bucky Ball on 2015-06-26
Well, that is really strange, as it is showing the wireless bus as if USB dongle is still plugged in, unless I'm mistaken:

 ```
*-network 
       description: Wireless interface 
       physical id: 1 
     **  bus info: usb@2:1.6 **
       logical name: wlan0 
       serial: 1c:65:9d:64:0c:20 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes **driver=r8712u** multicast=yes wireless=unassociated
```

See the line in bold. :-k

Bit stumped about that. The driver it is loading is also not for the internal card (also in bold above).

---

### Post by Matthew_Pacheco on 2015-06-26
Is there anything else i can try?

---

### Post by wildmanne39 on 2015-06-26
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Matthew_Pacheco on 2015-06-27
Sorry i took so long let me try this and ill repost.

---

### Post by Matthew_Pacheco on 2015-06-27
I was using the ralink wireless adapter when i ran this. should i redo it with out it?
```

########## wireless info START ##########

Report from: 27 Jun 2015 03:10 PDT -0700

Booted last: 27 Jun 2015 03:06 PDT -0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

KDE Plasma Workspace

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Acer Incorporated [ALI] Device [1025:8000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 007: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 006: ID 04ca:0058 Lite-On Technology Corp. 
Bus 002 Device 005: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 004: ID 1cb6:6650 IdeaCom Technology Inc. 
Bus 002 Device 003: ID 04f2:b1f3 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              27189  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              652777  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              494362  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
r8712u                184139  0 
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:10.255.241.245  Bcast:10.255.243.255  Mask:255.255.252.0
          inet6 addr: fe80::2c0:caff:fe87:e6ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4510431 (4.5 MB)  TX bytes:352639 (352.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bgn  ESSID:"Economy Inn Salinas"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'Economy Inn Salinas' [AC1]>   
          Bit Rate=52 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:19  Invalid misc:187   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.255.240.1    0.0.0.0         UG    0      0        0 wlan1
10.255.240.0    0.0.0.0         255.255.252.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       881     1  0 03:06 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: wlan1  [Economy Inn Salinas] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    XFBSECA7HE6H:    Infra, <MAC 'budgetinn' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA2 Enterprise
    eiwan:           Infra, <MAC 'XFBSECA7HE6H' [AC12]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 69 WPA2
    eiwan:           Infra, <MAC 'Economy Inn Salinas' [AC10]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 55 WPA2
    budgetinn:       Infra, <MAC 'xfinitywifi' [AC15]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 55 WPA2
    ATT352:          Infra, <MAC 'ATT352' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    HRC2:            Infra, <MAC 'ATT352' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    BLACKTHORNE POOLS: Infra, <MAC 'BPT' [AC22]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    cloudtrax-secure:Infra, <MAC 'BLACKTHORNE POOLS' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    aawan:           Infra, <MAC 'BPT' [AC25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    xfinitywifi:     Infra, <MAC '' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 99
    CableWiFi:       Infra, <MAC 'xfinitywifi' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 65
    Economy Inn Salinas: Infra, <MAC 'Economy Inn Salinas' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 59 WPA2
    Economy Inn Salinas: Infra, <MAC 'eiwan' [AC11]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 61 WPA2
    eiwan:           Infra, <MAC 'eiwan' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 92 WPA2
    XFBSECA7HE6H:    Infra, <MAC 'eiwan' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA2 Enterprise
    XFBSECA7HE6H:    Infra, <MAC 'XFBSECA7HE6H' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    BPT:             Infra, <MAC '' [AC20]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BPT:             Infra, <MAC '' [AC23]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BPT:             Infra, <MAC 'xfinitywifi' [AC26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    budgetinn:       Infra, <MAC 'budgetinn' [AC14]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 39 WPA2
    ATT688:          Infra, <MAC 'budgetinn' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    budgetinn:       Infra, <MAC '' [AC18]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 35 WPA2
    ATT920:          Infra, <MAC 'budgetinn' [AN23]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Mr JOE LOPEZ:    Infra, <MAC 'ATT920' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    CableWiFi:       Infra, <MAC 'CableWiFi' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95
    xfinitywifi:     Infra, <MAC 'CableWiFi' [AN26]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52
    *Economy Inn Salinas: Infra, <MAC 'Economy Inn Salinas' [AC1]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 75 WPA2
    BPT:             Infra, <MAC 'Economy Inn Salinas' [AN28]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    HOME-EE62:       Infra, <MAC 'BPT' [AN29]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    cloudtrax-secure:Infra, <MAC 'HOME-EE62' [AN30]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BayPM:           Infra, <MAC 'cloudtrax-secure:Infra, <MAC address>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2' [AN31]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Howard Johnson - Salinas CA: Infra, <MAC 'BayPM' [AN32]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    CableWiFi:       Infra, <MAC 'Howard Johnson - Salinas CA' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45
    ATT224:          Infra, <MAC 'CableWiFi' [AN34]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         10.255.241.245
    Prefix:          22 (255.255.252.0)
    Gateway:         10.255.240.1

    DNS:             10.255.240.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless | permissions=user:matthew:;
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Economy Inn Salinas]] (600 root)
[connection] id=Economy Inn Salinas | type=802-11-wireless
[802-11-wireless] ssid=Economy Inn Salinas | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/eiwan]] (600 root)
[connection] id=eiwan | type=802-11-wireless | permissions=user:matthew:;
[802-11-wireless] ssid=eiwan | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless | permissions=user:matthew:;
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.432 GHz (Channel 5)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      13   APs on   Frequency:2.432 GHz (Channel 5)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     No scan results

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'Economy Inn Salinas' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Economy Inn Salinas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000005d65d21
                    Extra: Last beacon: 108ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e487f4980
                    Extra: Last beacon: 292ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'eiwan' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"eiwan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000005f2a980
                    Extra: Last beacon: 188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Economy Inn Salinas' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Economy Inn Salinas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005de71180
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dbfdb47180
                    Extra: Last beacon: 3312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ATT352' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ATT352"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000041f460dd35c
                    Extra: Last beacon: 3284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'CableWiFi' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"CableWiFi"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dbdc9589f3
                    Extra: Last beacon: 276ms ago
          Cell 08 - Address: <MAC 'eiwan' [AC9]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000005150f388
                    Extra: Last beacon: 132ms ago
          Cell 09 - Address: <MAC 'Economy Inn Salinas' [AC10]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"eiwan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005de7d980
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'eiwan' [AC11]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Economy Inn Salinas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000051464236
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'XFBSECA7HE6H' [AC12]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"eiwan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000512a04a7
                    Extra: Last beacon: 232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'budgetinn' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"XFBSECA7HE6H"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dbdc8cf3b9
                    Extra: Last beacon: 840ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'budgetinn' [AC14]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"budgetinn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e4881a17f
                    Extra: Last beacon: 116ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'xfinitywifi' [AC15]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"budgetinn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e487e8180
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dbdc96e25a
                    Extra: Last beacon: 188ms ago
          Cell 16 - Address: <MAC 'budgetinn' [AC17]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e487f4980
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC '' [AC18]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"budgetinn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000051270753
                    Extra: Last beacon: 948ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'BPT' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dbdc97e180
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC '' [AC20]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BPT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    ESSID:""
                    ESSID:""
                    Mode:Master
                    Extra:tsf=000000014ca5c984
                    Extra: Last beacon: 2680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'BLACKTHORNE POOLS' [AC21]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000051295980
                    Extra: Last beacon: 820ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'BPT' [AC22]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BLACKTHORNE POOLS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000091558c99c1c
                    Extra: Last beacon: 1684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC '' [AC23]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"BPT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000040fed308a
                    Extra: Last beacon: 372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'aawan' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ce48f6f180
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'BPT' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"aawan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000078e50e77b45
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'xfinitywifi' [AC26]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"BPT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001754d7cff
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s
                    Bit Rates:36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001ce48f6f180
                    Extra: Last beacon: 48ms ago

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AA4336C224E35E523F23134
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     21417B97E30FD4E6E469E1F
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     EDDCA794C9E4C3981037918
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     71EFA3CA86D02D0528C49EE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8712u]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     9A0BDB5A266844AB0999460
depends:        
staging:        Y
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   14.804389] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   14.832658] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[   18.069567] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   18.076521] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   18.398720] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.116558] r8712u 2-1.6:1.0 wlan0: 1 RCR=0x153f00e
[   19.117308] r8712u 2-1.6:1.0 wlan0: 2 RCR=0x553f00e
[   19.224408] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   21.284508] wlan1: authenticate with <MAC 'eiwan' [AC11]>
[   21.325366] wlan1: direct probe to <MAC 'eiwan' [AC11]> (try 1/3)
[   21.525618] wlan1: direct probe to <MAC 'eiwan' [AC11]> (try 2/3)
[   21.729708] wlan1: send auth to <MAC 'eiwan' [AC11]> (try 3/3)
[   21.731682] wlan1: authenticated
[   21.733751] wlan1: associate with <MAC 'eiwan' [AC11]> (try 1/3)
[   21.738738] wlan1: RX AssocResp from <MAC 'eiwan' [AC11]> (capab=0x411 status=0 aid=1)
[   21.746192] wlan1: associated
[   21.746234] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   46.559383] wlan1: authenticate with <MAC 'Economy Inn Salinas' [AC1]>
[   46.591939] wlan1: send auth to <MAC 'Economy Inn Salinas' [AC1]> (try 1/3)
[   46.595112] wlan1: authenticated
[   46.598378] wlan1: associate with <MAC 'Economy Inn Salinas' [AC1]> (try 1/3)
[   46.604159] wlan1: RX AssocResp from <MAC 'Economy Inn Salinas' [AC1]> (capab=0x411 status=0 aid=3)
[   46.616264] wlan1: associated

########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-06-27
Please run the wireless script again without the usb adaptor plugged in, since you already have the script on your computer just run it with the following command.
```
./wireless-info
```
Thanks

---

### Post by Matthew_Pacheco on 2015-06-27
Here you go. If i did something wrong let me know.
```

########## wireless info START ##########

Report from: 27 Jun 2015 14:14 PDT -0700

Booted last: 27 Jun 2015 14:09 PDT -0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

KDE Plasma Workspace

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Acer Incorporated [ALI] Device [1025:8000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 005: ID 04ca:0058 Lite-On Technology Corp. 
Bus 002 Device 004: ID 1cb6:6650 IdeaCom Technology Inc. 
Bus 002 Device 003: ID 04f2:b1f3 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              494362  0 
r8712u                184139  0 
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       872     1  0 14:09 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless | permissions=user:matthew:;
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Economy Inn Salinas]] (600 root)
[connection] id=Economy Inn Salinas | type=802-11-wireless
[802-11-wireless] ssid=Economy Inn Salinas | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/eiwan]] (600 root)
[connection] id=eiwan | type=802-11-wireless | permissions=user:matthew:;
[802-11-wireless] ssid=eiwan | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless | permissions=user:matthew:;
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8712u]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     9A0BDB5A266844AB0999460
depends:        
staging:        Y
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   13.036375] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   13.036977] r8712u: Staging version
[   13.036994] r8712u: register rtl8712_netdev_ops to netdev_ops
[   13.036998] usb 2-1.6: r8712u: USB_SPEED_HIGH with 4 endpoints
[   13.037452] usb 2-1.6: r8712u: Boot from EFUSE: Autoload OK
[   13.639352] usb 2-1.6: r8712u: CustomerID = 0x0000
[   13.639360] usb 2-1.6: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[   13.639365] usb 2-1.6: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   18.248352] r8712u 2-1.6:1.0 wlan0: 1 RCR=0x153f00e
[   18.249065] r8712u 2-1.6:1.0 wlan0: 2 RCR=0x553f00e
[   18.356207] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############



```

---

### Post by tgalati4 on 2015-06-28
Well, we have learned a few things:

1.  Your wireless card is connected to the USB bus, which is unusual, normally it is on the PCI bus, but that shouldn't matter.
2.  You are running a driver that is Beta quality--

> r8712u: module is from the staging directory, the quality is unknown, **you have been warned**.

These are the switches that you can fiddle with:

```
modinfo r8712u
```

Although they are in the same chipset family, they are not the same chip.  You have a RTL8191SU and my guess is that the wrong driver got selected.  So you can try a few things:

```
sudo modprobe -r r8712u
sudo modprobe -i something_else
```

That something_else would be a different driver from:

[https://wiki.debian.org/rtl819x](https://wiki.debian.org/rtl819x)

Your specific chip is not listed, so you will have to try several to see if something works.

I think the closest would be:

```
modinfo r8192u_usb
sudo modprobe -i r8192u_usb
```

If it works, great, if not, then you have more fiddling to do.

---

### Post by stanleyp2 on 2015-06-29
longshot:

logon to router -> connected devices -> delete your machine > reboot router and linux
possible old "hard arp" port forwarding issue

---

### Post by wildmanne39 on 2015-06-29
That is the right driver for his device but I believe the driver is just broken, it is going to be replaced with a new driver found here:
[https://github.com/chunkeey/rtl8192su](https://github.com/chunkeey/rtl8192su)
it requires that latest kernel, if you want to try it we can get the details wrote up to install the new kernel and then the new driver but this is highly experimental.
Thanks

---

### Post by Matthew_Pacheco on 2015-06-30
Yea ill try it. Thanks

---

### Post by Matthew_Pacheco on 2015-07-02
Having no luck install the driver

---

### Post by slooksterpsv on 2015-07-02
Why not compile the drivers from here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=229&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=229&DownTypeID=3&GetDown=false&Downloads=true)

Otherwise you could try ndiswrapper and use the Windows driver.

---

### Post by Bucky Ball on 2015-07-03
> **slooksterpsv said:**
> 

Otherwise you could try ndiswrapper and use the Windows driver.

No. Avoid ndiswrapper at all costs. Largely superseded and not needed for this card and should be considered an absolute last resort.

@Matthew_Pacheco: Having no luck installing the driver? You don't give us any detail about what with so can't give much help.

Download the driver, open a terminal, navigate to the folder you have downloaded it to (for example 'cd /home/Matthew_Pacheco/Downloads).

Now:

```
make
make load
```

Post any and all errors and details of anything you don't understand. Good luck.

---

### Post by Matthew_Pacheco on 2015-07-04
command output=        [FONT=monospace][COLOR=#000000]root@KnowledgeisPower:/home/matthew/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_[/COLOR]
8191_8192SU_usb_linux_v2.6.6.0.20120405# make 

[/FONT]
   
```
        [FONT=monospace][COLOR=#000000]cc1: some warnings being treated as errors [/COLOR]
scripts/Makefile.build:257: recipe for target '/home/matthew/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.2012
0405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o' failed 
make[2]: *** [/home/matthew/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_819
2SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.o] Error 1 
Makefile:1394: recipe for target '_module_/home/matthew/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/
driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405' failed 
make[1]: *** [_module_/home/matthew/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_
8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2 
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-21-generic' 
Makefile:220: recipe for target 'modules' failed 
make: *** [modules] Error 2 
root@KnowledgeisPower:/home/matthew/Downloads/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_
8191_8192SU_usb_linux_v2.6.6.0.20120405# 

[/FONT]
   
```

---

### Post by tgalati4 on 2015-07-04
Was there a .configure file in that directory?  If so, then you need to configure your build environment first, them make:

```
./.configure
make clean
make all
sudo make install

```

---

