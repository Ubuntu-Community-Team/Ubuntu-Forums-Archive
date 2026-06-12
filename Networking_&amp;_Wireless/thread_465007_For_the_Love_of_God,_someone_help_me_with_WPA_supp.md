---
title: "For the Love of God, someone help me with WPA support for ubuntu feisty fawn"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by adasuper on 2007-06-05
HI,
 Please forgive me but, i quite frustrated right now. I've been trying to get my wireless network adapter to connect to a wpa enabled network but all attempts have become are futile. I use a DELL Inspiron 510m laptop with intergrated centrino wireless (IPW 2100). For some reason the network connection only provides me with the option to enter a WEP (either ascii or hex) but never wpa key. I upgraded from edgy to feisty (i heard feisty supports wpa 'out of the box' but alas..) I'm new to linux, i have tried downloading ndiswrapper and wps supplicant but i don't know how to install them. I ran this command 'sudo gedit /etc/network/interfaces' and made the following additions to it

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <i inserted my essid here>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <inserted my hex key here>

But still nothing has changed.  Please is there some application or a step by step solution out there? My windows partition is corrupted so i'm stuck with Linux and need to get some work done. Any help will be much appreciated.:((

---

### Post by kevdog on 2007-06-05
Have you installed the wpa_supplicant package??  This is a necessity.

---

### Post by adasuper on 2007-06-05
I ran the command 'sudo apt-get install wpasupplicant' here is the output

jan@jan-laptop:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic libgdk-pixbuf2 linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jan@jan-laptop:~$ 

I think that means its already installed and the latest version.

---

### Post by dmizer on 2007-06-05
have you checked the sticky thread at the top of this form about wireless security?

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) ... there are edits specifically for feisty in that thread.

---

### Post by adasuper on 2007-06-05
yes Dmizer, i have seen the link thats how i got the first set of codes that i included in my initial posting

---

### Post by kevdog on 2007-06-05
Before going on a wild goose chase, does your wireless connection work either with WEP or no encryption.  I just want to make sure that this is only a WPA problem, rather than another network problem in addition to WPA.

After making your changes to your interfaces file, did you restart the networking daemon??
sudo /etc/init.d/networking restart

---

### Post by adasuper on 2007-06-05
Yes the network is setup for WPA, as a test i was able to connect 2 other laptops running windows XP SP2 successfully.

---

### Post by kevdog on 2007-06-05
So everything works???

---

### Post by Lord Illidan on 2007-06-05
Try using wicd:

[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

---

### Post by adasuper on 2007-06-05
Sorry i forgot to mention that i restarted the daemon. It said something about NO DHCPOFFERS received. Unfortunately in my impatience i tried out something else in some website ([http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)) and now network manager says my network interface does not exist. I tried to undo what i did and restart the daemon again and i got the following output 

jan@jan-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 12098
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:12:3f:05:68:57
Sending on   LPF/eth0/00:12:3f:05:68:57
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 8192
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:66:c2:9b
Sending on   LPF/eth1/00:0c:f1:66:c2:9b
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:12:3f:05:68:57
Sending on   LPF/eth0/00:12:3f:05:68:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.5 -- renewal in 117450 seconds.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

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
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Segmentation fault (core dumped)
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:66:c2:9b
Sending on   LPF/eth1/00:0c:f1:66:c2:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
jan@jan-laptop:~$ 

and my network adapter no longer exists

---

### Post by adasuper on 2007-06-05
sorry for all the stress i'm putting you all through. The wireless wpa network works with winxp but not on my ubuntu laptop

---

### Post by kevdog on 2007-06-05
Posting an output like this really doesnt help me.  

#1. Be more specific in what you did.  What is the name of your interface (eth0, wlan0)?? Does /etc/iftab accurately tell you the name of your adapter???

#2. Does your computer connect properly if all encryption in the router is turned OFF???  Can you get and obtain and unencrypted connection.

#3.  If you get serious errors like you posted above, oftentimes a reboot may be the best thing.

---

### Post by Lord Illidan on 2007-06-05
Again, try wicd, I had the same problems on my father's laptop with Feisty Fawn, wicd works perfectly with WPA. In my case, we use WPA2.

---

### Post by adasuper on 2007-06-05
Ok

The router is on right now and is set to work with WPA  encryption, the passpharase and everything else is setup and running. I have the connection with 2 laptops running win xp and they have both connected to the wireless network.

Right now i have connected directly to the router with a network cable. The interface for the wired network card is eth0 and for the wireless eth1. I have been using the laptop with WEP but just changed broadband providers and the wireless box that came implements WPA.

I tried to install ndiswrapper and wpasupplicant last night but i didn't know what to do with the "tar files" 
This morning beofore i made the initial posting this is what i did

STEP 1.  "sudo apt-get install wpasupplicant " and it produced the following output

jan@jan-laptop:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic libgdk-pixbuf2 linux-headers-2.6.20-15
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

STEP 2. "sudo gedit /etc/network/interfaces" and edited it to look like this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface eth1 inet dhcp
wireless-essid SKY50877

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <i put ssid here>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <i put the hex key here>
auto eth1

STEP 3. "sudo /etc/init.d/networking restart" and there was no change to the network manager, i still could not input a WPA key.

After that i put in my first post.

I will take your advice kevdog and reboot and see. Thank you very much i'm trying to avoid making a long post, do you want me to list what i did to make "the interface not exist"?

---

### Post by adasuper on 2007-06-05
I have rebooted now and the interface now exists:D but it still just asks me to enter a WEP key

---

### Post by Lord Illidan on 2007-06-05
> **adasuper said:**
> I have rebooted now and the interface now exists:D but it still just asks me to enter a WEP key

Wicd works better with WPA connections, why don't you try it out?

---

### Post by kevdog on 2007-06-05
OK, Im getting very frustrated, since I dont think you are telling me the whole story.

Your laptop, or computer has two ethernet connections -- a wired and wireless.  This is what I glean so far

The wired connection works.
The wireless connection does not.

I dont know what your ultimate goal is meaning:
1. Do you just want to use the wired connection eth0?
2. Do you need the wireless connection -- it seems very obvious that you do not have ndiswrapper installed since you told me that you didnt know what to do with the tar files.  The tar files are simply source files.  These files need to be compiled and then installed.
3. Do you know the WPA details about the router -- ie WPA1 or WPA2, personal shared key, or enterprise??  Can you log into the router and see the details??  I find it very unusual that you couldnt turn the WPA encryption off at least for a short time, until we can verify things and then turn it on later.

My own personal strategy in trying to get ethernet connections.  
1. Turn off all firewalls on computer, and all mac filtering and encryption on router
2. Install driver for network card on computer (this is the most difficult thing)  This entails ndiswrapper installation.
3. Configure driver and then make sure connection is viable
4. Then install and configure for WPA
5. Make final changes to /etc/network/interfaces file if needed to allow for WPA, and or static IP if necessary.

I dont care about your two xp computers at least right now.  If you need to configure samba so you can connect to the computers, this is a whole different story.

ndiswrapper is really intended for wireless cards although I suppose it could work with wired ethernet cards although Ive never used it as such.  Here is the first thing from the ndiswrapper website:
> 
Many vendors do not release specifications of the hardware or provide a Linux driver for their wireless network cards. This project implements Windows kernel API and NDIS (Network Driver Interface Specification) API within Linux kernel. A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in Windows, without binary emulation.
 
 With ndiswrapper, most miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network cards work in Linux with x86 or x86-64. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., ethernet cards, USB to serial port device, home phone network device etc. 


Please answer the questions above so I can help you.  The last few posts you havent really told me anything.

---

### Post by adasuper on 2007-06-05
My goal is to use the wireless connection eth1, i'm connected to the router directly  via wired ethernet eth0 as this is the only way i can get on the internet. I only mentioned the Winxp because you wanted me to confirm if the network was up and running. 

The router is using WPA1 with TKIP and a pre shared key and i have the passphrase which i used the command wpa_passphrase to generate the hex key.

I didn't think of logging into the router to change anything because it worked straight away fior the other 2 laptop on win xp (which i only entered the WPA key). 

The basic thing is that whenever i right click the icon for the wireless connection here on ubuntu. It shows me options:

1 properties
2 help
3 about
... etc

when i click on properties and configure
 i can enter the essid but the where it says "password type" it only gives me options for WEP(hex or ASCII). 

I was using this laptop with the same OS (ubuntu feisty) with a WEP enabled router but have when we changed  broadband providers the new router came with WPA.  

I just tried installing Wcid, i had to uninstall network-manager and restart and the wireless connection is working now.!!:D

Thanks soooooo much for your time :D

---

### Post by Lord Illidan on 2007-06-05
I found I had the same problem with network-manager on my dad's pc, and wicd solved it. Glad it did the same for you.

---

### Post by kevdog on 2007-06-05
Not trying to knock wicd -- I looked at it and it seemed very simple for WPA access, which it seems many users have confirmed.  My only problem with this package is to my knowledge it does not allow for the use of static IP addresses. If it did, I would have ditched network-manager a long time ago!

---

### Post by wieman01 on 2007-06-06
Problem seems to be resolved, but remember to always remove the Ethernet cable before you attempt to connect via wireless. In Linux you cannot have 2 connections at a time to the same network.

---

### Post by compwiz18 on 2007-06-06
Wicd does support static IPs.

---

### Post by disrupta on 2007-07-05
thanks 
i had no wpa access with feisty and have spent hours on it. network manager removed easily and WICD wicd solved my problem and connected for me. it has an option to enter your password and wpa access. if its not mentioned already. have a look at this site 

[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

it has a guide on how to set up wicd. i think this could help lots of people trying to connect feisty ubuntu with wpa access. it was absolutely essential reading for me. thanks for this. i hope it helps many more people who read this forum. 

but i  can confirm that wicd is an excellent answer.

---

### Post by walkerk on 2007-07-05
> **disrupta said:**
> thanks 
i had no wpa access with feisty and have spent hours on it. network manager removed easily and WICD wicd solved my problem and connected for me. it has an option to enter your password and wpa access. if its not mentioned already. have a look at this site 

[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

it has a guide on how to set up wicd. i think this could help lots of people trying to connect feisty ubuntu with wpa access. it was absolutely essential reading for me. thanks for this. i hope it helps many more people who read this forum. 

but i  can confirm that wicd is an excellent answer.
agreed. wicd is a great and simple method of connection wifi w/ wpa1/2.. a lot nicer than network-manager imo.

---

### Post by technomom on 2007-07-05
Yes, for the love of God, someone put WICD in a sticky note at the top of this forum.  

I was about to trash my Ubuntu CD until I saw this post answer.     Could not connect my Thinkpad T42 to my Linksys Router with WPA using network-manager.   Downloaded WICD and had it running in about 30 seconds.

---

### Post by walkerk on 2007-07-05
> **technomom said:**
> Yes, for the love of God, someone put WICD in a sticky note at the top of this forum.  

I was about to trash my Ubuntu CD until I saw this post answer.     Could not connect my Thinkpad T42 to my Linksys Router with WPA using network-manager.   Downloaded WICD and had it running in about 30 seconds.

Good to hear. Im a huge supporter of wicd and wifi-radar (though wifi-radar took a bit of work..)

wicd improved upon wifi-radar.. both blow network-manager away.. imo

---

