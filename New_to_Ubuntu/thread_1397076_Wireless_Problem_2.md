---
title: "Wireless Problem 2"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Tholley on 2010-02-02
I have had an ongoing problem with getting wireless to work on this computer.
I am using a Linksys wireless pci adapter - wmp54g Ver.4.1 . Old computer with Ubuntu 9.04.

If I click on Windows Wireless Drivers in Sys/Admin menu, it says "unable to see if hardware is present." I click on OK and then it shows RT61 Hardware Present: Yes

If I click on Configure Network, everything is grayed out, including Unlock.
If I go thru Sys/Admin and select Network, It comes up ok, I can Unlock, and go to properties on the Wireless connection, under Network Name I see my sys id, but in password type, the only choice is WEP, no WPA.

Here are my settings...

```
kaylen@kaylen-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0d:87:48:c0:aa
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.107 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: wlan2
       version: 00
       serial: 00:18:39:1c:ff:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt61 driverversion=1.53+Linksys, A Division of Cisc latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:b8:d7:6b:3e:4c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kaylen@kaylen-desktop:~$ 

```

Hoping it is something simple... ;)

---

### Post by Enigmapond on 2010-02-02
I also have a Ralink card and I used the standard Network Manager in ubuntu to connect how ever that kept disconnecting on occasion. I then install wicd and use that manager which works very well.

---

### Post by spiderbatdad on 2010-02-02
It looks like you've made some progress since previous post, where the card was unclaimed.
From what I have seen, if you want wpa with this device, suggestions include the serial monkey driver. And blacklisting rt61pci, modprobing rt61.
Blacklisting works a little differently in karmic as far as I can tell.

That is instead of putting everything in blacklist.conf, you might actually create a file called /etc/modprobe.d/blacklist/rt61pci.conf and in that file have the line "blacklist rt61pci."
Before installing any source drivers, you might just try creating the blacklist, then:
```
sudo modprobe -r rt61pci
sudo modprobe rt61
sudo /etc/inti.d/networking restart
```

---

### Post by Tholley on 2010-02-02
> **Enigmapond said:**
> I also have a Ralink card and I used the standard Network Manager in ubuntu to connect how ever that kept disconnecting on occasion. I then install wicd and use that manager which works very well.

Installed wicd, all looked good, put in WPA passphrase, but still won't connect.

---

### Post by Tholley on 2010-02-02
> That is instead of putting everything in blacklist.conf, you might actually create a file called /etc/modprobe.d/blacklist/rt61pci.conf and in that file have the line "blacklist rt61pci."

Ok.. can you help me do this?

Plus on this machine I am using Jaunty, not Karmic, that is on my main computer.

---

### Post by Enigmapond on 2010-02-02
Quite possibly the problem stems from the router itself? Maybe re-set the connection and make sure it's allowing a connection?? Just a thought..

---

### Post by spiderbatdad on 2010-02-02
You can just run the commands one at a time as posted above and see if your networking kicks in.

---

### Post by Tholley on 2010-02-02
> **Enigmapond said:**
> Quite possibly the problem stems from the router itself? Maybe re-set the connection and make sure it's allowing a connection?? Just a thought..

Rebooted everything, unplugged the Ethernet cable, and now wicd says No wireless network found. ?

---

### Post by spiderbatdad on 2010-02-02
There is info on google for the serial monkey driver if you google serial monkey rt61. It isn't the simplest thing you'll ever do on linux but it isnt too terribly difficult to follow either. For example: [http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/](http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/)

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> You can just run the commands one at a time as posted above and see if your networking kicks in.

this is what I got...


kaylen@kaylen-desktop:~$ sudo modprobe -r rt61pci
[sudo] password for kaylen: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
kaylen@kaylen-desktop:~$ sudo modprobe rt61
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module rt61 not found.
kaylen@kaylen-desktop:~$ sudo /etc/inti.d/networking restart
sudo: /etc/inti.d/networking: command not found
kaylen@kaylen-desktop:~$

---

### Post by Tholley on 2010-02-02
The network shows to be UNCLAIMED now again!  ???

---

### Post by spiderbatdad on 2010-02-02
The final command is not found because it should read init.d instead of inti.d
The others are the result of missing drivers. This link should get you going with wpa: [http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/](http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/)

---

### Post by spiderbatdad on 2010-02-02
The link to download the driver appears to be broken. Try sourceforge directly: [http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt61-cvs-daily.tar.gz/](http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt61-cvs-daily.tar.gz/)

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> The final command is not found because it should read init.d instead of inti.d
The others are the result of missing drivers. This link should get you going with wpa: [http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/](http://linuxkc.wordpress.com/2008/03/10/howto-install-serialmonkey-drivers-for-ralink-rt61-wireless-card/)

Started to follow the instructions and site may be gone? 

```
kaylen@kaylen-desktop:~$ lspci | grep RaLink
01:04.0 Network controller: RaLink RT2561/RT61 802.11g PCI
kaylen@kaylen-desktop:~$ wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
--2010-02-02 21:09:43--  http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
Resolving rt2x00.serialmonkey.com... 208.110.70.80
Connecting to rt2x00.serialmonkey.com|208.110.70.80|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-02-02 21:09:43 ERROR 404: Not Found.

kaylen@kaylen-desktop:~$ 
```

---

### Post by spiderbatdad on 2010-02-02
see post #13 :)

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> The link to download the driver appears to be broken. Try sourceforge directly: [http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt61-cvs-daily.tar.gz/](http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt61-cvs-daily.tar.gz/)

Do I save the tar.gz file, or open with Archive Manager?

---

### Post by spiderbatdad on 2010-02-02
save. then right click "extract here" to create the directory.

---

### Post by Tholley on 2010-02-02
OK! all seems to have gone well so far.
I am here now and not sure what it means...

**All that remains is setting up the interfaces file. As an example here is mine:**

What do I do now?

---

### Post by spiderbatdad on 2010-02-02
try to let network manager take over without configuring interfaces manually. Just reboot or restart networking with ```
sudo /etc/init.d/networking restart
```Then click on the network manager icon and see what happens.

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> try to let network manager take over without configuring interfaces manually. Just reboot or restart networking with ```
sudo /etc/init.d/networking restart
```Then click on the network manager icon and see what happens.

restarted network, clicked on wicd icon up top, saw my connection, tried to connect, seems to think it is wep, but in advanced settings I have WPA set with passphase...

gonna reboot system and see...

---

### Post by spiderbatdad on 2010-02-02
ack. please uninstall wicd and rely on network manager for this testing.

---

### Post by Tholley on 2010-02-02
Everthing looked good, until I clicked on connect, and then all the Wireless networks disapereared! 

do I need to install another driver? 

here is the settings...

```
kaylen@kaylen-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0d:87:48:c0:aa
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:05:c4:ec:eb:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kaylen@kaylen-desktop:~$ 


```

What gives?

---

### Post by spiderbatdad on 2010-02-02
```
sudo apt-get install network-manager network-manager-gnome
sudo apt-get remove wicd
```

make sure the module is loaded:
```
sudo modprobe rt61
sudo /etc/init.d/networking restart
```

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> ```
sudo apt-get install network-manager network-manager-gnome
sudo apt-get remove wicd
```make sure the module is loaded:
```
sudo modprobe rt61
sudo /etc/init.d/networking restart
```

I un-installed wicd and rebooted before I saw this, now no internet at.

Will try to type in and see if it brings it back...

---

### Post by spiderbatdad on 2010-02-02
great. I think you will need the live cd to reinstall network manager now. **Sorry** for the confusion. You will probably have to insert the live cd, close any dialog that open, then go to System>>Administration>>Software Sources from your desktop and check the box Installable from cdrom. Run the commands again to install nm and nm-gnome.

---

### Post by Tholley on 2010-02-02
Nothing... not even a wired connection or even the network icon. 

When I tried to run the second set of commands

sudo modprobe rt61
sudo /etc/init.d/networking restart
I got allot of errors...

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> great. I think you will need the live cd to reinstall network manager now. **Sorry** for the confusion. You will probably have to insert the live cd, close any dialog that open, then go to System>>Administration>>Software Sources from your desktop and check the box Installable from cdrom. Run the commands again to install nm and nm-gnome.


ok,,, will give that a go...

---

### Post by spiderbatdad on 2010-02-02
You'll get it. You saw post #25?

---

### Post by Tholley on 2010-02-02
> **spiderbatdad said:**
> You'll get it. You saw post #25?

Yes... 

Actually I will need to work on that tomorrow, I need to get some sleep now, so I won't be dragging too bad at work.

Thank allot for all the help, and I should be working on it about the same time as I started tonight, so hopefully you will be around in case I run across any more problems!

Thanks again, and until tomorrow....

---

### Post by spiderbatdad on 2010-02-02
just so you know, a majority of wireless cards work with ubuntu "out of the box." You are lucky enough to get this experience in jumping though hoops

---

### Post by Tholley on 2010-02-03
> **spiderbatdad said:**
> just so you know, a majority of wireless cards work with ubuntu "out of the box." You are lucky enough to get this experience in jumping though hoops
 
This morning before work, I figured I would mess with it a little, I put in the 9.04 live cd, went to Software Sources, checked the Installable for Cdrom/DVD, it said something about software being out of date, clicked Close, it tried to download updates, but couldn't since I don't have ANY connection now. 
 
Tried to run the commands again, but didn't seem like it was reading off the cd, kept getting errors. 
 
Rebooted into live cd, the wireless worked perfect, so like you said, it should work right out of the box.
 
booted back normal, tried again, and it said it installed 2 files, but still nothing.
 
lshw also says my eth0 is "disconnected."

---

### Post by Tholley on 2010-02-03
Ok, I'm going to try a couple more times to run the commands again with live cd in, if I can't get it them to work, I'm just going to re-install 9.04m since on this particle computer there is nothing on it I would lose.

---

### Post by Tholley on 2010-02-03
I got my wired connection back, didn't realize all I had to do was enable... duhhh.

So ran the first apt-get command... that seemed to work, asked me to reboot, and my network icon is back, but still no wireless. 

Just wanted to bring this up in case it matters, whenever I go to Windows Wireless Drivers, it always has a popup window that says "Unable to see if hardware is present."
I always click OK, then I see the rt61 driver.

I am about to run the other modprobe commands and see what happens.

Hope you are out there to help, spiderbatdad!

---

### Post by Tholley on 2010-02-03
This is what I got...

kaylen@kaylen-desktop:~$ sudo modprobe rt61
[sudo] password for kaylen: 
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
kaylen@kaylen-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 2627
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:87:48:c0:aa
Sending on   LPF/eth0/00:0d:87:48:c0:aa
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.pan0.pid with pid 3510
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/96:da:ac:a1:a3:bd
Sending on   LPF/pan0/96:da:ac:a1:a3:bd
Sending on   Socket/fallback
Cannot find device "wlan2"
There is already a pid file /var/run/dhclient.wlan2.pid with pid 3433
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Bind socket to interface: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "xxxxxxx".  
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan2 ; No such device.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan2: ERROR while getting interface flags: No such device
wlan2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan2.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/96:da:ac:a1:a3:bd
Sending on   LPF/pan0/96:da:ac:a1:a3:bd
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[pan0]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[pan0]: waiting for interface wlan2 before doing NFS mounts
 * if-up.d/mountnfs[pan0]: waiting for interface eth0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:87:48:c0:aa
Sending on   LPF/eth0/00:0d:87:48:c0:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 33928 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan2 before doing NFS mounts
                                                                         [ OK ]
kaylen@kaylen-desktop:~$ 

I X'd out my passprhase... 

so If I don't hear anything soon.... I am doing a fresh install.

Damn that wicd!!!

---

### Post by Tholley on 2010-02-03
Well... I re-installed 9.04, and like it should... right out of the box, it is working!
Maybe it works best if the wireless adapter is already installed when one installs Ubuntu.

Dunno... but it is downloading all the updates via wireless now, so I am happy.

Thanks for all the hard work and help spiderbatdad!!

---

