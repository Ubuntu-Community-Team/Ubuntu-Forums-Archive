---
title: "Trouble with AR5413 (Atheros) Card"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Deutscher Alex on 2008-10-01
I cannot get wireless internet to work on yet another computer.
" lshw -C network " gives me:
```

  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:18:f3:ad:1b:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-2 latency=0 module=e1000 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=96 maxlatency=28 mingnt=10

```

In the Network Configuration screen there is no Wireless option, only the wired connection and point to point.


I tried doing what DemonBob said [here]("http://ubuntuforums.org/showthread.php?t=896281&highlight=AR5413")

> **DemonBob said:**
> System -> Administration -> Hardware Driver

Make sure the Atheros driver is enabled. If not enable it, it should require a reboot.

If this does not work. The current driver in Hardy may not support the chip. You can update the driver, by following the steps below.  

Download both: 
[http://ubuntu.cs.utah.edu/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

Put them on a USB stick or CD, the copy them to the Ubuntu desktop

Goto a terminal. 

```

cd Desktop
sudo dpkg -i build-essential_11.3ubuntu1_i386.deb
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-current
sudo make
sudo make install

```

Then reboot.,
but that didn't seem to do anything.
I tried blacklisting ath_pci and ath_hal, as suggested [here]("http://ubuntuforums.org/showthread.php?t=603989"), but still nothing.

Also I was going to try using ndisgtk to install net5211.inf, suggested [here]("http://ubuntuforums.org/showthread.php?t=778726"), but there was no such file in the XP partition :(.


I tried downloading madwifi [here]("http://ubuntuforums.org/showthread.php?t=798485") using the "Installing without an Internet connection or using a source tarball (not fun)" method, but I get an error message saying there is no compatible hardware found. I tried about 10 different versions, all with the same outcome.

I've been working at this for about 4 hours straight now, and it's the second time HP has screwed me over with a wireless card :(

---

### Post by Deutscher Alex on 2008-10-01
sudo bump

Does anyone know where I could find madwifi-r1352-20051208?

---

### Post by jpete on 2008-10-01
You might try this thread.

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

Read it to the end, there is some important info at the end of it.

Don't know if it will apply to you, but it was suggested to me and it helped a bit.

---

### Post by Deutscher Alex on 2008-10-01
yes I had already tried all of that... (my initial post's last "here")
I went through it again and installed MadWifi v0.9.4
This didn't give me any sort of error, but it didn't change anything either.
What exactly am I supposed to do after running
```

sudo make
sudo make install

``` to install MadWifi?

I rebooted after installing, which didn't do anything.
I tried ```
sudo modprobe ath_pci
``` after rebooting, which also changed nothing.
lshw still says UNCLAIMED
```
*-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:18:f3:ad:1b:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-2 latency=0 module=e1000 multicast=yes
  [b]*-network UNCLAIMED
 [/b]      description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=96 maxlatency=28 mingnt=10
```
and there is still no wireless option under network configuration

---

### Post by Deutscher Alex on 2008-10-04
buMP
BUmp

---

### Post by jellylogix on 2009-02-21
I know this is going to sound kinda rude, but have you tried ndiswrapper?

---

### Post by Hirokazu Nasu on 2009-02-25
Hello, everyone.

I am a debian user, and I have been struggling for a couple of weeks to activate a wireless lan device of my new desktop PC (pavilion v7780jp) with AR5413 card. Finally I have found a solution. I have just upgraded the version of the kernel from 2.6.26 to 2.6.28. Then I see ath5k module (a standard module) works perfectly fine! The same module in the version 2.6.26 could be loaded successfully, but I had no scan results.

I hope this information would be a help to ubuntu users also.

---

### Post by James Keating on 2009-05-13
Thank you. After many days of searching and trying everything, your suggestion let me finally use my wireless connection.

Details:

I have a wireless router. Before I installed the wireless card, I set up the router with a wired connection and set the password to access the router. 

My wireless card is an NEC PA-WL54SC2. It uses the chipset AR5413, which needs the kernel module ath5k.

To get any such card working, you need: 

a) the kernel module ath5k 
b) the wlan0 interface 
c) wpa_supplicant 
d) a GUI front end, maybe


1: get kernel module

In Synaptic, install the package for linux-backports-modules-(kernel version)-generic


2. install wpa_supplicant

In Synaptic, install wpasupplicant


3. have the ath5k module included on boot

As root, open the file /etc/modules with gedit or another editor:
sudo gedit /etc/modules

and add one line reading:
ath5k


4. add wlan0 interface 

As root, open the file /etc/network/interfaces

and add two lines:
auto wlan0
iface wlan0 inet dhcp 

5. reboot 

Now the card should be recognized by the system, but you still have to tell it how to connect, and set the password.

6. generate an encrypted passphrase from your wireless router passphrase:

sudo wpa_passphrase yourroutername yourpassword

This will produce lines like 

network={
	ssid="yourroutername"
	#psk="yourpassword"
	psk=encrypted.password94sdf6ffhdghd61196b60sdf4d1b41196b60sdf4d1b4

and that last line is the password in encrypted form. Copy it and save it along with your plain password.

7. create and open a configuration file for wpa_supplicant

sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf

and enter the following lines, substituting your ssid (the name your router broadcasts itself as, which you have chosen on wired setup), password and encrypted password:

ctrl_interface=/var/run/wpa_supplicant
network={
	ssid="yourrouter"
	 scan_ssid=1
	 proto=WPA RSN
	 proto=WPA 
	 key_mgmt=WPA-PSK
	 pairwise=CCMP TKIP
	 group=CCMP TKIP
	#psk="yourpassword"
	psk=encrypted.password94sdf6ffhdghd61196b60sdf4d1b41196b60sdf4d1b4
}


8. start wpa_supplicant:

sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext

This uses the wext driver, which you should already have. The driver is not ath5k.
-i sets interface, -c sets configuration file, -D sets driver

If you are lucky, this will give you a connection. I was not lucky. I tried this command countless times, with and without various GUI front ends, with no effect. It finally worked after a suspend and resume; I don't know why.

Everything above may not be necessary on a normal Ubuntu setup. You may only have to install the kernel module, and the system will do the rest. I have an oddball cut-back system and did everything by hand.


Front ends:

A standard Ubuntu configuration shouldn't need any.
I tried, liked and kept rutilt 
I tried and rejected kwlan (too many windows and icons popping about) and wicd (run it with wicd-client -n)

I made two scripts to start and stop wpa_supplicant and insert and reject the wireless card, because the card wakes up my computer as soon as it is suspended:

#!/bin/sh
/sbin/pccardctl insert 0
/sbin/wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext  

#!/bin/sh
/usr/bin/killall wpa_supplicant 
/sbin/pccardctl eject 0 


..........
..........
various commands:

..........
Get device model and chipset of card:
lspci -nn

The relevant lines should look like

Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)
chipset number AR5413

..........
See if ath5k module has been loaded by system:
lsmod | grep ath5k

The output should look like:

ath5k                 116612  0 
lbm_cw_mac80211       215856  1 ath5k
lbm_cw_cfg80211        46744  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k

The 0, 1 and 2 refer to how many other modules depend on that one, and they are listed at the end. If the module is listed, it's loaded.	

..........
If the module is not listed, try to load it:

sudo depmod -a 
sudo modprobe ath5k

..........
Now check kernel messages to see if anything happened:
dmesg | grep -e ath5k

If it worked, the output will look like

[   41.317509] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
[   41.317693] ath5k 0000:02:00.0: registered as 'phy0'
[   41.984192] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa5, PHY: 0x61)

..........
Get general info on module: 

modinfo ath5k 

The output should look like

filename:       /lib/modules/2.6.28-11-generic/updates/ath5k.ko
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.

..........
See network status
(see if ath5k module is loaded, and no other driver is trying to claim wireless):

sudo lshw -C Network

  *-network
       description: AtermWL54SC2(PA-WL54SC2)
       product: 1.0
       vendor: NEC AccessTechnica, Ltd.
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:8b:69:8b:b8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg

If the module is already claimed, you may have to edit a blacklist file. There are posts elsewhere on this. There is also a good wireless troubleshooting how-to in Ubuntu's documentation section. It didn't solve my problem, but it did help me see where the problem lay.

..........
See if network is connected and running:

ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:1b:8b:69:8b:b8  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:8bff:fe69:8bb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:999 (999.0 B)  TX bytes:1157 (1.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-8B-69-8B-B8-62-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

..........
Get wireless network info:

iwconfig


##### 

update:

Since at least Karmic 9.10, wireless has been no problem with this chipset. 

In /etc/network/interfaces, I (or Ubuntu by now?) added the lines 
auto wlan0 
iface lo inet dhcp

On another machine, which has a wireless card that needs the b43 module, add a module line to /etc/modules
      b43
then with a wire connection installed the package b43-fwcutter

After that, I just pick my router from the list and give the password.

---

