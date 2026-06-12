---
title: "Wireless Internet"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Buco on 2008-04-24
Hello,

I installed my Sitecom WL113 v1-002 with the RT73 driver on my Ubuntu (64 bit). 

After, I set up the network manager with the required info.

I added a screenshot (see attachment) with the ifconfig info. It seems like the driver installed well. 

However, if I start up Firefox it can't open any site.

Any suggestions what might be wrong?

Cheers, 
Buco

---

### Post by prshah on 2008-04-24
> **Buco said:**
> 
However, if I start up Firefox it can't open any site.
Any suggestions what might be wrong?


Maybe you have no DNS servers setup. If you have set up your network manually (ie, no "Roadming Mode") then you need to add your DNS server addresses in the "/etc/resolv.conf" file. Typically, just one or two lines, containing either your router ip address or DNS addresses as specified by your ISP```

cat /etc/resolv.conf
nameserver 192.168.1.1

```

---

### Post by Buco on 2008-04-24
If I use that command I get the following output:

search lan
nameserver 192.168.1.***

So I guess this is ok.

By the way if I run the code:

     sudo ifup -v wlan0

I get the message:

No DHCPOFFERS received.
No working leases in persistent database - sleeping

Could this be the problem and how can I fix this?

I also added an extra screenshot for some more info.

Cheerz

---

### Post by prshah on 2008-04-25
> **Buco said:**
> If I use that command I get the following output:
I also added an extra screenshot for some more info.
Cheerz

Seeing your attached screenshot, I note that your wlan0 has been given a ipv6 address; and from what I understand you don't _use_ ipv6.

If that is the case, disable ipv6 by adding the word "ipv6" at the bottom of the file "/etc/modprobe.d/blacklist"

That should go a long way to solving your problem, and if you still face problems, please post back.

---

### Post by Buco on 2008-04-26
Tried it, but unfortunately thats not the solution.

I changed my interfaces file to install my connection manually:

[FONT="Courier New"]
# The loopback network interface
auto lo
iface lo inet loopback

#Wireless Interface
auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "internetservice"
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=1a2b3c4c
pre-up ifconfig wlan0 up[/FONT]


But now my computer freezes during boot time. It's due to the [FONT="Courier New"]pre-up iwpriv wlan0 set WPAPSK=1a2b3c4c... [/FONT]
line, because if I run this one separately it freezes.

---

