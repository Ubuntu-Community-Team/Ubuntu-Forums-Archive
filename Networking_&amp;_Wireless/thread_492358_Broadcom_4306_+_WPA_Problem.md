---
title: "Broadcom 4306 + WPA Problem"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by explosive on 2007-07-04
Hey,

Im trying to set up a Broadcom 4306 (rev 2) in Ubuntu 7.04.

I have successfully setup a Broadcom 4306 (rev 3) in Ubuntu 7.04 server edition with WPA that works very well using the instructions on the Ubuntu Wiki detailing bcm43xx and the instructions in the HOWTO pinned to the top of this forum for the WPA.

I have followed the same instructions for my desktop installation of 7.04 but have run into problems. The card is detected and installed and I can do a 'iwlist scan' and see all available networks but I cannot stay connected to my own - so i suspect this is a WPA problem?

iwevent seems to show the problem but I do not know how to fix it.

> 
19:39:32.251970   eth1     New Access Point/Cell address:Not-Associated
19:39:32.603485   eth1     Scan request completed
19:39:32.604348   eth1     Set Mode:Managed
19:39:32.604412   eth1     Set ESSID:"z765treg"
19:39:32.614237   eth1     Custom driver event:authenticated
19:39:32.618133   eth1     New Access Point/Cell address:00:18:4D:CC:2D:D4
19:39:36.614110   eth1     New Access Point/Cell address:Not-Associated
19:39:36.980024   eth1     Scan request completed
19:39:36.980326   eth1     Set Mode:Managed
19:39:36.980384   eth1     Set ESSID:"z765treg"
19:39:36.989589   eth1     Custom driver event:authenticated
19:39:36.993533   eth1     New Access Point/Cell address:00:18:4D:CC:2D:D4
19:39:40.993759   eth1     New Access Point/Cell address:Not-Associated
19:39:41.384322   eth1     Scan request completed
19:39:41.384659   eth1     Set Mode:Managed
19:39:41.384704   eth1     Set ESSID:"z765treg"
19:39:41.396401   eth1     Custom driver event:authenticated
19:39:41.397435   eth1     New Access Point/Cell address:00:18:4D:CC:2D:D4


this loops every few seconds - the card seems to keep losing the connection to my AP... this doesn't happen on my server edition installation that works fine.

Any ideas???

---

### Post by explosive on 2007-07-05
*Bump*

---

### Post by explosive on 2007-07-06
Anyone got any ideas? I'm really stumped with this!

---

### Post by explosive on 2007-07-08
Another bump!

---

### Post by kevdog on 2007-07-08
Do you have wpasupplicant installed???  Are you using network manager, or are you configuring the /etc/network/interfaces file manually??  WPA will never work straight out of the box without at least wpasupplicant and a little tweaking!

---

### Post by explosive on 2007-07-08
Yep, wpa_supplicant is installed & I'm editing /etc/network/interfaces manually.
As I said I have got WPA working on one Ubuntu box already there is just problem on my second box.

---

### Post by kevdog on 2007-07-08
Are you trying to use network manager??

Can you post your interfaces file??

Does your wireless driver support wpa??

What is result of:
iwlist scan

---

### Post by explosive on 2007-07-08
I'm using the same driver as I used on the PC that works with WPA.

iwlist scan works and finds my AP:
> 
eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:CC:2D:D4
                    ESSID:"z765treg"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-63 dBm  Noise level=-64 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 328ms ago
          Cell 02 - Address: 00:17:3F:0D:54:58
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-80 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 4520ms ago

I have tried WPA1 and WPA2 (AP is set to accept both).

/etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
	address 10.20.251.35
	netmask 255.255.255.0
	network 10.20.251.0
	broadcast 10.20.251.255
	gateway 10.20.251.75
	
	# wireless-* options are implemented by the wireless-tools package
	#wireless-mode managed
	#wireless-essid z765treg
	
	#wpa stuff
	wpa-driver wext
	wpa-ssid z765treg
	wpa-ap-scan 1
	wpa-proto RSN
	wpa-pairwise CCMP
	wpa-groupwise CCMP
	wpa-key-mgmnt WPA-PSK
	wpa-psk cd994ea16644e030591d340b7b0e0532eefe3a41f3785047797d9d9f9a381ea2


	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 212.159.6.9 212.159.6.10


---

### Post by kevdog on 2007-07-08
Just stepping back for a minute...
Everything looks fine on your interfaces file.  I guess the wpa-driver for bcm43xx is wext (thought that was a generic driver that also worked with ndiswrapper).

Does your card connect and stay connected if WPA is removed from the equation --- meaning no encryption is used?  I just want to make sure this is a WPA problem and not a driver problem.

---

### Post by explosive on 2007-07-08
Yes, their appears to be basic wireless connevtivity.

---

### Post by kevdog on 2007-07-08
> Yes, their appears to be basic wireless connevtivity.

Not to be rude, but what does that mean.  There is or is not basic connectivity??

---

### Post by explosive on 2007-07-08
Sorry, yes my reply was rubbish!!

The wireless works without WPA enabled.

---

### Post by kevdog on 2007-07-08
I figured you were going to say that.

Ok, lets step the complexity up from no encryption for a while.

Can you set your router to use WPA version 1, PSK, TKIP algorithm.

Within your /etc/network/interfaces file (back up old configuration first)
edit it to just contain 
auto lo
iface lo inet loopback

Then create a file named /etc/default/wpasupplicant with root priviledges
and within file just add the line:
ENABLED=0

Then
sudo /etc/init.d/dbus restart

Basically I realized there is no static IP address with this method, and Im letting network-manager handle all the WPA connectivity, however I just stepwise approaching this issue to see if something works.

---

### Post by explosive on 2007-07-09
Sorry, I have an apology to make!
I'm not sure what was happening last night but the wireless is not working with encryption disabled.

---

### Post by kevdog on 2007-07-09
Although you probably dont want to do this, I would recommend installing ndiswrapper over the bcm43xx driver.  Its a little bit more work, however you will get 54 Mb/sec compared to 11 Mb/sec.  Ill walk you through it if you want!

---

### Post by explosive on 2007-07-09
Yes, I'm willing to try that. Any pointers you can give would be great :) - Also how can I ensure that bcm43xx is fully removed?

---

### Post by kevdog on 2007-07-09
Id recommend installing ndiswrapper from source if possible.  Also you really dont need to remove bcm43xx, you simply need to blacklist the module name.  To do this:

```
gksu gedit /etc/modprobe.d/blacklist
```

Add to end of file:
```
blacklist bcm43xx
```

Upon reboot the module should be blacklisted.

Here is the ndiswrapper page with instructions:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Also if installating from source, as a prerequisite you will need the build-essential package installed first.  Here is how to do this:

If you have a wired ethernet connection skip to step#4.  All commands are typed at command prompt:
```
1. Stick Ubuntu installation cd into drive, wait for it to "spin" up
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential
```

---

### Post by explosive on 2007-07-09
I have followed the instructions. The only 2 drivers in the ndiswrapper list for my card 14e4:4320 (rev 02) are both for laptop versions (mine is PCI for a desktop) and one is for the USA only so I haven't tried that.

The driver that I have tried seems to install fine but will never connect to my router. iwconfig always reports the ESSID as off/any no matter how many times I try to set it.

---

### Post by explosive on 2007-07-09
I have found more drivers in the list that have been used for my card before and I am still not able to connect to the router. I just get the ESSID of: off/any.

---

### Post by kevdog on 2007-07-09
Lets debug a few things:

Please post:
ndiswrapper -v
ndiswrapper -l

lshw -C network

dmesg | grep ndiswrapper

/etc/network/interfaces
/etc/iftab
ifconfig

I know thats a lot (wish I could have made more things up for you to post :))

---

### Post by explosive on 2007-07-09
ndiswrapper -v
> 
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

ndiswrapper -l
> 
bcmwl5a : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

lshw -C network
>   *-network:0
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@00:0c.0
       logical name: eth0
       version: 00
       serial: 00:60:08:2d:75:5a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=10.20.251.200 latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:d800-d83f irq:10
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth1
       version: 02
       serial: 00:30:bd:98:e1:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.47+Broadcom,06/25/2004, 3.40.7 ip=10.20.251.35 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:efffc000-efffdfff irq:9

dmesg | grep ndiswrapper
> [  152.263713] ndiswrapper version 1.47 loaded (smp=yes)
[  152.356433] ndiswrapper: driver bcmwl5a (Broadcom,06/25/2004, 3.40.73.0) loaded
[  152.367234] ndiswrapper: using IRQ 9
[  152.672769] usbcore: registered new interface driver ndiswrapper
[  152.682476] ndiswrapper: changing interface name from 'wlan0' to 'eth1'

/etc/network/interfaces
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
	address 10.20.251.35
	netmask 255.255.255.0
	network 10.20.251.0
	broadcast 10.20.251.255
	gateway 10.20.251.75
	
	# wireless-* options are implemented by the wireless-tools package
	#wireless-mode managed
	wireless-essid z765treg
	
	#wpa stuff
	#wpa-driver wext
#	wpa-ssid z765treg
#	wpa-ap-scan 1
#	wpa-proto RSN
#	wpa-pairwise CCMP
#	wpa-groupwise CCMP
#	wpa-key-mgmnt WPA-PSK
#	wpa-psk cd994ea16644e030591d340b7b0e0532eefe3a41f3785047797d9d9f9a381ea2


	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 212.159.6.9 212.159.6.10

iface eth0 inet static
address 10.20.251.200
netmask 255.255.255.0
gateway 10.20.251.75

auto eth0

/etc/iftab
> # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:60:08:2d:75:5a arp 1
eth1 mac 00:30:bd:98:e1:ac arp 1

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:60:08:2D:75:5A  
          inet addr:10.20.251.200  Bcast:10.20.251.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:30:BD:98:E1:AC  
          inet addr:10.20.251.35  Bcast:10.20.251.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Memory:efffc000-efffe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1508 (1.4 KiB)  TX bytes:1508 (1.4 KiB)



---

### Post by kevdog on 2007-07-09
Ok here is what I want you to try.  Everywhere in the /etc/network/interfaces and /etc/iftab file, I want you to change eth1 to wlan0. ndiswrapper automatically assumes an alias on wlan0.

Reboot.  Everything else looks good!

---

### Post by explosive on 2007-07-09
Changed to wlan0.
It still has the same problem.

---

### Post by explosive on 2007-07-09
Just a note:
When I install the driver using Ndiswrapper I get the message:
forcing parameter IBSSGmode from 0 to 2

---

### Post by kevdog on 2007-07-09
Ok something has to be causing an error someplace.

Please post following:
iwlist scan
lshw -C network
/etc/network/interfaces/
/etc/iftab

The entire dmesg output (may have to include this as an attachment).  One of these things has to give some information why its not working.

Oh yea - turn off any WPA/WEP or MAC filtering on the router for now -- my goal right now is not WPA but basic connectivity.  After this is working we will add in WPA

---

### Post by explosive on 2007-07-09
iwlist scan
> wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:0D:54:58
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


This isn't my network (it is my neighbours)! - My network *used* to show up when i did an iwlist scan with the bcm43xx drivers. I can connect to my network with my macbook so the wireless *is* enabled and the ESSID is being broadcast so no idea why it doesn't show up here!

lshw -C network
> 
  *-network:0
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@00:0c.0
       logical name: eth0
       version: 00
       serial: 00:60:08:2d:75:5a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:d800-d83f irq:10
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: wlan0
       version: 02
       serial: 00:30:bd:98:e1:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,07/17/2003, 3.30.1 ip=10.20.251.35 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:efffc000-efffdfff irq:9

/etc/network/interfaces/
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
	address 10.20.251.35
	netmask 255.255.255.0
	network 10.20.251.0
	broadcast 10.20.251.255
	gateway 10.20.251.75
	
	# wireless-* options are implemented by the wireless-tools package
	#wireless-mode managed
	wireless-essid z765treg
	
	#wpa stuff
	#wpa-driver wext
#	wpa-ssid z765treg
#	wpa-ap-scan 1
#	wpa-proto RSN
#	wpa-pairwise CCMP
#	wpa-groupwise CCMP
#	wpa-key-mgmnt WPA-PSK
#	wpa-psk cd994ea16644e030591d340b7b0e0532eefe3a41f3785047797d9d9f9a381ea2


	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 212.159.6.9 212.159.6.10

iface eth0 inet static
address 10.20.251.200
netmask 255.255.255.0
gateway 10.20.251.75

/etc/iftab
> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:60:08:2d:75:5a arp 1
wlan0 mac 00:30:bd:98:e1:ac arp 1



dmesg - attached (I had to delete some stuff from the very top (looks like boot-up stuff) cos the file was too big to upload!

---

### Post by kevdog on 2007-07-09
Sorry missing attachment

Another One Last Thing -- you cant have wired ethernet and wireless running at same time with Ubuntu.  This means when you reboot you will have to pull the ethernet cord out of the connector and then plug in the card to see if it works.  I know its a pain in the butt, but that is the way it is!

---

### Post by explosive on 2007-07-09
The attachment is there now.
The ethernet cord is out. I only have the one that is conencted to this computer so I had to undo it all before in order to setup ndiswrapper!

I'm using a usb stick to move all the logs to this pc to post here :) (youll see the usb stick being connected and disconnected in dmesg i think)

---

### Post by kevdog on 2007-07-09
Your problem is beginning to be a pain in the butt!

Ok -- you can see your neighbor's router.
Is your router without WPA/WEP or MAC filtering?

Are you using network manager -- I guess not since you are trying to work with static IP??

Try doing this:  Change this:

auto wlan0
iface wlan0 inet static
address 10.20.251.35
netmask 255.255.255.0
network 10.20.251.0
broadcast 10.20.251.255
gateway 10.20.251.75

to:
auto wlan0
iface wlan0 inet dhcp

Again Im trying to make this as simple as possible.  We can add complexity later.

---

### Post by explosive on 2007-07-09
Security is off and it has been added to the MAC filter list.
I can't put it to DHCP without messing up all the other computers on the network!

---

### Post by kevdog on 2007-07-09
Here is the mac address of the card:
00:30:bd:98:e1:ac

Make sure then this is the correct MAC address in the router. 

Im running out of ideas.

Change this:
auto wlan0
iface wlan0 inet static
address 10.20.251.35
netmask 255.255.255.0
network 10.20.251.0
broadcast 10.20.251.255
gateway 10.20.251.75

to 
auto wlan0
iface wlan0 inet static
address 10.20.251.35
netmask 255.255.255.0
gateway 10.20.251.75

The other problem is that if you issue command
iwlist scan

and you cant see your router, then nothing is going to work.

---

### Post by explosive on 2007-07-09
The mac address is correct.

That is what I can't understand! It *was* able to see the router via iwlist scan using th bcm43xx drivers and I can't understand how changing to ndiswrapper means that it van now only see my neighbours router?

---

### Post by kevdog on 2007-07-09
Look, Im kind of out of ideas, but I guess if I were in your shoes at this point, I might try a different driver than the one you have.

Can you give me the name and version of the card along with the following:
lspci -nn

Thanks -- I'll look for a driver for you too!

---

### Post by explosive on 2007-07-10
This is the line you will want:

> 00:0d.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)


It is a Belkin F5D7000uk. - Linux reports it as a rev2 but the PCI board itself says rev1! I have tried all the rev2 drivers, and a rev3 driver as well as belkins rev 1 driver but none seem to work.

Each of them has the same problem - they can see my neighbours router - but not mine (most of the time!). - I turned the PC on earlier and the first time i ran iwlist scan it found my router but each subsequent time i tried it couldn't find it - even after a reboot!

---

### Post by kevdog on 2007-07-10
Out of ideas -- maybe you should just go back to bcm43xx -- even though it wasnt exactly like that was doing anything either.

If you want to switch back within /etc/modprobe.d/blacklist
blacklist ndiswrapper

Put a # sign (comment) in front of
blacklist bcm43xx

Sorry -- seems like this belkin device just will not work -- at least for me!
If you figure it out let me know!

---

### Post by explosive on 2007-07-10
Thanks for all your time and effort trying to fix this one! - Much appreciated :)

I'm a bit fed up with it so I'll leave it for a bit and come back to it I think!

---

### Post by fxjr on 2008-04-04
Hi, kevdog!

I'm having the same problem with ubuntu 7.10 and 8.04. 

My broadcom card keeps in a loop trying to establish a connection to my router.

When I don't use WPA it works ok.

i'm using networkmanager. All dhcp. 

Do you have any idea of why it is looping?

Thanks in advance.

---

### Post by kevdog on 2008-04-04
You are going to have to troubleshoot your WPA problems using a manual command line connection (see link in signature), so some debugging output can be generated that might shed light on the problem.

---

### Post by fxjr on 2008-04-04
Hi, kevdog!

I saw your manual command line connection section. And I was about to try it when I remember that today I got an updated kernel 2.6.24-14 and give it a try. To my surprise IT WORKED like a charm!!!!

It's awesome!!! Ubuntu rulez!! Gnu/Linux rulez!! I'm very happy to get it working with no problems now!!

Thank you very much for your attention and promptly reply.

---

### Post by fxjr on 2008-04-08
Hi, kevdog!

It seems the problem is still present :(

After some more updates, networkmanager DOESN'T WORK with WPA again!! :(

I don't know what can be happening... I thought it was a kernel issue, but when I booted back on 2.6.24-14, on which wpa worked for the first time, it didn't too :(

I will try your tutorial and post any problems I see. 

Thanks in advance.

---

### Post by wojnicki on 2008-06-08
I've got the same problem. After starting:  wpa_supplicant  -D wext -i wlan0 -c /etc/wpa_supplicant.conf, it keeps repeating:

Associated with 00:1c:f0:88:c9:a8
Associated with 00:1c:f0:88:c9:a8
Associated with 00:1c:f0:88:c9:a8
Associated with 00:1c:f0:88:c9:a8
Associated with 00:1c:f0:88:c9:a8
....

any help?

---

