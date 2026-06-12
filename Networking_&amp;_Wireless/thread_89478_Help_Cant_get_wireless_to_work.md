---
title: "Help Cant get wireless to work"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by Royal2000H on 2005-11-12
I tried posting on the kubuntu forums but its very slow there,
so here I am in the ubuntu forums, in the kubuntu section:


well I have a computer with a wireless Linksys WMP54G card...

This wasn't supported in kubuntu but I followed the ndiswrapper instructions from [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

and got a new interface: wlan0

but if I "sudo systemsettings" and go to network settings, I try to enable wlan0 it enables and in less than a second disables...

if i, "sudo ifdown eth0" "sudo ifdown wlan0" "sudo ifup wlan0"

I get a bunch of lines, but most importantly it shows

"
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
"

Now my network is setup with DHCP and on frequency 6 (2.437 GHz)

When I do "sudo iwconfig" wlan0 shows Frequency:2.462 GHz

Now, I know we can pick up a weak wireless signal from our neighbor, but his network is secured, so I'm afraid the 2.462 GHz iwconfig is showing, is the neighbor's network and it can't connect because of the need of WEP/WPA. And my network is unsecured...

So I "iwconfig wlan0 freq 2.437G"

But to no avail I get the same
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval xx

is it saying it's trying to get DHCP on 255.255.255.255 or all ip's upto 255.255.255.255 because I know my router is 192.168.1.1
I tried pinging 192.168.1.1
I get, "connect: Network is unreachable"

any suggestions?

---

### Post by mlomker on 2005-11-14
What are you getting from **ndiswrapper -l** and **iwconfig wlan0**?  Usually if DHCP can't get an address then it means that you either have security on your access point (and it isn't configured properly in Ubuntu) or the driver isn't working properly.

As an aside, Broadcom is evil.  If you can get a supported chipset then you'll be a lot happier.  They are one of the few companies that refuses to make a linux driver.

---

### Post by Royal2000H on 2005-11-14
[QUOTE=mlomker]What are you getting from **ndiswrapper -l** and **iwconfig wlan0**?  Usually if DHCP can't get an address then it means that you either have security on your access point (and it isn't configured properly in Ubuntu) or the driver isn't working properly.

As an aside, Broadcom is evil.  If you can get a supported chipset then you'll be a lot happier.  They are one of the few companies that refuses to make a linux driver.[/QUOTE]
ahh nvm i got it solved, in an updated thread on the kubuntu-forums

---

### Post by RSX311 on 2005-11-14
what thread would that be? Im having the same problems

---

### Post by Royal2000H on 2005-11-14
[http://kubuntuforums.net/index.php?topic=1567](http://kubuntuforums.net/index.php?topic=1567)

---

