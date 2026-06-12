---
title: "kubuntu wireless networking problems, KNetworkManager hangs at 28%"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by thisissean on 2007-06-09
I'm using Kubuntu and all my networking works perfectly using my wired eth0, but when I try to use my ra0 connection (RaLink RT2561/RT61 802.11g PCI card) I have problems. KNetworkManager can see all the wireless networks around me but when I try to connect to any of them KNetworkManager hangs at 28% for a while, and then closes without connecting. I am trying to connect only to unsecured networks. I can get the network working if I run `sudo dhclient ra0` (and then opera and firefox work) but the problem is that then the network only works for non-kde apps. KNetworkManager doesn't see that a connection has been made, and Konqueror, KTorrent, Amarok all act as if there is no network connection. Actually Konqueror sort of works... I can connect to ftp sites, but not http... and when I try to connect to an http site, it will download and display the site's favicon, but not the page. Konqueror gives "An error occurred while loading [http://www.google.com:](http://www.google.com:) Could not connect to host http://www.google.com/." When I try `ping www.google.com` that works though. 

Any help??

---

### Post by Eigenwert on 2007-06-12
I got the same problem.

---

### Post by jdn on 2007-06-17
Hi

Got the same problem (kubuntu 7.04, fujitsu-siemens 7020)

It seems that there is a conflict between knetworkmanager and standard linux networking due to /etc/network/interfaces...

You must not have auto activation of interfaces in this config file bq it seems that there will be a hazard etween knetworkmanager and std linux networking.

Solution - comment out alll external interfaces
 
Below is my /etc/network/interfaces.

All "#" are set by myself - so std installation of kubuntu seems to give this conflict.

I do not know how gnome function but maybe gnome.ubuntu use /etc/network/intefaces in std way.

/Jens @ Aalborg - Denmark

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

---

### Post by ricardisimo on 2007-09-12
I'm having the same problem, so I'll give this a try, but I'm curious as to whether or not I need to add ra0 to /etc/network/interfaces. I ask because when I tried another solution, namely running ```
sudo /etc/init.d/networking restart
```in a terminal, I got the following. Please notice that it never even mentions the ra0 interface:
```
~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                                             RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5580
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0d:87:c3:a0:9d
Sending on   LPF/eth0/00:0d:87:c3:a0:9d
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0d:87:c3:a0:9d
Sending on   LPF/eth0/00:0d:87:c3:a0:9d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```
Thanks in advance. Wish me luck.

---

### Post by ricardisimo on 2007-09-12
No luck either way. When I try a manual configuration of knetworkmanager, it just tells me that the default gateway address is invalid. When I put in an address it seems to like (192.168.8.1, for example) it lets me save any changes, but then seems to ignore them completely.

I might as well give some more info:
```
sudo lshw
{blahblahblah}
*-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 90
             serial: 00:0d:87:c3:a0:9d
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
             resources: ioport:e400-e4ff iomemory:dfffc000-dfffcfff irq:20
        *-network:1
             description: Wireless interface
             product: RT2500 802.11g Cardbus/mini-PCI
             vendor: RaLink
             physical id: 8
             bus info: pci@00:08.0
             logical name: ra0
             version: 01
             serial: 00:0f:66:e6:81:69
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
             resources: iomemory:dfffa000-dfffbfff irq:21
        *-communication
             description: Modem
             product: SmartLink SmartPCI561 56K Modem
             vendor: ALi Corporation
             physical id: a
             bus info: pci@00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: generic bus_master cap_list
             configuration: driver=serial latency=64
             resources: iomemory:dfff9000-dfff9fff ioport:e000-e0ff irq:16
```
Thanks again for any help. I would really like to get Kubuntu up and running, but if this takes too long I'm going right back to Gnome.

---

### Post by Zorael on 2007-09-13
Have you tried [wicd](http://wicd.sourceforge.net)?

I'm a sucker for recommending it to everyone, since it's made of win and awesome.

---

### Post by wieman01 on 2007-09-13
RT2561 is trouble if you happen to have one. I recommend that you replace the driver using "ndiswrapper". Ralink drivers don't work the way others do.

---

### Post by ricardisimo on 2007-09-13
It's actually an RT 2500 that I have, but I gather these aren't much more cooperative. Is ndiswrapper fairly self-explanatory, or should I ask for instructions now? Thanks.

---

### Post by ricardisimo on 2007-09-13
Ditto for wicd, by the way... is it straightforward?

---

### Post by ricardisimo on 2007-09-13
So much for that... it takes my brain a while, but it finally occurs to me that there might be a problem with downloading a solution to not having an internet connection. Time to get creative, or give up on Kubuntu altogether. [sigh]

---

### Post by ricardisimo on 2007-09-13
So here I am... no idea exactly how I did it, other than sort of rewriting /etc/network/interfaces several times. Here's what it looks like now, in case it's of any help to anyone else in the future:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto ra0
iface ra0 inet dhcp

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
```
Wish I could guarantee that this will do anything at all. Good luck.

---

### Post by kevdog on 2007-09-14
Everything probably works now correct???

---

### Post by ricardisimo on 2007-09-14
Well, no, as a matter of fact... I still have to manually configure knetworkmanager, and who knows what is actually doing the trick, considering that knet is probably just like netman, in that there is a delay involved with some changes. Meanwhile I'm altering nine different things, and one of them is working, kind of...

Right now, for example, apt has access to the internet, as does Firefox, which I fortunately downloaded and installed earlier, because Konqueror does NOT have access. Bizarre. KM right now claims to be disconnected, so what are you going to do?

---

### Post by kevdog on 2007-09-14
Let me just confirm a few things and you can tell me where Im wrong.

You have a ra chipset using the rt2500 driver.
lshw -C network

This would confirm the above statement

If the above is true, then these drivers do not work well in Feisty with network manager.  Alternatives would be the following:

1. If you want to continue using network manager
Change driver to ndiswrapper -- which means you need the winxp drivers for your device

2. Dont use network manager
Alternative Options:
Manually bring the interface up as follows (would need to do this after every boot).  Example below assumes interface on wlan0 (I think you told me yours was on ra0 --- but you get the point):
```
sudo ifconfig wlan0 down
sudo killall dhclient dhclient3
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "YOUR_NETWORK_NAME_HERE_in_QUOTES"
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY  <-----Dont need this line if using unencrypted network
sudo dhclient wlan0
```

If the above works can do the following to make these changes permanent:

   manually configure the /etc/network/interfaces file as follows:
If the instructions above did work for you, here's what you can do to make the interface be brought up automatically across reboots:

   1. Edit the /etc/network/interfaces file
      Code:

      gksu gedit /etc/network/interfaces (if you are using Ubuntu)
      kdesu kate /etc/network/interfaces (if you are using Kubuntu)

   2. Look for a section containing "wlan0", if there is no such section, add the following to the bottom of the file:
      Code:

      auto wlan0
      iface wlan0 inet dhcp

   3. Beneath those lines, add the following (*):
      Code:

      	pre-up ifconfig wlan0 up
      	pre-up iwconfig wlan0 essid YOUR_ESSID
      	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

   4. If you have it installed (you will if you are using dapper), remove network manager (!)
      Code:

      sudo aptitude purge knetworkmanager


Yet another alternative would be to switch to WICD and dump network manager/knetworkmanager.

And yet one more suggestion -- as if you havent had enough already -- update your driver if you intend to keep the ra driver to the rt2500 serial monkey driver.  Here is a link that uses the rt73 driver as an example -- however the process is exactly the same for you except substitute 2500 for 73 when performing the actions, and dont blacklist the rt2500 driver.
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)


Good luck

---

### Post by wieman01 on 2007-09-14
> **ricardisimo said:**
> So much for that... it takes my brain a while, but it finally occurs to me that there might be a problem with downloading a solution to not having an internet connection. Time to get creative, or give up on Kubuntu altogether. [sigh]
It's not a Kubuntu specific problem. Ralink drivers are different and you will face the same problem in all Ubuntu derivatives. Not sure as far as other distribution are concerned but Ralink drivers generally mean trouble. You need to configure WPA, WEP, etc. manually unless you revert to using "ndiswrapper".

---

### Post by wieman01 on 2007-09-14
> **kevdog said:**
> Yet another alternative would be to switch to WICD and dump network manager/knetworkmanager.
That's exactly my point, Kevdog. It's no alternative at all. Ralink drivers have a unique design, therefore this thread. Updating the driver won't help much either. I have a Ralink chipset on one of my PCs as well and have through it... I eventually decided to blacklist the driver and use "ndiswrapper" instead. It works great now but it took me a while to figure it out.

---

### Post by ricardisimo on 2007-09-17
In case anyone is curious, I reinstalled Ubuntu. Network Manager has it's own issues, but nothing like this. Maybe I'll give Kubuntu a try on my next comp, although I must say I was pretty stunned by how much slower everything compared to Gnome. Everything has its pluses and minuses, I guess.

---

### Post by kevdog on 2007-09-17
So what did you do for the wireless solution.

I have both gnome and kde installed, and really dont notice any "performance" difference.  Maybe its just my hardware.  Kind of like the Gnome interface with skins, but kde apps (amarok, k3b, k9copy, kaffeine) are much better than their gnome counterparts IMO.

---

### Post by wieman01 on 2007-09-18
> **kevdog said:**
> So what did you do for the wireless solution.

I have both gnome and kde installed, and really dont notice any "performance" difference.  Maybe its just my hardware.  Kind of like the Gnome interface with skins, but kde apps (amarok, k3b, k9copy, kaffeine) are much better than their gnome counterparts IMO.
Same here... no performance gap at all. KDE runs just fine on any computer that I have. Maybe "felt" performance is different though.

---

### Post by ricardisimo on 2007-09-18
I never did find a reasonable solution to the wireless problem. Every time I thought I'd solved it, I'd restart to test it again, but no... I'd have to fumble with it for another half-hour, or even longer.

I find that KDE apps embarrass their Gnome counterparts regularly, which is the main reason why I was intent on switching. Believe me, if I went into this with a bias, it was towards Kubuntu. However, it really did seem like everything took 3 or 4 times as long to load, and twice as long to do their jobs. Lots of hanging and pausing. A bit of crashing along the way as well.

Someone mentioned installing kubuntu-desktop on top of the ubuntu core, which I may try at some point. We'll see. Thanks again.

---

### Post by kevdog on 2007-09-18
Can you summarize your wireless problem -- I thought you had it solved.  Ubuntu is cool too -- Im using it right know.  I dont find that much difference between the two desktop environments really, its only that I find some of the kde apps more useful.  If you install kde-desktop ontop of ubuntu (thats what I did) you get the best of both worlds.

---

### Post by ricardisimo on 2007-09-18
The problem is exactly as described by the original poster. I was mistaken when I thought it was solved.

---

### Post by urk_nono on 2007-09-26
>  
No luck either way. When I try a manual configuration of knetworkmanager, it just tells me that the default gateway address is invalid. When I put in an address it seems to like (192.168.8.1, for example) it lets me save any changes, but then seems to ignore them completely.

Concerning setting default gateway I had the same problem with it ignoring. You might want to try leaving it blank. When you apply your settings it should save your settings properly. I had the same problem earlier today.

---

