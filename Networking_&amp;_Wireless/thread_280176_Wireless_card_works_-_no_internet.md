---
title: "Wireless card works - no internet"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by somersetsimon on 2006-10-19
This is my first week with Linux and Ubuntu and I'm stumped by wireless networking. I managed to correctly install the zd1211b driver for my USB wireless adaptor (I think). The device appears to be working ok. I have a router on my wireless network (192.168.1.1) that has all protection switched off. No MAC filtering, no encryption. The SSID is B####Net broadcasting on Channel 10 and it is enabled as a DHCP server. XP on the same machine connects perfectly, but Ubuntu won't let me connect to the internet or my existing network. I've tried lots of suggestions I've seen on the forum, but haven't managed to get anywhere.

iwlist gives...

simon@linux1:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:0D:54:F9:16:73
                    ESSID:"B####Net"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Extra:SignalStrength=38%,LinkQuality:96%
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

So it looks like the device can see my wireless network.

 iwconfig gives...

simon@linux1:~$ sudo iwconfig wlan0
Password:
wlan0     802.11b/g NIC  ESSID:"B####Net"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=92/100  Signal level=52/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:8
          Tx excessive retries:224123  Invalid misc:0   Missed beacon:0

The 'Not-Associated' bit doesn't look too good. 

dhclient gives...


simon@linux1:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:02:72:56:58:79
Sending on   LPF/wlan0/00:02:72:56:58:79
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I tried putting in a sensible fixed ip address instead of dhcp (192.168.1.10), but that didn't work either. What else should I be doing to get on to the network? I'm a bit confused by all the settings in the Network utility. E.g. what should I be putting in the boxes for:

General - Hostname & Domain Name
DNS - DNS servers
Hosts 

Under the hosts section there is an entry for my machine name, also with an alias of 'localhost', with an ip address of 127.0.0.1. I tried changing that to 192.168.1.10 to be the same as the fixed IP address I gave earlier, but that didn't help.


Any suggestions would be appreciated

Thanks

Simon

---

### Post by somersetsimon on 2006-10-19
Any suggestions? I've seen a couple of other posts that have the same problem. I.e. Ubuntu appears to 'see' the wireless network, but can't connect to it. Can anyone help? Please?

---

### Post by somersetsimon on 2006-10-20
Still nobody to help?
Looking at other threads here I installed Network Manager from the alternate install CD. When it runs I just get an icon in the corner of the screen with two little screens. When I right-click it just says there is no network connection, so I can't do anything with it. How is network manager supposed to help in setting up a wireless network?

---

### Post by gnomer_ on 2006-10-20
What chipset?

---

### Post by dannyboy79 on 2006-10-20
what does ifconfig tell you? have you tried sudo ifup interfacehere, example would be "sudo ifup ath0". i have seen a lot of this issue lately, have you tried disabling ipv6 in firefox and also, what about installing wifi-radar and using a gui to see if you can connect to your access point. sudo aptitude install wifi-radar. if that's not the exact title, then to find it out do, sudo aptitude search wifi. then whatever looks closest to wifi-radar, install it. then look for it in the menu under networking. i used to use it, it worked great.

---

### Post by jstueve on 2006-10-20
if you are trying to use network-manager can we see the results of 

```
cat /etc/network/interfaces
```

For network-manager to work, you need to have the interfaces that you want to work using network manager not listed in /etc/network/interfaces  if they are listed there, then network-manager will leave them alone, thus reporting the 'no interfaces available'

see [here](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
especially:
> Configuring Devices

Devices which are automatically configured on boot will not be available in NetworkManager. To allow network manager to use all of your devices remove instances of auto in /etc/network/interfaces. (apart from the "auto lo" line, which is needed for the loopback interface) **Backup the file and remove everything or ad a:"#" for each line of the file except for:**

auto lo
iface lo inet loopback

Save and reboot. 

---

### Post by dbott67 on 2006-10-20
Hi Simon,

The fact that you can see the AP is good, the bad part is that the signal strength is a little on the low side when it comes to obtaining an IP (not bad if you're already connected, but I've found that getting as close as possible is the best option when trying to troubleshoot).

127.0.0.1 is the 'local loopback' address and is required.  It's a way for the computer to communicate with itself via the network.  So you should return it to its previous value.

Okay, in order, please try the following:

1. Move closer to the AP.

Issue the following commands:

```
sudo ifdown wlan0
```
```
sudo ifup wlan0
```
```
sudo iwlist wlan0 scanning
```
```
sudo dhclient wlan0
```

Post the output here if you're still unable to connect.

2. Reset your router (they are just little dedicated application servers & sometimes things like DHCP can hang).  A reboot might cure it.

3. Upgrade the firmware of your router.  Again, sometimes these things get a little flaky (even when they worked perfectly yesterday or with other OSes).

Keep me posted.

As mentioned above, if you could also post the output of **cat /etc/network/interfaces**.  You should see something like:

```
dbott@dapper:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott   [COLOR="Red"]<--- this will be your ESSID[/COLOR]
wireless-key s:secretWEPkey1   [COLOR="Red"]<--- you won't see this part[/COLOR]
dbott@dapper:~$
```

-Dave

---

### Post by jstueve on 2006-10-20
if you are using network-manager and want it to work it would look more like:

```

#auto wlan0
#iface wlan0 inet dhcp

```

(yes, they are edited out... if you want to test using the ifup and ifdown, then the uncommented above as per -Dave would work fine.)

---

### Post by MightyMouse on 2006-10-20
Hi,
might sound strange, but I had the same problem with another wirelss USB adapter. The rather simple step after having figured out that the device was working and could find almost any network in the neighbourhood except mine was to change the channel! My AP was on channel12, now it's on 4 and suddenly I could see the light!

It's worth a try.

Anja

---

### Post by somersetsimon on 2006-10-20
I didn't realise that this stuff will have to be commented out! I'll do that and report back. I have a feeling that the rest of the weekend will be taken up with family stuff, so I might not get much of a chance to experiment :-)

---

### Post by somersetsimon on 2006-10-20
Thanks for the advice. I think most of the info you suggested is in my original post. Moving the pc and the router physically closer together is a bit of a pain, also everything works fine with XP on the same machine in the same location.

---

### Post by somersetsimon on 2006-10-21
I edited those lines out, rebooted, and network manager still didn't do anything - just said No Network

---

### Post by dannyboy79 on 2006-10-21
and what about trying wifi-radar. you have nothing to lose by trying.

---

### Post by somersetsimon on 2006-10-22
That's the next step. The only problem is that this means I need to connect to the internet to download it! I have an ethernet connection that works in XP and did work with a Kubuntu Live CD a few weeks ago. The only problem is that I need to carry the PC into a different room to connect it. This needs to wait until the kids are in bed!

My problem seems to be that the wireless card is active, it can see my wireless network, but it can't connect to the network. Does wi-fi radar help with this? Also, for network manager, I had to remove the wlan0 entry from my interfaces file. Do I need to do this for wi-fi radar?

---

### Post by dannyboy79 on 2006-10-22
> **somersetsimon said:**
> That's the next step. The only problem is that this means I need to connect to the internet to download it! I have an ethernet connection that works in XP and did work with a Kubuntu Live CD a few weeks ago. The only problem is that I need to carry the PC into a different room to connect it. This needs to wait until the kids are in bed!

My problem seems to be that the wireless card is active, it can see my wireless network, but it can't connect to the network. Does wi-fi radar help with this? Also, for network manager, I had to remove the wlan0 entry from my interfaces file. Do I need to do this for wi-fi radar?

well, I think that it WON'T help you connect better unfortunately but what it helped me with was keeping several different access points and their security settings. it allows me to see the variuous access point and try to connect to them. i would suggest downloading the wifi-radar.deb on your winxp machine or using a live cd if that works, then put it on a floppy or usb drive then simply copy the .deb from the disk or wherever then paste it on your desktop then double click it and it'll install. you should have all t he dependencies because I was able to install it on xubuntu and all the dependencies were in that install. i wish I could help more. good luck

---

### Post by somersetsimon on 2006-10-22
I may be getting somewhere. I installed wi-fi radar and ran it. My SSID was on the drop-down menu, so I selected that and configured the connection. It acquired an IP address. Looking good! The IP address was the same as the one that XP finds on the same machine.

Unfortunately I still couldn't connect to anything. I tried Firefox, but couldn't get to the internet. I tried entering 192.168.1.1 (my router IP address) in Firefox, but couldn't connect to that either. What else could I try?

---

### Post by wieman01 on 2006-10-23
> **somersetsimon said:**
> I may be getting somewhere. I installed wi-fi radar and ran it. My SSID was on the drop-down menu, so I selected that and configured the connection. It acquired an IP address. Looking good! The IP address was the same as the one that XP finds on the same machine.

Unfortunately I still couldn't connect to anything. I tried Firefox, but couldn't get to the internet. I tried entering 192.168.1.1 (my router IP address) in Firefox, but couldn't connect to that either. What else could I try?
What does this say?
> route
I suspect that you are connect, however, you may have to disable IPV6. And can you ping your router?
> ping 192.168.1.1

---

### Post by MegaTroopX on 2006-11-03
I'm having a problem too. I have a dual-boot system, XP on one drive, Ubuntu Dapper on the other. I have a Linksys WUSB54G, which operates fine in XP, but when I boot Ubuntu and try to connect with WiFi Radar, the router shows up at 0 strength, and will not give me an IP address. It's kind of a problem.

---

### Post by wieman01 on 2006-11-03
> **MegaTroopX said:**
> I'm having a problem too. I have a dual-boot system, XP on one drive, Ubuntu Dapper on the other. I have a Linksys WUSB54G, which operates fine in XP, but when I boot Ubuntu and try to connect with WiFi Radar, the router shows up at 0 strength, and will not give me an IP address. It's kind of a problem.
WUSB54G is a piece of cake, mate. :-) No, honestly, I have got one & am using "ndiswrapper" to get it working. Wanna try?

---

### Post by wieman01 on 2006-11-03
Mini-howto:

1. Install "ndiswrapper":
> sudo apt-get install ndiswrapper-utils
2. Open "blacklist" file:
> sudo gedit /etc/modprobe.d/blacklist
3. Add this line & save:
> blacklist rt2570
4. Get the latest(!) Windows driver for your card.

5. Copy the driver files (*.sys, *.inf, etc.) to your home folder:
> /home/[COLOR="Red"]your_user[/COLOR]/WUSB54GV4
6. Install Windows driver:
> sudo ndiswrapper -i /home/[COLOR="Red"]your_user[/COLOR]/WUSB54GV4/rt2500usb.inf
7. Check if driver has installed correctly:
> ndiswrapper -l
8. Load new driver module (may not be necessary):
> sudo depmod -a
sudo modprobe ndiswrapper
9. Loading module at startup:
> sudo ndiswrapper -m
10. Restart computer & scan for networks:
> iwlist scan
[COLOR="Blue"][Please post the results...][/COLOR]

---

### Post by OwenA on 2006-11-11
I tried to install ndiswrapper as you put it:

sudo apt-get install ndiswrapper-utils 

I get error that E: COuldn't find package ndiswrapper-utils????

---

### Post by somersetsimon on 2006-11-11
> **OwenA said:**
> I tried to install ndiswrapper as you put it:

sudo apt-get install ndiswrapper-utils 

I get error that E: COuldn't find package ndiswrapper-utils????

I extracted all the ndiswrapper stuff from the CD using synaptic. You can see all the ndiswrapper info that you need to select.

---

### Post by OwenA on 2006-11-11
OK.. did that. Went thru all the commands wie put down. When I went to test by typing ndiswrapper -l I got a rt2500usb invalid driver???

I wasn't suppose to execute the setup.exe for the linksys was I?

---

### Post by wieman01 on 2006-11-11
> **OwenA said:**
> OK.. did that. Went thru all the commands wie put down. When I went to test by typing ndiswrapper -l I got a rt2500usb invalid driver???

I wasn't suppose to execute the setup.exe for the linksys was I?
You probably have installed the wrong driver.

1. What card have you got (also mention the version number)?
2. The .EXE file is a zip archive that contains the driver file. Unzip it and put the files (*.INF, *.CAT, *.SYS, etc.) here:
> unzip [COLOR="Red"]your_driver_archive.exe[/COLOR] /home/your_user/WUSB54GV4
Alternatively you can open the .EXE file with Winzip or any other Zip-Tool. Just make sure that **_all_** driver files are in the mentioned folder. We go ahead from there.

---

### Post by OwenA on 2006-11-12
I have the Linksys WUSB54G version 4. I downloaded directly from Linksys thier latest drivers for this USB adapter as Wie instructed. I directed the commands to that file and it says invalid file.

---

### Post by OwenA on 2006-11-12
When I do the iwlist scan I see 4 access points my WIndows PC sees as well. So the device is somewhat working. I just need to figure out why when I do the following 2 things I have issues:

1. When I type sudo modprobe ndiswrapper I get FATAL error inserting ndiswrapper.

2. When I type ndiswrappers -l I get invalid driver.

---

### Post by OwenA on 2006-11-12
I tried reinstalling Ubuntu to see if that would make a difference. IT did not.

I went through all the steps and copied in the WUSB54GV4 folder the sys, cat and inf files. I ran the commande sudo ndiswrapper -i /home/owen/WUSB54GV4/rt2500usb.inf and it said rt2500usb is already installed. When I type ndiswrapper -l it says invalid driver.

SO I am confused as to why it says it is installed but then invalid driver.

---

### Post by wieman01 on 2006-11-13
Try to remove ndiswrapper completely using Synaptic and then reinstall it. It seems you may have install the wrong file in the first place. This should definitely work, I have a WUSB54G V4 as well. No issues with it. 

Make sure it really say V4 on the back of the device, then go through the procedure once again. Are there any other driver files that you should copy to the mentioned folder?

---

### Post by OwenA on 2006-11-13
There are 2 versions od ndiswrapper. ANyone know which is the right version?

As for any other files being in folder...I am assuming it should be only those 3 which are a sys, cat and inf files.

---

### Post by OwenA on 2006-11-13
Wie,

I am very new Ubuntu. I wonder if I am not doing something right. I followed all the directions, but maybe there is one step I missed. This is not a simple OS as we see with all the questions. Maybe what I am forgetting is something simple that experienced users take for granted???

---

### Post by wieman01 on 2006-11-13
Hi Owen, 

You may be right... Can you post all the commands you have used and also validate that the version number of your driver is right? Please include a link to website from which you have downloaded it.

We'll do this step by step then... No problem.

---

