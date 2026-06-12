---
title: "wmaster0 ate my hamster, i mean wifi"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by fisheep on 2008-05-04
Hi all, I wonder if any of you kind folks will know what's gone wrong here.  Since upgrading to Kubuntu Hardy Heron (via the upgrader from the previous release), I've found myself hungering for the wifi freedom that Gutsy provided so unquestioningly.  That is to say, it has stopped working since the upgrade.  KNetworkManager stops on "Activation stage: Configuring device."  It sits like that for a while before throwing up its hands and asking me to enter my network settings- KNetworkManager's little way of saying "well that didn't work."

I decided to look on these hallowed forums for help.  And I did (ooh).  And there was (hooray!).  But it didn't (drat).  I refer to this:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

So I started from the beginning and lshw -C reported this:

```

  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:be:b4:ea
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 ip=192.168.0.5 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:82:30:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

"Wmaster0?  This is new," I thought to myself.  "The wireless network card always used to appear as eth1.  And interestingly it used to work.  Okay, it's called wmaster0 now."  So I followed the instructions (for WEP), and got as far as this:

```

alex@pineapple:~$ sudo ifconfig wmaster0 down
alex@pineapple:~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
alex@pineapple:~$ sudo ifconfig wmaster0 up
alex@pineapple:~$ sudo iwconfig wmaster0 essid "my ssid"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.

```

Not good, I like being able to connect to my AP.  I know, I'll try with good old eth1.  This was beguilingly encouraging, I got as far as
```

alex@pineapple:~$ sudo ifconfig eth1 down
alex@pineapple:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1c:bf:82:30:08
Sending on   LPF/eth1/00:1c:bf:82:30:08
Sending on   Socket/fallback
alex@pineapple:~$ sudo ifconfig eth1 up
alex@pineapple:~$ sudo iwconfig eth1 essid "33BalmwellGrove"
alex@pineapple:~$ sudo iwconfig eth1 mode Managed
alex@pineapple:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1c:bf:82:30:08
Sending on   LPF/eth1/00:1c:bf:82:30:08
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Have any of you got any clues as to what I'm doing wrong?  I'm hoping it'll be as simple as "force a reinstall of package X" :)  Please let me know if I can post any handy logfiles or whatnot.

My machine is a Lenovo ThinkPad x60t, if that's relevant.  And it was perfectly happy in Gutsy.

Thanks for any help!

Alex

---

### Post by WkenCouser on 2008-05-04
Hello,
I have exactly the same issues and I do not see my wireless card under System/Administration/Hardware devices.
:confused:

---

### Post by andreselsuave on 2008-05-04
Hi, I have the same problem, the GUI network manager sometimes works but sometimes don't... so I want to install network via command line and i also have the wmaster0 name... and i get the same errors as you. By the way, i'm using ubuntu Hardy Heron in a HP Compaq 8710p laptop.
```
root@portatilnuevo:/home/andreselsuave# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:82:16:18
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: [COLOR="Red"]wmaster0[/COLOR]
       version: 61
       serial: 00:13:e8:f6:e0:dd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.36 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

root@portatilnuevo:/home/andreselsuave# iwconfig wmaster0 essid "WLAN_34"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.

```

Thanks for your help in advance!

---

### Post by tr333 on 2008-05-08
FYI, the wmaster0 interface is created by the new mac80211 driver.

More information about this is available at [http://linuxwireless.org/en/developers/Documentation/mac80211](http://linuxwireless.org/en/developers/Documentation/mac80211).  I suggest viewing that website for more information about the state of wireless development in the linux kernel.

---

### Post by chili555 on 2008-05-08
Let me just say this. I have a perfectly working 3945ABG that I am replying on right now. I have a wmaster0. Ignore it. It does nothing to help or hurt you. Only you can decide to worry about it, or not. So don't.

You have a variety of issues.

@andreselsuave- Why is your interface DISABLED? Please do:```
sudo cat /var/log/messages | grep Kill
```Does it report the kill switch is on? Flip that switch or key combination and let's get wireless going.

@fisheep- Network Manager, which is installed by default, will not activate wireless as long as you have a working connection by wire, which you do:```
ip=192.168.0.5
```Until you detach the wire and restart networking:```
sudo /etc/init.d/networking restart
```then NM will try to help you get your wireless connected. You should be able to run:```
iwconfig
```and see that your wireless interface is really either wlan0 or eth1.

---

