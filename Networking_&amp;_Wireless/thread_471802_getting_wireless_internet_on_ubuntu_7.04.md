---
title: "getting wireless internet on ubuntu 7.04"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Dman87 on 2007-06-12
Iv got a belkin wireless G plus MIMO router and can connect from my desktop pc (windows xp) to the internet fine, but i cannot get ubuntu to connect to the wireless for some reason. my connection type is dynamic im not broadcasting ssid security is WPE-PSK(no-server) encryption type AES. iv tryed to connect to other wireless network thing and entered all the details correctly. is there anything im doing wrong or should be doing. btw the ubuntu is 7.04 and its live cd not installed will that make a difrence?

---

### Post by dardack on 2007-06-12
dman not expert myself but might be able to help.  I COULD NOT get my wireless to connect to my router without it broadcasting the ID.  At least with network-manager (i had to unistall that cause my internet was dropping cause NM kept scanning and dropping the connection), but i didn't try it manually.  
2. we need to make sure that ubuntu is seeing your wiireless card and has it setup.
As far as the wireless, could you post the relevant results of:

sudo lshw

the section under network should indicate that it found a wireless
device and the product will be listed. What  info is under the product
heading?
Could you also post the results of :

sudo ifconfig -a
and
sudo iwconfig

In my case my PCI wireless worked out of box, but for my laptop with a Belkin wirless G card, i had to use ndiswrapper-common, a windows driver for my wireless chip.

ALSO do you mean WPA-PSK not WPE?  There is also a sticky thread about getting WPA working in ubuntu, might want to check out.
This will be a start.  (and did you know not broadcasting really does nothing? IIRC with a sniffer someone can get your SSID,  when a client connects to the router it actually sends out the SSID in clear text, again IIRC)

---

### Post by Dman87 on 2007-06-12
here you go;

**sudo lshw**
  *-network DISABLED 
                description: Wireless interface 
                product: BCM4306 802.11b/g Wireless LAN Controller 
                vendor: Broadcom Corporation 
                physical id: 3 
                bus info: pci@03:03.0 
                logical name: eth1 
                version: 03 
                serial: 00:0b:7d:17:d8:9e 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master ethernet physical wireless 
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g 
                resources: iomemory:dfcfe000-dfcfffff irq:18 


**sudo ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:11:43:4B:8C:75   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16  
 
eth1      Link encap:Ethernet  HWaddr 00:0B:7D:17:D8:9E   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:10 Base address:0x4000  
 
eth0:avah Link encap:Ethernet  HWaddr 00:11:43:4B:8C:75   
          inet addr:169.254.5.242  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:16  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:2664 (2.6 KiB)  TX bytes:2664 (2.6 KiB) 


**sudo iwconfig **
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306" 
          Mode:Managed  Access Point: Invalid    
          RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i also have a question, iv done a bit of linux commands in computing but how the flip do most linux users know most of them and all the -a - r and what they do, any special site or book or just practice. also why the sudo in from of the command?

---

### Post by dardack on 2007-06-12
Ok first the -a blah blah is per command.  Like dhclient
sudo dhclient -d wlan0
the -d turns on debugging so if you leave that terminal up it will print out anything going on with it.  to usually find out the options for commands try 
command --help
will usually print out the -(dash) options.

as far as SUDO goes, sudo is ubuntu for superuser but not.  It enables you to run commands that only SU can use without being logged in as SU.  More secure that way.


ok good it seems like it can see that you have a wireless card.  I do not know how to get WPA working, so you might want to turn this off for now (either through antoher computer or a wired connection) just try:

sudo ifdown [eth0 or whatever wired interface] (which i believe yours is eth0)
sudo killall dhclient
sudo iwconfig eth1 essid "your ESSID without the quotes" mode managed enc off
sudo dhclient -d eth1

post what those say.  So if we can connect with WPA off, i can than link you the article on getting WPA working, and you can go from there.  Half the battle is to get wireless working at all, than moving on.  Also, before trying not only disable WPA/security, broadcast your ESSID (unless you're that concerned that in those few minutes someone will hijack your' network, i'm in the suburbs so it's rare that in say 10 minutes someone will hop on.)

---

### Post by Dman87 on 2007-06-12
here are the results:

**sudo ifdown eth0 **
ifdown: interface eth0 not configured


**sudo killall dhclient **
dhclient: no process killed


**sudo iwconfig eth1 essid Donaldson mode managed enc off**
no reslut, must have done the command.


**sudo dhclient -d eth1 **
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
Listening on LPF/eth1/00:0b:7d:17:d8:9e 
Sending on   LPF/eth1/00:0b:7d:17:d8:9e 
Sending on   Socket/fallback 
receive_packet failed on eth1: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.

---

### Post by dardack on 2007-06-12
Ok somethings wrong.  What kind of belkin, model number, version, PCMCIA/USB/PCI?  Also, is the cards light blink or on or anything?


Your probably will need to use NDISWRAPpER to get working (that's what i had to do with my Belkin)

---

### Post by Dman87 on 2007-06-13
Belkin wireless G plus MIMO router, only connects to my pc by the internet cables, firmware up to date, Part # F5D9230uk4 on the belkin web site, ye the light is flickering on the back of the pc. 

how would i get the NDISWRAPpER working on the live cd? iv not installed ubuntu running it from cd. if i put the NDISWRAPpER on a USB pen drive and installed it from there would it put it on the hard drive/swap file virtual memory or somthing, how would i get the NDISWRAPpER to work on a live cd?

---

### Post by Dman87 on 2007-06-13
deleted

---

### Post by Dman87 on 2007-06-13
mmm iv got a new problem now i was going to try download the packages from the net but when i put my wire in for wired connection it said it was connected but when i tryed to use the net it wouldent connect??


was going to try this but  when i searched for ndiswrapper only 2 items appered common and -utils. when i tryed to install them it wouldent work.


copyed from another post
----The Repo Way----
1. Open up synaptic via menus system>administration>synaptic package manager
2. Go to settings>repositories
3. Click on each listing and edit it to include multiverse,universe, and non-free
4. Close repo list and hit the reload button in synaptic
5. Search ndiswrapper (3 items should appear)
6. Select ndiswrapper-utils and you may want to select ndisgtk(gui for installing drivers)
7.With ndisgtk simple go to where your drivers are installed and select the inf file
or
Copy your drivers onto your desktop. Open a terminal and enter the following command

sudo ndiswrapper -i ~/Desktop/****.inf (replace the **** witht he driver name)

With either method you will still have to enter the following two commands into your terminal

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Configure your network via the menus System>Administration>Networking

After all of this youll be done. I would recommend a shutdown at this point. If you just restart your wireless lights wont shut off. Shutdown and then turn your pc back and on see if everything is working

This is the method I recommend you could do the source but Im not very good at debugging build error messages so youll have to ask for help.

---

### Post by Dman87 on 2007-06-13
stop the press got it to work now check [http://ubuntuforums.org/showthread.php?p=2838941#post2838941](http://ubuntuforums.org/showthread.php?p=2838941#post2838941) for the attachment worked like a charm np.

 thanx for your help dardack.

---

