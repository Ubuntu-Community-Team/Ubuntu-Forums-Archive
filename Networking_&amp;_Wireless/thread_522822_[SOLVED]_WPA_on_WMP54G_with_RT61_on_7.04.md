---
title: "[SOLVED] WPA on WMP54G with RT61 on 7.04"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by thusgaard on 2007-08-11
Hi 

I've just installed my fathers PC with Feisty Fawn. The machine has a WMP54Gv4.1 WLAN card. It's the one with the RT61 chipset. But it seams that the driver (Feisty installed one by it self) does not work with WPA encryption. 

Is there anyway to turn on WPA. 

I've searched the forums, and the internet. But maybe my search string is wrong. please keep in mind I'm a newbie, this is only my second linux install.

J;-)

---

### Post by ugm6hr on 2007-08-11
Yes - with ndiswrapper.

This has a few links to help get you going - but perhaps not the best.  Maybe search for ndiswrapper RT61?

[http://ubuntuforums.org/showpost.php?p=3170670&postcount=3](http://ubuntuforums.org/showpost.php?p=3170670&postcount=3)

---

### Post by thusgaard on 2007-08-11
Following the "Installing Windows driver using command line" method in one of your links: 

```
sudo ndiswrapper -i ~/drivers/drivername.inf
```

Returns: 
driver rt61 is already installed

```
ndiswrapper -l
```

Returns: 
bcmwl5 : driver installed
rt61 : invalid driver!

Do I need to disable the bcmwl5 driver?
Is it a free driver?
Can I disable it using [blacklisting]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3")?
And is there anything to do about the invalid driver?
Will this ever work?

Panic... ;-)

Kind regards

J;-)

---

### Post by thusgaard on 2007-08-12
BTW. The current driver setup is not abel to connect to unprotected networks.

---

### Post by kevdog on 2007-08-12
Hmm I guess you have two options

1. Upgrade your rt61 driver (the default one included is very old).  The new version does wpa but not wpa2.  This is known as the rt61 serial monkey driver.

2. Ndiswrapper -- Ive done ndiswrapper with people almost 100 times, but not for the ra chipset cards.  I guess it would work, but I have no idea if it will do wpa/wpa2.  

Just letting you know some of the limitations you might run into!

---

### Post by thusgaard on 2007-08-12
Any links to a how to. 

At the moment I just want a wireless connection. 
Securtiy will some later. 

J;-)

---

### Post by bollix47 on 2007-08-12
See if anything [here]("http://ubuntuforums.org/showthread.php?t=419709") helps.  It's been a while but I'm pretty sure it's what I used.  I've never used ndiswrapper.

---

### Post by thusgaard on 2007-08-12
> **bollix47 said:**
> See if anything [here]("http://ubuntuforums.org/showthread.php?t=419709") helps.  It's been a while but I'm pretty sure it's what I used.  I've never used ndiswrapper.

That link seams to do the trick.... But. 

When I get to "1.3) Configure ra0's IP details" I want to use DHCP, and even if I try with a static IP  all connections fail when I try to change the route in "1.4) Configure routes" I dont get an error message, I just cant connect to the internet.

INFO about the current setup: 

```
$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:1A:70:AD:31:56  
          inet6 addr: fe80::21a:70ff:fead:3156/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000 
          RX bytes:39012 (38.0 KiB)  TX bytes:487 (487.0 b)
          Interrupt:9 

```

And

```
$ iwconfig ra0
ra0       RT61 Wireless  ESSID:"769PiskeRis"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:51:68:83   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off

```

And

```
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:0F:66:51:68:83
                    ESSID:"769PiskeRis"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

```


J;-)

---

### Post by bollix47 on 2007-08-12
I'm using static but there are some in that thread that are using dhcp so you might have better luck asking there.

A couple things to check might be:

1.  Did you blacklist your wireless driver in any of your previous attempts?

     Check /etc/modprobe.d/blacklist

      If so, remove it from the blacklist.

2.  Have you disabled ipv6?

     Search the forums for this one but basically you can just add "blacklist ipv6" (without the quotes) to /etc/modprobe.d/blacklist. Re-boot to ensure disable.

---

### Post by thusgaard on 2007-08-12
I had to leave, to go home. 
And i'll be back in 14 days to get it working. 

Fortunatly I have a similar setup at home, so I'll do some testing. 
Maybe even do my own how to with the brilliant help of the community.

J;-)

---

