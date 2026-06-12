---
title: "At wits end with wireless"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Doug11 on 2006-11-16
Hello all, I must say I'm relativley a noob to the world of linux. I have done most of my experimenting with Suse10 but with a new notebook, I find it wont detect any hardware what so ever. So I heard about Ubuntu so I just got the new release? Edgy? Anyway,,here's my situation,,my wired connection worked from the get-go. Not a prob. BUT, after about 5 days of reading the forums trying to get my wireless up, I've done two fresh installs and manged to get my radio working with the ndiswrapper. My wireless light is now and configured with the correct WEP key the best to my knowledge. In the kwifi manager, it shows the sig stregnth. I would post a screenshot but I'm not quite sure how its done. When I go to Sys>Admin>Networking,,,My wireless is enabled and ready to go. When I use this command:  sudo gedit /etc/network/interfaces
this is the result I get,,with the x's being my proper wep key.

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid default
address 192.168.0.1
netmask 255.255.255.0
wireless-key xxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Don't know if there is anything else I'm missing.
My machine is an Acer Aspire. D-Link router. Any help or tips would be greatly appreciated.

---

### Post by linuxgrrl on 2006-11-16
hi,
Not sure if this is your problem, but with Breezy I had to disable eth0 in /etc/interfaces in order to get the wireless to work properly.  This was done by commenting out the "eth0" lines in /etc/network/interfaces.  I wasn't using ndiswrapper tho', so as I say, not sure if this will help you.

If the signal strength is showing up but you can't connect to the net, I wonder if dhcp setup is the problem.  Can you ping a public server by its address (like 4.2.2.2?) What results if you do "sudo dhclient wlan0" or "sudo dhclient eth1"?  

Final thought: if you can get the wireless to work on its own, there is a link here [http://www.linuxquestions.org/questions/showthread.php?t=107313](http://www.linuxquestions.org/questions/showthread.php?t=107313)
with one way to have the wired and wireless coexist.

Anyway, I have not tried any of this since Breezy but I hope it is of some use to you in narrowing the problem.

---

### Post by FrodoB on 2006-11-16
I have a device that insists on changing the name wireless-key to wireless-key1 on ndiswrapper. Edit the file and change it to:

wireless-key1 xxxxxxxxxx

save it.

Then try:

sudo ifdown eth1

then

sudo ifup eth1

It is worth a try.

---

### Post by Doug11 on 2006-11-16
This is what i get when i try the first command


sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


as far as the second command,,have these results:

 sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:ce:32:fd:d6
Sending on   LPF/eth1/00:16:ce:32:fd:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Ran into some probs,,i changed a few network settings,,tried to reboot and just hung on the brown screen,,,I had to press the button to disable my radio,,it booted back up and is working fine,,still now connection though.

---

### Post by FrodoB on 2006-11-16
Well you have some mutually exclusive stuff in your interfaces file:

iface eth1 inet dhcp
wireless-essid default
address 192.168.0.1
netmask 255.255.255.0
wireless-key xxxxxxxxxx

should only be:

iface eth1 inet dhcp
wireless-essid default
wireless-key xxxxxxxxxx
auto eth1           

I would move the auto eth1 from wherever it is in the file to just below the wireless-key to keep them together.

If this does not seem to work the add wireless-key1 with the exact same wep key. If that works you do not need plain wireless-key xxxxxxxxxx at all.

iface eth1 inet dhcp
wireless-essid default
wireless-key xxxxxxxxxx
wireless-key1 xxxxxxxxxx
auto eth1 

If none of this works then provide the output from iwconfig.

---

### Post by Doug11 on 2006-11-17
Why is it the only way I can run this command is if I have uninstalled my Network Manager. Also, when i have network manager installed, how do i access it?


sudo gedit /etc/network/interfaces

---

### Post by Doug11 on 2006-11-17
I ran the iwconfig,,,these are the results



lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by FrodoB on 2006-11-17
If you run Network Manager it will be a tiny icon in the upper right hand side of the top toolbar close to the speaker control icon.

I think that you need to get things running without worrying about Network manager for the moment.  Once it works then you can use it.  

The first thing to do is to fix the problem in the interfaces file where you are invoking dhcp and also a static address.

So after fixing it you should supply a fresh copy of the interfaces file along with the output from iwconfig and netstat. 

You also need to supply the output of lsusb or lspci that shows your device in it.

---

### Post by Doug11 on 2006-11-17
I think this error may have something to do with it??

doug@doug-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

Something wrong here?

---

### Post by FrodoB on 2006-11-17
Yes, do a search on your device on the forums.

---

### Post by Doug11 on 2006-11-18
Sorry guys,,I must edit my first post,,my wifi manager does not show sig strength,,I think that the problem is that the radio will not pick up the router. This shows that my driver is here and installed but I still get the module error as nit being present.



doug@doug-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

doug@doug-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present
doug@doug-laptop:~$


This is my /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper


It seems I could be missing one simple little thing.

OPTION 2--Is there a little more user friendly Linux distro for beginners?

---

### Post by Doug11 on 2006-11-21
Well, after a few more days of head scratching, I installed S=SE and got it working relativley quickly. So I reinstalled Ubuntu and tried a few things that seemed to work in the other distro. The Only different things I did this time was 1. I did NOT install Network Manager or Wifi radar ( or whatever its called) and 2. I completely Disabled my eth0 connection  (wired connection) and had it all up and running within 5 minutes of installation. Thanks to all that helped.

---

### Post by FrodoB on 2006-11-21
So it is working and reinstalling without Network Manager and WiFi Radar solved it?

---

### Post by Doug11 on 2006-11-21
Yes, it picks up my wired connection automatically, so as soon as i found the page with a pretty good howto of the codes, I unhooked it and disabled it in network settings. Then all I did was install ndiswrapper and my bcmwl5.inf file, went into Network settings and enabled it with right settings, made sure my wired connection was disabled and Voila. No oter apps were installed.

---

### Post by FrodoB on 2006-11-21
Could you please document the exact model of bcm43xx that you are using and let us know where you got the drivers that worked for you?

Thanks,

FrodoB

---

### Post by Doug11 on 2006-11-21
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


The driver I found was from the Acer support site under downloads>drivers. pick your model and then take the bcmwl5.inf file and install it with ndiswrapper.

I double checked, I have 0 (zero) of the three network managers installed.
Only network tools. Hope this helps some.

---

### Post by FrodoB on 2006-11-23
Doug;

Can you give a more exact link to the NDIS files that worked? Someone else it trying to get this device working.

See:

[http://www.ubuntuforums.org/showthread.php?t=305369](http://www.ubuntuforums.org/showthread.php?t=305369)

---

