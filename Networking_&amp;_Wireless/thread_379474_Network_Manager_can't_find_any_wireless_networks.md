---
title: "Network Manager can't find any wireless networks?"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by matthewartz on 2007-03-08
Okay, there are 3000 of these messages posted, so I hate to start another thread, but I've read through everything I can stand to read through and after three days of fiddling and trying things out, I'm getting close to throwing in the towel.  I've read all 62 threads that come up under a search for "wireless, network, manager, doesn't, appear".  Someone, somewhere has figured this out...  

The system stats: Compaq Presario v2670 notebook, AMD Turion 64, Ubuntu 6.1 64-bit version.

I have the infamous Broadcom 4318 wireless card.  However, I don't *think* that's the problem.  I downloaded and installed ndiswrapper 1.37 from sourceforge.  I downloaded the windows wireless drivers from Compaq for my model and used cabextract to pull everything into a folder ndiswrapper could read.  Installed ndiswrapper, installed the driver.  

ndiswrapper -l returns:
```
martz@martz-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```

I followed other recommendations:
```
martz@martz-laptop:~$ sudo gedit /etc/modprobe.d/blacklist (and blacklisted both bcm43xx & bcm43xx.ko - per thread 303694)
martz@martz-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
```
(and all of the other commands they recommend - e.g. depmod, modprobe, ndiswrapper -m, etc.)

Rebooted, little blue light turns on.  {One little victory - yes!}

System > Administration > Network shows the card.  Configure for my network, but get no connection.  (Also tried changing my network to be open (no protection) and still couldn't get it to connect.)

Installed Network Manager.  Reboot.  Network Manager only pops up "Wired Network" and doesn't recognize the WiFi card.  Little blue light is still on.  

Followed some more instructions in thread 367092 to go to Administration > Network and disable the card & reboot.  Sure enough, Wireless Networks now appears under Network Manager.  But it doesn't display any wireless networks to choose from.  (My Windows machine next to me sees it, so I know it's there.  Confirmed that the router is set to broadcast.)

Next I tried entering a new connection manually via Network Manager (connect to other wireless network & create new wireless network).  No joy - it just spins and then dies.

Tried to get things to connect via command line:
```
martz@martz-laptop:~$ sudo iwconfig wlan0 essid any  (also tried inputing the exact SSID)
martz@martz-laptop:~$ sudo iwconfig wlan0 key XXXXXXXXX (triple checked that it was correct)
```
No results to speak of.

Tried some recommendations in post 201902 and verified that things said wlan0 instead of eth1 in /etc/modprobe.d/ndiswrapper, etc/iftab (changed this one).  Tried 'connect to other wireless network' in Network Manager, but it failed again.
 
A few more bits of code:
```
martz@martz-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:23:73:51  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe23:7351/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25519 (24.9 KiB)  TX bytes:9257 (9.0 KiB)
          Interrupt:217 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:6F:48:BE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:c0204000-c0206000 
```


```
martz@martz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
martz@martz-laptop:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
```

```
martz@martz-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 5430
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:a5:6f:48:be
Sending on   LPF/wlan0/00:14:a5:6f:48:be
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 6240
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:36:23:73:51
Sending on   LPF/eth0/00:16:36:23:73:51
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:a5:6f:48:be
Sending on   LPF/wlan0/00:14:a5:6f:48:be
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:36:23:73:51
Sending on   LPF/eth0/00:16:36:23:73:51
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 32924 seconds.
```

```
martz@martz-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:23:73:51
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.109 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:217
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:6f:48:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.37 firmware=Broadcom,03/23/2006, 4.40.19.0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0204000-c0205fff irq:177
```


```
martz@martz-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
sit0      Interface doesn't support scanning.
```


Other stuff that tried and failed:
* fwcutter fried Ubunto completely.  Had to hard reboot, then reinstall.
* Installing wifi-radar hosed the system.  Little blue light disappeared, Administration > Network lost the wireless card.  Had to apt-get remove and reinstall ndiswrapper to get the blue light back.

Only other thing showing as wrong is the "siocgifflags error" no such device" up at the top right, next to where Network Manager is.

Also, ndiswrapper -l still shows (alternate driver: bcm43xx) despite my blacklisting it and doing sudo rmmod bcm43xx.  The posts I've read make it sound like that should no longer be the case.

What other info can I provide to those smarter (and more patient) than I before slitting my wrists and going back to Windoze?

---

### Post by handaxe on 2007-03-08
Ok, you have been through the wringer here...no specific advice except to try another route that has worked for some.

Assuming that you have driver & other hardware issues sorted out, you might try WICD as your manager of wireless connections. Under active development.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Deb install. Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption and unlike Network Manager does not require you to mess about with /etc/network/interfaces.

NB - ver 1.0.9 might give problems so use 1.0.7 for the mo'.

See how you fare...

HA

---

### Post by matthewartz on 2007-03-08
Do I need to do anything to Network Manager prior to install of WICD?  I'm guessing (since they both serve the same purpose) that they might not play nice together.

Thanks!
Matt

---

### Post by handaxe on 2007-03-08
Uninstalling NM would be a good idea - no biggie I guess.

HA

BTW, wicd may not auto-restart after suspend /hibernate.  Known problem being worked on - just run wicd or right click on the tray icon and choose connect.

---

### Post by matthewartz on 2007-03-08
Removed Network Manager and rebooted.  Still get the blue light.  

Installed WICD, which finds the wired network, but lists "no networks found" for the wireless.  Tried changing the preferences and it does have the right interfaces listed (wlan0 for wireless, eth0 for wired).  Tried switching the WPA Supplicant driver from wext to ndiswrapper and broadcom, but same result on refresh - no networks found.  

Groan.  I feel like I'm so close!:-k

---

### Post by matthewartz on 2007-03-08
Here's what bugs me.  Following all of the guidance in the [troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), the only thing that really comes back as odd is:
```
martz@martz-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

No errors, so I assume this means it's actually scanning, but just not finding anything??

Here's another weird thing:
```
martz@martz-laptop:~$ sudo iwconfig wlan0 essid Artz
martz@martz-laptop:~$ sudo iwconfig wlan0 ap 00:13:10:88:74:2B
martz@martz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Shouldn't the iwconfigs at the beginning have updated the details?  

At present, I have any and all wifi scanner gui's unsintalled (no Network Manager, no wifi- etc.), so there shouldn't be any weird conflicts there..

```
martz@martz-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5058
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:a5:6f:48:be
Sending on   LPF/wlan0/00:14:a5:6f:48:be
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Again, it looks like it's scanning and trying to get an IP, but can't.  I've tried static IP in place of DHCP, but it still won't connect.  I've tried making the wifi network open (no WEP, no WAP), but same result.

Anyone got any thoughts?

---

### Post by matthewartz on 2007-03-08
Hmmm....  one more thing tried (and failed):  I updated the ndiswrapper driver to change Afterburner to 0 instead of 1 (noted as a problem for Broadcom & Linksys communication in one of the community docs).  Alas, no joy.

The biggest conundrum at present is why iwconfig returns ESSID: off/any when both System > Administration > Networking and /etc/network/interfaces show it as Artz.

Something ain't right...

---

### Post by jml on 2007-03-08
I'm assuming that you are running 6.10.  Ubuntu installs a Broadcom driver that does not work very well and will prevent the successful use of ndiswrapper plus the Windows driver.  You need to blacklist the native driver first and then ndiswrapper should work.  Edit the file: etc/modprobe.d/blacklist by typing in "blacklist "your driver" which is the driver installed by Ubuntu.  Save the file, reboot and have another go at ndiswrapper.

Joe

---

### Post by matthewartz on 2007-03-08
Yep - been there, done that.  

I've double and triple checked that bcm43xx is blacklisted as well as done sudo rmmod bcm43xx.  

Any way it might not be recognizing the blacklist (e.g. still trying to use it, even though it's on the black list)?

---

### Post by handaxe on 2007-03-09
> **matthewartz said:**
> Here's what bugs me.  Following all of the guidance in the [troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), the only thing that really comes back as odd is:
```
martz@martz-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```No errors, so I assume this means it's actually scanning, but just not finding anything??


Hi,
Sorry for delay ... the above simply is not right, so yes, you have a (fundamental) problem. I would guess the card is in fact not scanning and that ndis is not working at all. (I assume this lappie dual boots and has no problem in Windoze)

If you want to make sure about the blacklist, rename the driver (the ones entered in the blacklist (/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/bcm43xx)) and see if it helps. That way it cannot load. I am mindful of what you wrote at first:

> Also, ndiswrapper -l still shows (alternate driver: bcm43xx) despite my blacklisting it and doing sudo rmmod bcm43xx. The posts I've read make it sound like that should no longer be the case.For comparison, here is my result, replacing wlan0 with eth1 ..

```
~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:18:39:D3:78:84
                    ESSID:"bohlinyates"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-52 dBm  Noise level=-52 dBm
                    Extra: Last beacon: 68ms ago

```Another (not really helpful) thing is, I wonder what the 32bit Ubuntu would be like?  Ie. is this a Ubuntu wide issue with your card, or a 64bit one?

I know how frustrating this must be.

HA

---

### Post by matthewartz on 2007-03-09
Okay, a new morning (for me anyway) and a fresh start.  

First, I renamed bcm43xx.ko to bcm43xx_backup, so there shouldn't be any way the system is still calling that.  (Thanks for the tip!)

Next, I uninstalled ndiswrapper:
- verified it's not installed per synaptic
- verified that there wasn't an apt-get install version floating around via apt-get remove
- did make uninstall via the download folder for ndiswrapper1.37
- confirmed it all by getting a nice error message "no such file or directory" when I entered ndiswrapper

Next, I reinstalled ndiswrapper-1.37
- make distclean
- make
- make install
- verified that there are NO drivers currently installed through ndiswrapper -l

I downloaded a bunch of different drivers from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) based on my card id 14e4:4318.  

Guess I'll play with different drivers and see if one works.

Also, saw a tip that this card sometimes doesn't work unless you set boot to noapic nolapic.  What's the easiest way to test that?

Thanks to any and all for the help.

---

### Post by handaxe on 2007-03-09
Hi,

Assuming you are dual booting and using grub, for permanent noapic etc, you edit /boot/grub/menu.lst (as root) and change the line I have marked **** to (note it will differ according to the kernel you are running (64bit for one thing):

```
/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro noapic nolapic splash
``````
title        Ubuntu, kernel 2.6.17-11-generic
root        (hd0,2)
****kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```As a temporary test you can simply highlight the kernel line when grub displays and press "e" for edit and then type in noapic etc as per the above.

HA

---

### Post by matthewartz on 2007-03-09
Many thanks to handaxe and jml for the morale support and tips.  ;-) 

I'm sending this message via my wireless which, at long last, is working.  I'll post a follow-on mail a bit later which outlines how I got it to work.  I want to play with the noapic/nolapic and see if that was really the issue or if it was an install order issue.  (After trying five different drivers, the one that I was originally using is the one that ended up working.)

---

### Post by matthewartz on 2007-03-09
Definitely the 'noapic' during boot that makes it work.  Tried to boot without that and I get the wifi card to come up, but it won't associate with anything.  The nolapic doesn't seem to be necessary however.

As a side note, Network Manager doesn't play well with the card.  Tried loading that up and lost my wireless connection.  Uninstalled, rebooted, and got it back.  wifi-radar does seem to work.

---

### Post by handaxe on 2007-03-09
Wonderful news - relish the delight:)

Wifi-radar or Wicd? I know you wrote wifi but wondered if you meant the other...

HA

---

### Post by matthewartz on 2007-03-09
Haven't had a chance to try wicd yet.  WiFi Radar does work.

---

