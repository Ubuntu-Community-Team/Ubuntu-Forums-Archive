---
title: "Ubuntu Clean Install - Get Wireless signal but status disconnected"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by gavaiken on 2007-02-07
Hey all, I tired to format this information in an easy to read way although I'm not sure if it's worked!! I have a lot of information to hopefully help you help me but those in the know just read the summary and skip to the bottom :) Thanks

-----------------------------------------------------------------
[SIZE="4"]Brief Summary[/SIZE]
-----------------------------------------------------------------
I want wireless on my Ubuntu desktop installation. 
'iwlist wlan0 scan' finds my AP.
'iwconfig wlan0' is set up to the correct SSID and WEP key
On startup I get signal for the connection but a status of disconnected.

I want it to connect :) 

Screenshots of the output of above functions can be found at this url

[http://www.commonwealth-hall.co.uk/gavin/EE/screenshots.htm](http://www.commonwealth-hall.co.uk/gavin/EE/screenshots.htm)

-----------------------------------------------------------------
[SIZE="4"]Background[/SIZE]
-----------------------------------------------------------------

- Did a clean install on an 80GB partition of Ubuntu 6.10 for desktop PCs and I use grub to boot between it, XP and Vista the latter two both have working wireless connections.

- I used the ndiswrapper by following the guide at the url below to install a windows XP driver for my D-Link AirPlusG+ 520+ PCI card.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Installation)

- Everything went perfectly, at the stage which states

"Now, setup the network parameters for the interface wlan0. This varies from distribution to distribution. Refer to your distribution's documents on how to do this. Once this is done, you can use network tools to bring up the network e.g.,
 ifconfig wlan0 up
dhclient wlan0"

- I went to the Ubuntu specific wiki which gives the following skeleton for the interfaces file in /etc/network

-----------------------------------------------------------------
[SIZE="4"]Skeleton  network config file[/SIZE]
-----------------------------------------------------------------
[FONT="Courier New"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

# The primary network interface
iface wlan0 inet static
# wireless-* options are implemented by the wireless-tools package
wireless_keymode open
wireless_key REPLACE WITH YOUR WEP KEY
wireless_mode managed
wireless_essid REPLACE WITH YOUR ESSID
wireless_nick REPLACE WITH YOUR HOST NAME
address 192.168.1.3 OR REPLACE WITH YOUR FIXED IP ADDRESS
netmask 255.255.255.0 OR REPLACE WITH YOUR NETMASK RANGE
network 192.168.1.0 OR REPLACE WITH YOUR IP ADDRESS
broadcast 192.168.1.255 OR REPLACE WITH YOUR IP ADDRESS
gateway 192.168.1.254 OR REPLACE WITH YOUR GATEWAY (WAP or Router) IP ADDRESS
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.1.254 OR REPLACE WITH YOUR GATEWAY (WAP or Router) IP ADDRESS

auto wlan0[/FONT]

-----------------------------------------------------------------

From this I went into XP and ran [SIZE="4"]ipconfig[/SIZE] so that I could fill in the neccesary information.

-----------------------------------------------------------------

[FONT="Courier New"]C:\Documents and Settings\Gavin>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : sirsystem
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : config

Ethernet adapter Wireless Network Connection 3:

        Connection-specific DNS Suffix  . : config
        Description . . . . . . . . . . . : D-Link AirPlus G+ DWL-G520+ Wireless
 PCI Adapter
        Physical Address. . . . . . . . . : 00-13-46-B2-74-15
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.64
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254
        DHCP Server . . . . . . . . . . . : 192.168.1.254
        DNS Servers . . . . . . . . . . . : 192.168.1.254
        Lease Obtained. . . . . . . . . . : 07 February 2007 18:51:51
        Lease Expires . . . . . . . . . . : 08 February 2007 18:51:51[/FONT]
-----------------------------------------------------------------

Using this information I created the file below, I appreciate that creating a static ip seems like more trouble but the DHCP option gave me no results.

-----------------------------------------------------------------
[SIZE="4"]My version of  the network interface file is[/SIZE]
-----------------------------------------------------------------
[FONT="Courier New"]# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

# The primary network interface
iface wlan0 inet static
# wireless-* options are implemented by the wireless-tools package
wireless_keymode open
wireless_key F49F7AE132
wireless_mode managed
wireless_essid BeBox
wireless_nick gavUbuntu
address 192.168.1.64
netmask 255.255.255.0 
network 192.168.1.64
broadcast 192.168.1.64 
gateway 192.168.1.254 
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.1.254 

auto wlan0[/FONT]
-----------------------------------------------------------------

Which gets me to the stage I'm at now, Ubuntu gives a signal strength but says disconnected, I use the same wireless card and router with XP on the same machine with what seems like the same settings.

The router says SSID: BeBox and WEP(hex): F49F7AE132 WPA: F49F7AE132
if that makes any difference?!

To make it easier for you to answer my question i've got a few screenshots available as mentioned previously.

[http://www.commonwealth-hall.co.uk/gavin/EE/screenshots.htm](http://www.commonwealth-hall.co.uk/gavin/EE/screenshots.htm)

Can someone please tell me the settings I need to change to get this whole thing to work?
I think the secret might be in the 'wireless_mode' and 'iface wlan0 inet static' parts.
I tried it with DHCP which I understand to be automatic ip assignment and I get no connection and no signal upon reboot.

Maybe I need to understand what network & broadcast refer to in the linux config file as I just entered my own ip and not knowing what they do this might be wrong.

Please help, I really want to join the Linux community :)  It might just be that I'm new to Ubuntu and i'm missing comething simple like the CONNECT button, Disconnected is just written on the info box (see screenshots) and there isn't really anything to fiddle with!

I have looked at similar threads but haven't found a viable answer, just people who format and reload and it works second time around. Although this is an option, I'm really looking to get to know how the system works.

Thanks in advance,

Gav

---

### Post by ukripper on 2007-02-08
Install wlassistant and run from terminal using $ *sudo wlassistant*, wireless network will show up if your wireless card is configured correctly, wlassistant will show you available networks click on one of the network you wnat to use, put wep key in and don't forget to tick on **ASCII** and use either dhcp or static as you need. click ok and there you go.

check using $ sudo gedit /etc/network/interfaces       , should have wlan0 (or eth1 if you using eth1) and make sure it has 

wlan0 or eth1 configured or use gui feature netwrork manager.

hope it helps.

---

### Post by gavaiken on 2007-02-08
Hi, thanks for the reply, being a new Ubuntu user I'm having problems installing wlanassistant to test your solution.

My machine is offline so the Synaptic Package manager is out of the question. I don't think the package is on the Ubuntu disk so I downloaded the souch code from here

[http://wlassistant.sourceforge.net/](http://wlassistant.sourceforge.net/)    I chose source 0.5.6

I have installed the build-essentials package (I needed it to install ndiswrapper) but when i use the terminal to 'make install' on the extracted wlassistant  I get an error. Running ./configure gave me this:

> gav@gav-PC:~/Desktop/wlassistant-0.5.6$ sudo ./configure
Password:
Checking for Python               :  -e /usr/bin/python
Checking for SCons                :  -e not found, will use mini distribution.
scons: Reading SConscript files ...
Checking for kde-config           :  kde-config was NOT found in your PATH 
Make sure kde is installed properly
(missing package kdebase-devel?)
gav@gav-PC:~/Desktop/wlassistant-0.5.6$ 

Any ideas how I can get this working or what the error means? Hopefully it's simple and i'm just not thinking clearly because I've been working on this so long!!

Thanks again,

Gav

---

### Post by ukripper on 2007-02-08
try this first $ sudo ifdown wlan0 and then $ sudo ifup wlan0 and if it still doesn't work check your wlan0 WEP key is correct which you are using and try using DHCP instead of static which might resolve dns issues(if any).

If light is not flashing then do following:
$ sudo depmod -a
$ sudo modprobe ndiswrapper

now when light flashes do the following:
$ sudo ifdown wlan0
$ sudo ifup wlan0

check network manager and enable wlan0 and properties to ESSID : network name you want to connect to,
WEP KEY: YOUR WEP KEY to connect network
Select DHCP

OK.

It will enable your wlan0
and make sure /etc/network/interfaces has wlan0 associated with same ESSID and WEP you entered above.

for wlassistant best thing to do is connect ethernet wire to eth0 and from synaptic install wlanassistant which is for KDE therefore you will need $ sudo wlanassistant comand to run from terminal and then follow my instruction from the previous post.

Hope it helps.

:KS

---

### Post by ukripper on 2007-02-08
type $ sudo iwconfig and paste here.

Cheers

---

### Post by gavaiken on 2007-02-08
Thanks again for the quick reply, I tried what you've suggested but to no avail, here's my terminal:

> gav@gav-PC:~$ **sudo depmod -a**
Password:
gav@gav-PC:~$ **sudo modprobe ndiswrapper**
gav@gav-PC:~$ **sudo ifdown wlan0**
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4736
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:b2:74:15
Sending on   LPF/wlan0/00:13:46:b2:74:15
Sending on   Socket/fallback
gav@gav-PC:~$ **sudo ifup wlan0**
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:b2:74:15
Sending on   LPF/wlan0/00:13:46:b2:74:15
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
gav@gav-PC:~$ **sudo iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"BeBox"  Nickname:"gavUbuntu"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:F49F-7AE1-32   Security mode:open
          Power Management:off
          Link Quality=39/100  Signal level=14/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


Is the DHCPDISCOVER meant to search for and aquire the ip address?

In the interfaces file what's the difference when you add the s: to 
wireless_key s:MYKEY

it doesn't work with or without it :( anyway.

iwconfig is in the above quote is the listening and sending correct? I really can't get my pc to where the router is without a lot of effort as there aren't enough plugs in that location.

Cheers.

---

### Post by ukripper on 2007-02-08
Your access point - Access Point: Not-Associated 
This means wlan0 is configured but can't find access point which is associated with it.
in ESSID you need to put the network name configured as in router something like DLink or BTvoyager(if BT) network id, find out using windows XP (if you have) and WEP-key should be the same as you used on wndows XP to connect to router. 

just find correct ESSID and WEP KEY, this is important.

Cheers

---

### Post by gavaiken on 2007-02-08
Hey, yeah I appreciate the importance of the correct ESSID and WEP KEY and I'm sure they are right unless it's the way I format the key

XXXXXXXXXX   ?
XXXX-XXXX-XX ?

the ESSID is "BeBox"

I've moved the pc painstakingly into the hall :) so im online in Ubuntu getting the wlassistant which will hopefully correct whatever errors I have made in the interface file.

Thanks again for all the help mate.

watch this space.........

---

### Post by ukripper on 2007-02-09
> **gavaiken said:**
> Hey, yeah I appreciate the importance of the correct ESSID and WEP KEY and I'm sure they are right unless it's the way I format the key

XXXXXXXXXX   ?
XXXX-XXXX-XX ?

the ESSID is "BeBox"

I've moved the pc painstakingly into the hall :) so im online in Ubuntu getting the wlassistant which will hopefully correct whatever errors I have made in the interface file.

Thanks again for all the help mate.

watch this space.........

No worries dude, just let me know of any outcome as it would be important for the new ubuntu users.:popcorn: 

Peace upon all!

Cheers

---

