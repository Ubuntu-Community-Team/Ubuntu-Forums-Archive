---
title: "install dlink n150 dwa 123 wifi adapter"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by nash2 on 2013-09-07
how to instakk dlink n150 dwa 123 wifi adapter on ubuntu 12.04

---

### Post by scbingham on 2013-09-08
What have you tried to get it to work?
Have you searched the forums for solutions?

It's difficult for people to try & help you unless you describe what you have tried & what results you have had so far.

---

### Post by nash2 on 2013-09-08
I am new to ubuntu so dont know much abt it , did some search on forums n google but couldnt come to any result. some help will be really appreciated.

---

### Post by scbingham on 2013-09-09
[COLOR=#000000]You're still not giving anyone any info to help you out.

I copied this from one of Wild Man's (a forum moderator) posts. Hopefully this will provide something to go on:-


Hi, copy and paste this command in the terminal (ctrl+alt+t) please:[/COLOR]
[COLOR=#000000]Code:
 
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script[/COLOR]
[COLOR=#000000]
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. [/COLOR]

[COLOR=#000000]If you do not have ethernet either then follow the directions at this link for running the script without internet.[/COLOR]
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by Bucky Ball on 2013-09-09
Welcome.

Open a terminal and run these two commands one at a time:
```

sudo lshw -C network
iwconfig

```

If USB, plug in and run these two:

```
lsusb
iwconfig
```

Post the results here. Thanks. If that doesn't give clues then perhaps time to move on to Wild Man's rather more involved procedure (although no harm posting that now also if you want). ;)

---

### Post by nash2 on 2013-09-12
> **Bucky Ball said:**
> Welcome.

Open a terminal and run these two commands one at a time:
```

sudo lshw -C network
iwconfig

```

If USB, plug in and run these two:

```
lsusb
iwconfig
```

Post the results here. Thanks. If that doesn't give clues then perhaps time to move on to Wild Man's rather more involved procedure (although no harm posting that now also if you want). ;)

**Result of sudo lshw -C network**

 *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: 00:23:24:1d:bb:9b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.3-1 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:1100(size=32)

**Result of iwconfig**

lo        no wireless extensions.

eth1      no wireless extensions.
[B]With usb plugged in
Result of lsusb[/B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:0324 Hewlett-Packard SK-2885 keyboard
Bus 007 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 026: ID 2001:3c1d D-Link Corp.

**Result of iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on




what should be done here.

---

### Post by Bucky Ball on 2013-09-12
Could you run this one again with it plugged in please, if you haven't already:

```
sudo lshw -C network
```

Definitely recognised without issue. From the output of 'lsusb':

```
Bus 001 Device 026: ID 2001:3c1d D-Link Corp
```

These generally work 'out of the box' so should be fixable without too much hacking. D-Link tend to do a lot of revisions, though, so this can sometimes be problematic.

PS: With it plugged in, when you left click on the network icon, do you see any available networks and is yours listed? I am a bit in and out at the moment so forgive me if it takes awhile to get back to you. Hopefully someone else we see this and jump in. Feel free to bump the thread after 24 hours if not. ;)

---

### Post by nash2 on 2013-09-12
Result of  sudo lshw -C network with usb plugged in
*-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: 00:23:24:1d:bb:9b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.3-1 ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f0180000-f019ffff memory:f01a5000-f01a5fff ioport:1100(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 78:54:2e:23:a6:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-53-generic-pae firmware=0.29 ip=10.42.0.1 link=yes multicast=yes wireless=IEEE 802.11bgn

when i click on the network tab there is only wired connection of by broadband showing, wireless is enabled n whwn i create a wireless network it shows a wireless network created but it is not found on any other device like my phone when i search for it.

---

### Post by Bucky Ball on 2013-09-12
No, you don't create a wireless network (actually, you can't without the correct hardware in the machine and a good degree of knowhow), but you can and want to create a network connection from your client machine to the network (provided by your wireless router/access point or AP). 

Unplug the cable, delete whatever it is you've created (presumably in Network Manager), plug the dongle in, restart the computer, click on the network icon. Anything? 

The wireless dongle is there, recognised, has a driver loaded and should be good to go, just needs a little tweaking. 

```
description: Wireless interface
physical id: 1
bus info: usb@1:4
logical name: wlan0
serial: 78:54:2e:23:a6:b5
capabilities: ethernet physical wireless
configuration: **broadcast=yes driver=rt2800usb driverversion=3.2.0-53-generic-pae firmware=0.29 ip=10.42.0.1 link=yes multicast=yes wireless=IEEE 802.11bgn**
```

The part in bold shows all is good. That driver is part of the kernel. But then, it might not be the one for your card as, as mentioned, D-Link tend to do a lot of revisions. This from iwconfig:

```
wlan0 IEEE 802.11bgn ESSID: Off/any
``` 

... lets us know your card is up (as wlan0) but is not associated with your, or any, access point. The ESSID should read 'ESSID: your_access_point/router' where 'your_access_point/router' is the actual name of your network. If you don't know what that is, you should find out now or you don't know what you're looking for.

Now, you don't create a network, you look for an existing one (which is on your wireless router/access point). What is the wireless router/AP you have connected to the internet? You need to connect to that 'gateway' to connect to the internet. You need some details and you can get them, with the cable plugged in to your router, by opening a web browser and entering the IP address of the router in the address bar. If you don't know it, find it in the manual or try:

192.168.0.1 (sometimes .2 or .0, experiment)

Firstly, make sure the router is set up as a DHCP server and is serving IP addresses. Once in, get the details of your network and then open Network Manager and create a connection under 'Wireless' tab. You need to have the correct security type setup (WPA, WEP, whatever the router is using) and the security key (sometimes written on the underside of the router/AP) for starters. 

Also in Network Manager, when editing the wireless connection, make sure you have 'Available to all users' and 'Connect Automatically' ticked.

Try this and see how it all goes. You should be getting offered to connect to your network or at least be seeing a range of available networks when you click on the network icon, though, so a little unclear as to what the problem is at this point. Keep digging. Can't be far away. :-k

*Note: notice your card is IEEE 802.11bgn. The 'n' part can sometimes be problematic and switching off wirelss N capabilities can sometimes fix. The AP might not have N capabilities and, for some reason, this can cause issues rather than the card simply falling back to g speeds.

---

### Post by varunendra on 2013-09-13
nash2,

Please always use 'Code' box to post commands/outputs in, so that the formatting is preserved and it doesn't change into those funny smileys :P
To see how to use it, please follow the "Using Code Tags" link in my signature.

Onto your problem -

Apart from following what BB suggested above, please follow the "Wireless Script" link in my signature, follow the instructions to run it and post back the report it generates. It is the same thing that scbingham linked to in post #4 above, and would have helped us a lot to understand the technical details of your problem.

**PS:**
Oh, the info you already posted is valuable too. So please edit your previous posts to wrap the outputs in 'Code' tags as well. Should be fun :)

---

