---
title: "I can see networks, but cannot connect --wireless issue--"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Lazy-buntu on 2008-04-10
Currently I dual boot Windows Vista and Ubuntu 7.10 (Gutsy), but I'm running into a problem with my wireless.

I used ndiswrapper to install my wireless driver--the driver is installed (ndiswrapper -l shows it)--and if you are familiar with HP laptops the WLAN switch works properly (amber color when off, blue when on)

I can see wireless networks when I do iwlist eth1 scan (my network, and my two neighbors').

There's a problem though: I cannot connect to them. My network has a WEP key (hex) and a broadcasted ESSID. So, in my network tools I set my ESSID, put my WEP key in, and set my IP to DCHP. Even if I reboot it doesn't work.

I heard ipv6 can cause problems according to the built in help topics in ubuntu--it tells you to gedit /etc/modprobe.d/aliases and change ....... pf 10 ipv6    to      ........ pf 10 off--I did this and rebooted, no go. (I did change it back since then.)


Any ideas? (BTW: I can't get a wired connection, so I haven't been able to do any  updates)

P.S. bcm43xx has been blacklisted, I did add ndiswrapper to /etc/modules, my wireless card is eth1--it doesn't appear as wlan0

---

### Post by Lazy-buntu on 2008-04-10
double post

---

### Post by Lazy-buntu on 2008-04-10
I just burned an OpenSUSE live CD. I decided to see if my wired connection would work with OpenSUSE so I plug the same cable in I was trying with my actual gutsy install and I have a wired connection...:lolflag:

Anyway, I would rather have my gutsy install working than installing OpenSUSE and fooling around with YaST (I like synaptic package manager much better).

It's still linux, but why bother switching distros if I don't have to.

Come on ubuntu community, I know someone has to have solved this problem before!

---

### Post by Lazy-buntu on 2008-04-11
I think it may have to do with DHCP. When I try sudo dhclient eth1  I see offers and requests, but it does not stop. In other words, I can't answer to the offers I guess.

When I look in network manager (I think) it shows eth1 sending and receiving packets with a signal strength around 70-94%.

:confused: :bumps thread: :confused:

---

### Post by Lazy-buntu on 2008-04-11
Note: Router is set up for DHCP and my WEP key is 128 bit Hex (know this for sure).

---

### Post by nick.ncs on 2008-04-11
There are 2 things you can try out

1. Try creating a profile in Wi-fi Radar and try to connect
[http://wifi-radar.systemimager.org/]("http://wifi-radar.systemimager.org/")

2. Try using WPA instead of WEP.

---

### Post by Lazy-buntu on 2008-04-11
Is there another DHCP client/software I could try using within gutsy or is there an upgrade I can download on the windows half of the dual boot and put on a cd?

I don't know if this is what I'm looking for or not: [http://packages.ubuntu.com/gutsy-updates/dhcp](http://packages.ubuntu.com/gutsy-updates/dhcp)

but either way I can't load the page in vista

and I can't download wifi-radar in vista to a CD--won't load page

---

### Post by gilf on 2008-04-11
Turn off wep on your router make sure dhcp is set on the router and your computer, unplug the router for a minute, start it up, verify it's operatring with another computer, then try to connect. If you are connected, ping an address on your local network to verify. If that works, ping an address on the internet. If that works, try your browser. If that doesn't work check your DNS addresses and also do a Edit>Preferences>Advanced>Network>Settings (in Firefox) and try out the autodetect proxy settings.

---

### Post by gilf on 2008-04-11
Here are a couple of DNS server addresses (OpenDNS) in case youy don't have any:

208.67.222.222 and 208.67.220.220

---

### Post by Lazy-buntu on 2008-04-11
I can't connect to unprotected networks either.

Maybe it's the way I installed the driver. I used this guide: [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

but I put the ndiswrapper and WLANBroadcom .tar.gz on a cd and put it in my home folder; then, I couldn't do the steps:

sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

but as I said before, I can see wireless networks when I scan

however, even off a fresh install with nothing done yet, I could not get a wired connection (but using the OpenSUSE 10.3 live CD I could) through the router/switch or directly in the modem

I heard fw-cutter works surprisingly well in gutsy, but I'd need a wired connection

I'll try your DNS recommendation though

---

### Post by Lazy-buntu on 2008-04-11
Tried entering those as DNS entries, did nothing for my problem though.

I decided to reformat and reinstall gutsy just to make sure I cannot get a wired connection (if I run dhclient eth0 I get offers from my router, but ubuntu doesn't accept them). 


I'm not sure what to do now, I think I'll try burning the Fedora 8 Live CD and see if I can get a wired connection AND my sound working (OpenSUSE had network working but no sound), because it's starting to look like no one can help me here. 

However, if anyone has experience with an HP laptop with broadcom drivers using gutsy gibbon or knows a reliable/simple walk through for getting wireless working...or who can help me resolve my DHCP problem with ubuntu please post.

---

### Post by Lazy-buntu on 2008-04-11
I'm going to try: [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

I'll let you know how that works..

---

### Post by Lazy-buntu on 2008-04-11
Same exact problem as before: I can see networks, but cannot connect. My wireless adapter is eth1, not wlan0 (even after creating /etc/iftab where it says wlan0 mac "my mac address for wireless card without quotes")

Still no wired connection.

With cat-5 cable plugged in, or without it plugged in (using wireless)...if I run dhclient I get the usual:

...Offer from 192.168.2.1 (my router)
...Request
....DHsomething
....same DHsomething
...Request
...Offer

same loop for basically as long as I let it run

I am getting DHCP offers for an IP address, but I guess ubuntu isn't accepting them? I'm out of ideas...

---

### Post by Lazy-buntu on 2008-04-11
I've got the Live CD for Fedora 8 Werewolf in and the wired connection works, sound works, but no mouse pointer rofl (mouse works--so does touch pad but there's no pointer)

I think I'll install Fedora and work from there since no one here can point me in the right direction.

---

### Post by Lazy-buntu on 2008-04-11
Ok, I managed to get eth1 changed to wlan0 by doing:

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

(the equivalent of /etc/iftap in feisty)

I changed "eth1" to "wlan0"

However, I cannot connect still...here's my exact output of sudo dhclient wlan0


Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
ubuntu-dualboot@ubuntu-dualboot-laptop:~$ sudo ifconfig eth0 down
ubuntu-dualboot@ubuntu-dualboot-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   LPF/wlan0/XX:XX:XX:XX:XX:XX
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

and keeps going....

#-o

---

### Post by yuku-aki on 2008-06-02
I'm having the same problem with Feisty; just yesterday, everything worked fine, but this morning, when I'm at the coffeeshop (where everyone else's machine is connected just fine... mac/pc alike) I have the EXACT issue.  I ran wireshark, and seem to be getting the same request/no response problems.  I got online by using my Feisty LiveCD - so until I figure this out, I guess I'll be booting from CD to get online.  At least one step in the right direction.

---

