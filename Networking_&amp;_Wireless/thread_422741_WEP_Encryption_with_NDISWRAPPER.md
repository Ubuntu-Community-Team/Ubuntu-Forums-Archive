---
title: "WEP Encryption with NDISWRAPPER"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by ianb72 on 2007-04-25
I have installed a Linksys WUSB11b v4 wireless network adapter using NDISWRAPPER and the windows <WUSB11v4.inf> driver in Fiesty.

But when I enable WEP encryption on my router and on the wireless adapter,the apdater will not connect to my router, I have restarted the router and the pc but still no joy!

I have checked the wireless adapdater is installed and working in /etc/network/interfaces

Here are the results

[HTML] auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp












iface wlan0 inet dhcp
wireless-essid BARDELLS

auto wlan0
[/HTML]

Then I did this:

[HTML] ian@ian-desktop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:91:8F:F2
                    ESSID:"BARDELLS"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:49:A0:28:04
                    ESSID:"ZyXEL"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:0F:3D:B9:2B:54
                    ESSID:"HomeNetwork_J"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 04 - Address: 00:11:50:AD:1E:CA
                    ESSID:"David"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

ian@ian-desktop:~$ [/HTML]

So it all works WITHOUT any WEP Encryption!! 

Has anyone got any ideas how I can set it up to have the WEP encryption on as there are several wireless networks in my area and I do not want to share my broadband with anyone else!

Many Thanks
Ian

---

### Post by wieman01 on 2007-04-25
Ok, try this instead (simply overwrite the current settings in "/etc/network/interfaces"):
>  auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BARDELLS
wireless-key **[COLOR="Blue"]YOUR_HEX_WEP_KEY[/COLOR]**
**[COLOR="Blue"]YOUR_HEX_WEP_KEY[/COLOR]** stands for the hexadecimal key (i.e. your password) that your router has translated from plain text into hexadecimal.

Alternatively you can enter your plain text password this way:
>  auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BARDELLS
wireless-key **[COLOR="Red"]s:[/COLOR]**[COLOR="Blue"]YOUR_PLAIN_TEXT_PASSWORD[/COLOR]
Then restart the network:
> sudo /etc/init.d/networking restart
What's the output?

---

### Post by dbott67 on 2007-04-25
EDIT: oops! beaten to the punch... do what Wieman01 said!

You're missing the WEP key in your interfaces file:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid BARDELLS
[COLOR=Red]wireless-key s:your-ascii-key

[/COLOR]
```-Dave

---

### Post by ianb72 on 2007-04-25
ok when I do that it doesn't connect even if I reset the router
Here are the results you asked for
[HTML] ian@ian-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 7949
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:97:84:bb
Sending on   LPF/wlan0/00:12:17:97:84:bb
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
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
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:97:84:bb
Sending on   LPF/wlan0/00:12:17:97:84:bb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
ian@ian-desktop:~$ 


[/HTML]

Ian

---

### Post by wieman01 on 2007-04-25
First off, remove all other lines from "/etc/network/interfaces"... the file needs to contain only what Dbott67 and I have posted. Second, please remove the Ethernet cable as you cannot have 2 connections at a time. Then restart the computer.

Any results?

---

### Post by wieman01 on 2007-04-25
> **dbott67 said:**
> EDIT: oops! beaten to the punch... do what Wieman01 said!

You're missing the WEP key in your interfaces file:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid BARDELLS
[COLOR=Red]wireless-key s:your-ascii-key

[/COLOR]
```-Dave
No prob, Dave. Next time then. :-)

---

### Post by itsmeagain on 2007-04-25
Hi
Had the same problem in Feisty as yourself, without  WEP I could get an internet connection, with WEP enabled no joy.  Worked on it for hours and now it works perfectly. See my notes on what I did, maybe you should try it

Ubuntu Feisty 
Wireless Card Set-up Instructions using ndiswrapper

Hardware / software used...
Wifi card ref:  Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02) 
ndiswrapper version:  ndiswrapper-1.42.tar.gz
Windows driver files needed: WMP11V27.inf and WMP11V27.sys

The first step in setting up the wireless card is to have the wireless router with the following settings, this is only a temporary situation, WEP will be Enabled later
ESSID: Your essid (network name)
WEP: Disabled
Mode: Set to Managed
Channel: Write down the channel number used
Security: Set to Open

{a}.  Disabling the Ubuntu native Windows wireless driver
The native wireless driver supplied with Ubuntu Feisty (bcm43xx) does not work with the above wireless card, so it needs to be  disabled. Two actions are required.

1. Disabling bcm43xx driver...
Open a Terminal by going to Applications > Accessories > Terminal
Code:
sudo rmmod bcm43xx
Input the root password if prompted 

2. Editing the blacklist file...
Code:
sudo gedit /etc/modprobe.d/blacklist
Actions... Add to the bottom of the file “blacklist bcm43xx” > Save the file and close the window

{b}. Installing ndiswrapper...
To install ndiswrapper we need firstly to have two programs installed in Ubuntu,,  “kernel-headers”and “build-essential”. Luckily the “kernel-headers” are installed by default so we only need to install “build-essential”

Installing “build essential”...
Insert the Ubuntu installation CD > in the windows that opens click on “Start package manager” > this opens the “Synaptic Package Manager” window > in the Search window type in “build-essential” > Search > you will see the “build-essential” program > mark it for installation and then install it > once installed close Synaptic Package Manager

Installing ndiswrapper...
Open a Terminal window > cd to the folder that contains ndiswrapper-1.42.tar.gz
Code:
tar xvfz ndiswrapper-1.42.tar.gz
This will create a folder named “ndiswrapper-1.42”, cd to this folder
Code:
make
Note: The make command will take a few moments, also no errors should be seen
Code:
sudo make install
Input the root password if prompted

Installing the Windows driver {WMP11V27.inf}...
Using a Terminal cd to the folder where the file “WMP11V27.inf “ is located
Code:
sudo ndiswrapper -i WMP11V27.inf	
		
To list drivers installed...
Code:
sudo ndiswrapper -l					
report...
wmp11v27 : driver installed
	device  (14E4: 4301) present (alternative  driver : bcm43xx)

Update modules...
Code: 
sudo depmod -a

Test ndis modlule...
Code: 
sudo modprobe ndiswrapper

Initiate ndiswrapper as a system start-up module...
sudo ndiswrapper -m
report...
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

Modifying some files...
From a Terminal window
Code:
sudo gedit /etc/iftab
report...
# This file assigns persistent names to network interfaces. 
# See iftab(5) for syntax. 

eth0 mac 00:08:c7:ca:91:ff arp 1
eth1 mac 00:06:25:1c:f3:d6 arp 1

Change this file as shown below, then File > Save ***... (iftab) > Save > Replace > close the window

# This file assigns persistent names to network interfaces. 
# See iftab(5) for syntax. 
eth0 mac 00:08:c7:ca:91:ff arp 1
wlan0 mac 00:06:25:1c:f3:d6 arp1
Notes: 
“wlan0 mac 00:06:25:1c:f3:d6 arp1” is the Linksys wireless card mac address










Code:
sudo gedit /etc/modules
report...
# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 
fuse 
lp


Change this file as shown below then File > Save ***... (modules) > Save > Replace > close the window

# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
ndiswrapper


Code:
sudo gedit /etc/modprobe.d/ndiswrapper
Report...
alias wlan0 ndiswrapper
Note:
This file should be as above and should not need modifying

Reboot the machine



Setting up the Network...
Go to System > Administration > Network > input the root password if prompted > click on Wireless Connection > Properties > set the following...
Remove the tick from “Enable roaming mode
Network Name (ESSID): Input your ESSID (network name) 
Configuration: to Automatic configuration (DHCP)  
OK > Close

Check one more file, it should look like below...
Code:
sudo gedit /etc/network/interfaces
Report...
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp  

auto wlan0 
iface wlan0 inet dhcp 
wireless-essid “YOUR ESSID”

The internet should now work

Setting up WEP security
Firstly “Network Manager Applet (network-manager gnome) needs to be un-installed, this is because for some reason it does not like WEP

This is done using Synaptic Package Manager
Open Synaptic Package Manager > search for “network-manager gnome” and completely remove it
Now reboot for the changes to take place
Installing WiFi Radar
Now we will install “wifi radar” > open Synaptic Package Manager. > search for “wifi-radar” > install it
If you now look under > Applications > Internet > You will see WiFi Radar > open it and you should see any wireless networks that are broadcasting in your area.

Now to set up the WEP
Open Firefox and logon to your router.  For example in this case [http://192.168.1.1](http://192.168.1.1)
Now set your WEP key and write it down
Open WiFi Radar, after a while you should see your wireless ESSID, highlight it >  disconnect > connect > a window will open asking if your would like to configure the profile >  
Yes > input the following...
Network name (ESSID) “Your ESSID”
WiFi Options...
Mode: Managed
Channel: Input the channel your router is broadcasting on
Key: Input your “WEP” key
Security: In this case “Open”
Automatic network configuration DHCP
> and Save > WiFi will now connect to your router

Now add to your wireless WEP key as shown below to your /etc/network/interfaces file
auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto wlan0

iface wlan0 inet dhcp

wireless-essid “YOUR ESSID”
wireless-key ”YOUR KEY

let me know how it went

Stew

---

### Post by ianb72 on 2007-04-25
> **wieman01 said:**
> First off, remove all other lines from "/etc/network/interfaces"... the file needs to contain only what Dbott67 and I have posted. Second, please remove the Ethernet cable as you cannot have 2 connections at a time. Then restart the computer.

Any results?

Ok sorry I miss understood you! :( 

Right I copied and pasted this in
[HTML] auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BARDELLS
wireless-key YOUR_HEX_WEP_KEY[/HTML]

but I put in my HEX WEP KEY but still no joy.

It sees my network (router) and everyone else's but just wont connect to it, not even in the roaming mode.

---

### Post by wieman01 on 2007-04-25
> **ianb72 said:**
> Ok sorry I miss understood you! :( 

Right I copied and pasted this in
[HTML] auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid BARDELLS
wireless-key YOUR_HEX_WEP_KEY[/HTML]

but I put in my HEX WEP KEY but still no joy.

It sees my network (router) and everyone else's but just wont connect to it, not even in the roaming mode.
Not even if you unplug the Ethernet network cable and restart the computer?

---

### Post by itsmeagain on 2007-04-25
Check out my post, it works for me
Basically I did the following
1. Get a connection to your router and disconnect WEP. (I used Windows to do this)
2. Uninstall network-manager gnome 
3. Reboot the machine
4. Install WiFi-radar using synaptic package manager
5. Connet to your router and enable WEP
6. Start WiFi Radar, highlight your network, edit your connection and bingo it works even after rebooting

Stew

---

### Post by wieman01 on 2007-04-25
> **itsmeagain said:**
> Check out my post, it works for me
Basically I did the following
1. Get a connection to your router and disconnect WEP. (I used Windows to do this)
2. Uninstall network-manager gnome 
3. Reboot the machine
4. Install WiFi-radar using synaptic package manager
5. Connet to your router and enable WEP
6. Start WiFi Radar, highlight your network, edit your connection and bingo it works even after rebooting

Stew
Actually the default tools that come with Ubuntu are well capable of coping with WEP... I would not temper with a default install, at least not as far as such a simple thing as WEP is concerned. You'll regret it later on.

---

### Post by wieman01 on 2007-04-25
One last word for today (getting late here)... WEP keys can have different strenghts e.g. 64-bit, 104-bit. Try all options there are (router) because I remember Ubuntu used to have a problem with 64-bit keys.

---

### Post by ianb72 on 2007-04-25
Stew
Your a star this took a bit of time but its worked a real treat :)  :popcorn: 

Now I am connected to the router with 64 bit WEP Encryption

Thank you so very very much.

You Rock :guitar: 

Ian

---

### Post by keith11 on 2007-04-25
> **wieman01 said:**
> One last word for today (getting late here)... WEP keys can have different strenghts e.g. 64-bit, 104-bit. Try all options there are (router) because I remember Ubuntu used to have a problem with 64-bit keys.

I don't intend to distract you guys here but I was reading what you said about Ubuntu having problems with 64-bit WEP encryptions. It seems so true as I have been struggling with it since Edgy. If you have time please take a look at this thread I started about a problem with ipw2200 and WEP. Actually i noticed right now that even on wireless connections without encryption I get stuck for some seconds with a message like "looking for..." or "waiting for..." in firefox. I am using opendns nameservers and the situatio is acutally better with those nameservers compared to when I allow it to use the nameservers of the connection. My thread is at: [http://ubuntuforums.org/showthread.php?t=423075&highlight=wep+feisty](http://ubuntuforums.org/showthread.php?t=423075&highlight=wep+feisty)

Thanks and I am happy for the original poster who got his issue resolved. It's always a sigh of relief when you get your network connections working.

---

### Post by sloggerkhan on 2007-04-25
my school use wep2 encryption on their wireless, works fine with my card and ndiswrapper, but even on windows there are some cards that do not support it.

---

### Post by wieman01 on 2007-04-26
> **ianb72 said:**
> Stew
Your a star this took a bit of time but its worked a real treat :)  :popcorn: 

Now I am connected to the router with 64 bit WEP Encryption
Alright, 64-bit keys a bit of a headache. In that case I have to agree with Stew. :-)

Don't you want to give WPA2 a go? It is much more secure than WEP. Wifi-Radar supports it as well.

---

### Post by ianb72 on 2007-04-26
> **wieman01 said:**
> Don't you want to give WPA2 a go? 


I think I may well try this, just to see if I can do it!!

Ian

---

### Post by Candace on 2007-05-04
Thank you so much, Stew, for your easy to follow instructions on getting wireless to work!! It works for me with Fiesty now, again thanks sooo much. :) 8-) :grin: :-) :smile:  I am very happy that all my searching on the forums and trying different things finally paid off.  I edited your post and copied parts of it to reply to another post here: [http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

I just have one question for you or anyone though, where do I find the "how to's" to learn how to encrypt my network? I have never had my network encrypted even in Windows :oops:  but  I want to encrypt it now because I know that it is smarter. Any links would be appreciated. My laptop is now a dual boot (Ubuntu + WinXP) HP dv2000 with a Broadcom 1390 WLAN wireless card. Thanks.

---

