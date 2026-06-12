---
title: "Feisty: Network Manager connects, but no internet"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by Viper Daimao on 2007-04-27
I'm am also having problems with wireless in Feisty, though in Ubuntu, not kubuntu. I did a clean Feisty install on my dell inspiron 6000, with an intel wireless card and using ipw2200 driver. I can connect to my WPA2 network fine, and can transfer files over the network and ping external IPs. However I cannot ping domain names. Nor can I access any outside webpages, or connect to instant messengers, nor connect to ip addresses. I tried changing my dns to opendns but this hasn't helped. I turned off the encryption of my network and still see the same behavior. So I tried installing wicd, but still saw the same exact behavior. What's odd was that it worked at my friends apt on his WEP netgear router, but not my linksys WPA2, WEP, nor even no encryption. It was a bit slow with look ups and redirects though.

I looked at my /etc/network/interfaces file and saw this

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp

auto eth0

```
The weird thing is I don't have a eth2, ath0, or wlan0 interface. My wired network card is eth0 and my wireless card is eth1. So I added


```
auto eth1
iface eth1 inet dhcp
```

but nothing changed. I've tried manually stopping the network and restarting to see no change. What's worse is that after I removed the open dns servers from my router, when I restarted my laptop, my wired connection stopped working (in the same way my wireless was, can connect to network, but not out of network), so now I have no way to connect to the internet after just a clean install of ubuntu.

This all worked fine under Edgy so I'd be really grateful for any help or anything I can try to figure this out more.

---

### Post by agurk on 2007-04-28
Ok, start by adding back a DNS server, you definitely need one.
Then, check out [this](http://ubuntuforums.org/showthread.php?p=2545109) thread to find out if your problem is MTU related.

---

### Post by Viper Daimao on 2007-05-02
Of course I have a dns server. Just tried to user the opendns servers instead of my isp's.

I added the opendns servers back and after a few days, and before I could try the MTU tests, it's all started working again. I'm happy, but warry of my laptop's wireless fickleness.  I'll update further if the problem occurs again.

---

### Post by agurk on 2007-05-02
Alright. :)

Your /etc/network/interfaces does look a bit bushy. For reference, mine looks like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp
auto eth0
```

Actually, a commonly occurring tip is to comment out everything but the two loopback rows.
Perhaps it'd be worth trying if problems should arise again and the issues aren't MTU related.

---

### Post by Viper Daimao on 2007-05-07
It went out this weekend while I was transfering a file to another computer on my network. I noticed that my weather gnome toolbar widget thing occasionally connected, but only very very briefly. I'd look over at my laptop and noticed the temp had been updated. Access came back a day or so later. I power cycled my router and modem, but saw no change, then a few hours later brought my computer back from standby and it worked. 

Anyways, I've now commented out the other interfaces on my file. Also what is MTU exactly? I run an ifconfig on my wireless connection and get this output. This is now while it's working. 

```
eth1      Link encap:Ethernet  HWaddr 00:12:F0:3E:D3:76  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe3e:d376/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42099 errors:12 dropped:12 overruns:0 frame:0
          TX packets:24810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54722466 (52.1 MiB)  TX bytes:2321822 (2.2 MiB)
          Interrupt:18 Base address:0x4000 Memory:dfcfd000-dfcfdfff 
```

thanks for your help.

---

### Post by agurk on 2007-05-08
MTU is the size of the largest packets that can be transferred. There was a thread here not long ago where a guy could ping external IPs but not download anything but very small files. Basically, if the automatic MTU detection doesn't work (which can happen for a number of reasons), things b0rk.

More info: [http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

Quick test: sudo ifconfig eth1 mtu 1400

There are also numerous reports around about people having solved their network problems by disabling IPv6.

---

### Post by Whiffle on 2007-05-08
What happens when you ping your router?  How about a website?

---

### Post by Viper Daimao on 2007-05-08
Ah, thanks for the info agurk, I'll be sure to try that. 

Whiffle, I can ping my router with no problem, and can ping external ip addresses, however website domain names (e.g. [www.google.com](www.google.com)) will time out.

However right now, it's been working since sunday night, so I'll have to wait and see if it goes out again.

---

