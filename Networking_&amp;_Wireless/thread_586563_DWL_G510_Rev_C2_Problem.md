---
title: "DWL G510 Rev C2 Problem"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by akshayas1986 on 2007-10-22
Hey guys
I have a DLink DWL G510 Rev C2 Wireless PCI card on my computer. This card does not seem to be working. Once I plugged it in, the card was able to detect networks but was not connecting to it. I have tried everything and nothing seems to be working. 

I have a TPLink router at 192.168.1.1. One breakthrough: With all the iwpriv settings that I found online, my network gives a non zero finite Link Quality (around 80/100). 

But since my wireless network is DHCP enabled, I need to dynamically get my IP address. Almost all the posts on RT61 talks about static IP Addresses.

Also when I do 'sudo iwlist scan', I can see my network but it says 'Quality: 0/100'. But if I do iwconfig, I see that my Link Quality is some finite non-zero value.

And whenever I do dhclient ra0, it tries to acquire an IP address but ends up saying no DHCPOFFER or something

Please help me. Without th internet, Ubuntu is quite boring to work with.

Thanks

---

### Post by akshayas1986 on 2007-10-23
Please is there anyone who can help me?

---

### Post by akshayas1986 on 2007-10-29
Guys after spending almost 7 days on this trivial problem, I am proud to say that I HAVE SOLVED IT (But with the help of Raubsau. So a BIG THANKS to you man)

Well I noticed something.
> sudo ifconfig ra0 down
does not restart the network interface. So irrespective of the changes made to the interface file, it used to not reflect on it. So I tried
> sudo /etc/init.d/networking restart
after making changes to the interface file and it finally worked

So this is my /etc/network/interfaces file


> auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid Slash
pre-up iwconfig ra0 mode managed
pre-up ifconfig ra0 up
pre-up iwpriv ra0 set AuthMode=OPEN
pre-up iwpriv ra0 set EncrypType=WEP
pre-up iwpriv ra0 set Key1=hindu
pre-up iwpriv ra0 set DefaultKeyID=1
pre-up iwpriv ra0 set TxRate=0
pre-up ifconfig ra0 mtu 1464
Please ignore the last line. That is an MTU settings for my Broadband connection. Also since DHCP is not much talked about in this community for RT61, I hope this helps.

---

