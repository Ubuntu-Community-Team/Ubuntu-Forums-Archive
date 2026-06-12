---
title: "how: laptop is sharing internet-connection with desktop-pc?"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by SleepyHollow on 2006-11-12
Hi Folks,

wasted three hours this morning and now I'm back at my usual solution with windows (desktop) and ubuntu (laptop). I want to do the same with ubuntu at my desktop-pc too without any windows.

The goal: For installation purposes I used my Desktop with win2000 and connected my laptop via ethernet (eth0) with the interface eth0 at the desktop. This works really good. I installed ubuntu breezy / dapper and now edgy with a cd at the laptop and got the basic system. But for the advanced setups of wireless-chip and other stuff I need a working internet-connection at the ubuntu-laptop. The eaysiest way for the installation is to connect via ethernet and share the internet-connection with the desktop.

This is my Windows-Solution: I fire up my desktop-pc with win2k, the laptop is connected via ethernet and uses the internet-connection of my desktop pc. The laptop uses dhcp, the desktop uses its own wlan-connection and shares it with the laptop giving via dhcp an ipnumber.

Today: I tried the same with ubuntu-edgy (Wlan) on my desktop-pc and the brand-new edgy-installation on my desktop. No way!

How can I configure this only as a solution which don't need windows at all. Has something to do with a dhcp-server-setup on my desktop?

Any suggestions are welcome,

greetings 
SleepyHollow

---

### Post by lazyart on 2006-11-12
I'm a bit lost here... are you using a router?  If no, why not?

Just plug into the router and you'd have a connection independent of the desktop.

---

### Post by SleepyHollow on 2006-11-12
Hi,

i have a router linksys wrt54g. My desktop (dual-booting win2k and ubuntu edgy) has wmp54g with ralink2500 and is connected wireless with the internet (works with ubuntu and win2k).

I want to share the internet-connection of the desktop, because the router is in the room of my wife and there is no place for me and a laptop on the router. Oh, you should see this crowded room.

It is easier to plugin the laptop via cat5-cable to the desktop and  use this way than to go to the chaos-room of my wife. ;)

With win2k on the desktop as dhcp-server (?) and ubuntu-edgy on the new laptop (eth0 as dhcp configured) it works without any configurations-issues. It was one click-with-the-mouse "using this connection with other pc" (desktop) or something like that.

All in a nutshell:

Laptop uses internet-connection this way

Laptop (ubuntu edgy) -_with_cat5_ethernet-cable_-> 
PC-Desktop (ubuntu edgy) -_wireless_-> Router Wrt54G

It seems to be a problem with the desktop-system. How to configure my desktop-pc with ubuntu?

I found a tipp: 

Firestarter features

    * Enables Internet connection sharing, optionally with DHCP service for the clients

Is "firestarter" perhaps the solution. Maybe its only a question of the right lines in "interfaces"?

Greetings 
SleepyHollow

---

### Post by Peter76 on 2006-11-12
Hi, firestarter is your solution; but first you have to install and setup your dhcp-server. Then install firestarter and turn on internet sharing and you are there. Good luck.

---

### Post by SleepyHollow on 2006-11-12
<quote>
ut first you have to install and setup your dhcp-server
</quote>

Hi,

some docs for the dhcp-server-setup out there? A link would be great.

Greetings
SleepyHollow

---

### Post by n3gbz on 2006-11-12
Similar situation to mine; temporarily staying in a hotel with wifi. 

Computer 1 connects to Internet via wireless, computer 2 is connected to computer 1 via eth0. 

Computer 1 runs XP with Internet Connect Sharing turned on and Computer 2 shares the Internet connection fine. 

When Computer 1 is running Dapper Drake I cannot share Internet access on Computer 2. 

I have messed around with firestarter but have not had success yet.

---

### Post by lazyart on 2006-11-12
not a solution but possible workaround-

Plug laptop directy to router.. maybe even borrow the desktop cable long enough to get packages and set up the wireless?

Just a thought.

---

### Post by SleepyHollow on 2006-11-13
> not a solution but possible workaround-

Plug laptop directy to router.. maybe even borrow the desktop cable long enough to get packages and set up the wireless?

Just a thought.

This is ridiculous: every linuxbox like edgy should solve this problem without getting into a configuration hassle like this. Linux is a child of the internet. Its major strength should be the access or the sharing of internet ressources. It can't be very difficult except something is wrong designed under the surface. ](*,)

---

### Post by SleepyHollow on 2006-11-17
Alright now, never say never: Some pieces of this howto are out of the net (source forgotten), the configuration-values and the whole interfaces-file is my work 8) 

Here's the workaround, only the Desktop-Configuration:

##Internet-Connection sharing Desktop-WLan-bridge for ralink2500:

Desktop: ra0 (wlan static configured), eth0 (bridge must be static configured)
Laptop: eth0 (connection via DHCP configured)

sudo apt-get install dhcp3-server
sudo cp /etc/default/dhcp3-server /etc/default/dhcp3-server_backup
gksudo gedit /etc/default/dhcp3-server

    * Find this line 

...
INTERFACES=""

    * Replace with the following line 

INTERFACES="eth0"

    * Save the edited file 


sudo cp /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf_backup
gksudo gedit /etc/dhcp3/dhcpd.conf

    * Find this section 

...
# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;
...

    * Replace with the following lines 

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

    * Find this section 

...
# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
# range 10.5.5.26 10.5.5.30;
# option domain-name-servers ns1.internal.example.org;
# option domain-name "internal.example.org";
# option routers 10.5.5.1;
# option broadcast-address 10.5.5.31;
# default-lease-time 600;
# max-lease-time 7200;
#}
...

    * Replace with the following lines 

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.1 192.168.0.200;
#attention: wlan-router-ip-here: XXX.XXX.XXX.XXX, optional other DNS-IPs
  option domain-name-servers XXX.XXX.XXX.XXX;
  option domain-name "your_Domainname";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}

    * Save the edited file 

sudo /etc/init.d/dhcp3-server restart

very important: the /etc/network/interfaces

This was real difficult to understand for a windows used person like me:
############
------------
auto lo
iface lo inet loopback

auto ra0
#iface ra0 inet dhcp
#static
iface ra0 inet static
address 192.168.1.110
netmask 255.255.255.0
#wlan router-ip
gateway XXX.XXX.XXX.XXX

pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid yourSSID
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=yourchannelnumber
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=yourencryptype(AES or TKIP)
pre-up iwpriv ra0 set WPAPSK="your_key"
pre-up iwpriv ra0 set TxRate=0
pre-up ifconfig ra0 up

#here the important part for the connection sharing
auto eth0

iface eth0 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
-----------------------
#####################

This works now for me with my Desktop with Edgy and the Laptop with Edgy. I don't now if it works for you. Don't complain if it won't. The Configuration issue is very annoying. For this purpose there should be a simplier solution. A script or something which does the trick automatically.

Greetings
SleepyHollow

---

### Post by n3gbz on 2006-12-26
Glad to see you got it working!!! 

I just got back to the problem today and posted the way I resolved it in this thread:

**[http://ubuntuforums.org/showthread.php?t=325666](http://ubuntuforums.org/showthread.php?t=325666)**   

firestarter and dhcp-server were mentioned previously but I did not understand those concepts well enough at that time.

The overall experience was very frustrating ](*,) and I agree that there should be a simpler way.

---

