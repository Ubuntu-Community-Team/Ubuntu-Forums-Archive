---
title: "Atheros 5006x (AR5413) not working"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by DewBoy3d on 2008-05-02
After reading through every atheros thread I can find here, I still am not able to use my wireless card in linux. I'm hoping someone can help.

I am using latest madwifi but it appears that the ar5413 chipset is unsupported. from what i can tell it is the ONLY chipset in this family that is. I am relatively new to anything wireless in linux so any help/guidance/guesses would be appreciated.

Here is output of several commands.

deadvelocity@vistasucks:~$ lspci
```
02:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
```

deadvelocity@vistasucks:~$ dmesg | grep ath
```
[   42.863723] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   43.005616] ath_pci: 0.9.4
```

deadvelocity@vistasucks:~$ dmesg | grep wifi
```
[   43.006086] wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)
```

deadvelocity@vistasucks:~$ sudo lshw -C network
```
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
```

deadvelocity@vistasucks:~$ lsmod | grep ath
```
ath_pci               101024  0 
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci
```

---

### Post by tsoul on 2008-05-10
Same Problem here.. I have been waiting for this to get fixed for almost a year now.

Really hope someone can sort this out..

:(

---

### Post by eddie321 on 2008-08-20
Hey Everybody,

I got my atheros 5006x (5413) finally to work with Ubuntu 8.04. on a compaq presario c700 laptop.
I couldn't find any other threat where someone who got it to work so I'll post my solution up here. It's pretty simple and straightforward. I hope it'll work for you guys too!

The problem I had was;

with lshw -C network, the card was found, but it stated *UNAVAILABLE and at section configuration there was no driver installed.

In the desktop. there was a 'pop-up message' saying something about propetarian drivers. It did show the atheros card though.....

There was no wireless option in the network configuration screen.(only loopback and my cabled network card).



I tried a lot of stuff i found on this site but nothing worked. So I decided to start over.

1. clean install of Ubuntu.

2. install ndiswrapper 
(via synaptic package manager install the package ndisgtk (it'll be located on the ubuntu CD so set the source to this location)

3. install the windows driver
(after step 2 you'll have an extra option in system-administration-windows wireless network configuration) 

4. select the windows driver located in windows\system32\net5211.inf
(you will see inmediately that the hardware is located) after that, off you go!! You'll have wireless options in the network configuration screen.)

Note: I did try the windowsdriver from wildpackets.com the 4229 version. I'm not sure these work too. 

The net5211.inf file i used is from date 22-06-2007, size 91,0kb.


I'm just a week user of linux now so i don't know anything about it, i only knows it works finally!!!

good luck to you!

Eddie






[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns)

---

### Post by Nikopie on 2008-10-10
Hey... I'm having the same problems as you guys.  I've been using Linux for about 48 hrs now so I'm a real newbie.

   I don't have a 5211.inf file.  I do have a netathr.inf file, and when I put that in Windows Wireless Driver it is saying its not a valid driver...

any ideas?

Thanks,
-Nik

---

### Post by jheaton5 on 2008-10-11
We newbees need to stick together.  Here's a stupid question:  Is your wireless switch (the hardware one on the outside of the computer) turned on?

From the command results you posted a wireless card is not present.

By the way, I like your domain name and I agree.

---

### Post by Nikopie on 2008-10-11
jheaton5:

   Not a stupid question at all... My PC is a desktop, and there is no on/off switch for my Wireless.  I wish it was that easy!

-Nik

---

### Post by gulatiakshay on 2008-10-11
description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:e2:14:a3:83
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=136.159.91.20 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

Wireless is not working help help

---

### Post by jheaton5 on 2008-10-11
Using the menu bar, go to System>Administration>Hardware Drivers.  Do you see a wireless driver there?

---

### Post by jheaton5 on 2008-10-11
try here:  [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi")

---

### Post by Nikopie on 2008-10-11
When I access the Hardware Drivers it is there as the following:

Atheros Hardware Access Layer
SUpport for Atheros 802.11 wireless LAN cards.

Next to both of them the enable box is checked and the it says "not in use".

I've also tried the MadWifi stuff and thats not working.  MadWiFi isn't working.

Frustrating....:mad:

---

### Post by cyzhou on 2008-11-02
Hope this can help:

I am using ASUS laptop A8JR, the wifi card is Atheros 5006x. 
after a almost one week of experiments, I finally made it work on ubuntu 8.04 as well as 8.10. 

Actually, it is very simple. I just follow the instructions in the following link: [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download").

here is what I did for ubuntu 8.04:

(1)download: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

(2)commands: 
< tar jxvf compat-wireless-old.tar.bz2 > 
< cd compat-wireless-old > 
< make > # it takes some time
< sudo make install >
< sudo make unload >
< sudo modprobe ath5k > 

(3)reboot ubuntu

after installation, reboot is needed to activate wifi.

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another way to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by tsoul on 2008-11-03
> **cyzhou said:**
> Hope this can help:

I am using ASUS laptop A8JR, the wifi card is Atheros 5006x. 
after a almost one week of experiments, I finally made it work on ubuntu 8.04 as well as 8.10. 

Actually, it is very simple. I just follow the instructions in the following link: [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download").

here is what I did for ubuntu 8.04:

(1)download: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

(2)commands: 
< tar jxvf compat-wireless-old.tar.bz2 > 
< cd compat-wireless-old > 
< make > # it takes some time
< sudo make install >
< sudo make unload >
< sudo modprobe ath5k > 

(3)reboot ubuntu

after installation, reboot is needed to activate wifi.

**I did all above I managed to see my card in iwconfig but it dose not scan any network and the lights on my wireless card our not on. I have AR5413**

---

### Post by olskar on 2009-04-02
This worked in Jaunty for a while but then stopped after an update, I filed a bug here [https://bugs.launchpad.net/ubuntu/+bug/353341](https://bugs.launchpad.net/ubuntu/+bug/353341)

---

### Post by James Keating on 2009-05-13
I tried everything here and everywhere else. What finally worked was a new kernel module -- not the Windows driver and ndiswrapper. Using the module should be much easier.

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

Update: 

Since Karmic 9.10, I have had no problem.

In /etc/network/interfaces, these lines are necessary 
auto wlan0 
iface lo inet dhcp

and Ubuntu may now add those automatically. 

Everything else works with no tweaking.

---

### Post by salemboot on 2009-09-16
Try turning off the wireless router as well.

I noticed after updates I had problems keeping a connection.

Also check your proximity to the router.  If you are right on top of it you may have problems as well.  

I get this routinely with my new router.

Also if your home phone is a 2.4G variety this may cause problems.

---

