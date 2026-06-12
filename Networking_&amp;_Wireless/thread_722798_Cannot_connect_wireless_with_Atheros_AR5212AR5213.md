---
title: "Cannot connect wireless with Atheros AR5212/AR5213"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by steinfal on 2008-03-12
I have a netgear router that is broadcasting on 192.168.1.1.  I know it is broadcasting correctly because I had a friend connect to it with a windows laptop.  However, my laptop cannot find the access router.  It found it with Ubuntu 7.04 and intermitently with 7.10.  After a fresh install, it will not find it at all.

O/S: Ubuntu 7.10 Gutsy Gibbon
Wireless Card: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01) (found with lspci commmand)
Computer: Laptop - Linux Certified LC2464
Router: Netgear 54Mbps Model WGR614 v7

Output of 	sudo iwlist scanning (before and after typing sudo ifconfig ath0 up and sudo ifconig wifi0 up.  I typed both because I am not sure which one to use.)

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results
```

Output of  iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

partial output of lshw 

	```
*-network:1
             description: Wireless interface
             product: AR5212/AR5213 Multiprotocol MAC/baseband processor
             vendor: Atheros Communications, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: wifi0
             version: 01
             serial: 00:90:4b:dc:0b:a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

output for sudo dhclient -r wifi0
```

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback

```

---

### Post by Paris Heng on 2008-03-13
Did you install the driver for your wireless NIC?

---

### Post by kevdog on 2008-03-13
Your using the madwifi driver.  One of the nuances about this driver, is that it has a physical interface for the device itself wifi0, and then has the ability to create multiple virtual interfaces. By default it creates on virtual interface known as ath0.  Commands intended for the device must go directly through a virtual interface and not the actual interface.  So hence after all this long discussion, 

sudo dhclient -r wifi0

must be 
sudo dhclient -r ath0

---

### Post by steinfal on 2008-03-14
Still not working.  Sorry, can't tell how to insert quotes on this so here we go...

Did I install a driver for the NIC?  No I thought it was supported.

I took the second suggestion and here is the output.

Output of  sudo dhclient -r ath0
```
[sudo]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:4b:dc:0b:a0
Sending on   LPF/ath0/00:90:4b:dc:0b:a0
Sending on   Socket/fallback
adam@adam-laptop:~$ sudo ifconfig ath0 down
adam@adam-laptop:~$ sudo ifconfig ath0 up
adam@adam-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results
```

---

### Post by kevdog on 2008-03-14
Confirm the driver is loaded:

lshw -C network

This will show you the driver associated with the device

lsmod | grep ath

This will show you if the ath_pci driver is currently loaded in the kernel

---

### Post by steinfal on 2008-03-14
I do not understand the implications of these responses, but here they are.  Your help is hugely appreciated.

Output of lshw -C network
```
l
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:32:21:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wifi0
       version: 01
       serial: 00:90:4b:dc:0b:a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

Output of  lsmod | grep ath
```

ath_rate_sample        15616  1 
ath_pci               105392  0 
wlan                  225736  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               219888  3 ath_rate_sample,ath_pci

```

---

### Post by kevdog on 2008-03-14
So bring down your wired interface

sudo ifconfig eth0 down

Up your wireless interface

sudo ifconfig ath0 up

Then do a iwlist scan

iwlist scan

Do you see any networks??

You can reverse the process to bring up the wired interface!

---

### Post by steinfal on 2008-03-15
I still don't think it is finding anything...

```

adam@adam-laptop:~$ sudo ifconfig eth0 down
[sudo] password for adam:

adam@adam-laptop:~$ sudo ifconfig ath0 up

adam@adam-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

```

---

### Post by kevdog on 2008-03-15
Just to cover the obvious, wireless networks are nearby??  No scan results means its not picking up anything?

Can you also check dmesg and post any relevant output for the madwifi drivers (not the entire file)?

---

### Post by steinfal on 2008-03-15
I know there is wireless nearby.  My wireless router is on and my friend with another laptop picked it up last week.  Also, I used to be able to see my neighbor's networks as well.

I don't see any mention of madwifi while using dmesg, however I have posted anything from that command that I think may be helpful.

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[  129.535306] ath_hal: module license 'Proprietary' taints kernel.
[  129.536803] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  129.705764] wlan: 0.8.4.2 (0.9.3.2)
[  129.747999] ath_pci: 0.9.4.5 (0.9.3.2)
[  130.519485] ath_rate_sample: 1.2 (0.9.3.2)
[  130.521473] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  130.521489] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  130.521498] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  130.521517] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  130.521530] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  130.521538] wifi0: mac 5.9 phy 4.3 radio 3.6
[  130.521547] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  130.521551] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  130.521556] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  130.521561] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  130.521565] wifi0: Use hw queue 8 for CAB traffic
[  130.521570] wifi0: Use hw queue 9 for beacons
[  130.547592] wifi0: Atheros 5212: mem=0xfebe0000, irq=19
[  179.456729] ath0: no IPv6 routers present
[  183.718283] powernow-k8: error - out of sync, fix 0x8 0x0, vid 0x2 0x12
```

---

### Post by steinfal on 2008-04-01
UPDATE ---

I took the computer in for service and the tech found that there was a button on the top of the computer that was switched off!  I would of never guessed!  Thanks for the help kevdog.

---

### Post by kcallis on 2008-04-20
> **steinfal said:**
> UPDATE ---

I took the computer in for service and the tech found that there was a button on the top of the computer that was switched off!  I would of never guessed!  Thanks for the help kevdog.
I wish the solution was just as simple. The problem that I having is that although there is some initial wireless connectivity, once any heavy traffic is passed through the interface, it hangs. For instance, if I do an "apt-get update", I can get 99% of update, then suddenly, it just hangs and times out on the repository.

Just for information, I am running a Toshiba M35X-S311 running under 7.10

---

