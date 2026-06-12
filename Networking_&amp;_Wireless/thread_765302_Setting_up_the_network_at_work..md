---
title: "Setting up the network at work."
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by dover19 on 2008-04-24
I'm trying to install Ubuntu as a dual boot on my PC at work. I printed out a text file of ipconfig in WinXP to get all the network settings (I have static IP and if I use a different one I won't have access to the "outside world"). When I booted up the Live CD I wanted to setup the network so that I could have access to the outside for the install, but even after copying the network settings from Windows (except the host name, but that shouldn't matter right?) I still can't get out.

Any ideas?

---

### Post by rickyjones on 2008-04-24
> **dover19 said:**
> I'm trying to install Ubuntu as a dual boot on my PC at work. I printed out a text file of ipconfig in WinXP to get all the network settings (I have static IP and if I use a different one I won't have access to the "outside world"). When I booted up the Live CD I wanted to setup the network so that I could have access to the outside for the install, but even after copying the network settings from Windows (except the host name, but that shouldn't matter right?) I still can't get out.

Any ideas?

Are you sure you have all the network settings correct? IP, Subnet, Gateway, DNS? Does your network contain a proxy server?

-Richard

---

### Post by dover19 on 2008-04-24
IP: 10.0.0.76
Subnet Mask: 255.255.255.0
Default Gateway: 10.0.0.1

Ubuntu actually detects the DNS and puts in the same address XP uses.

As for the the proxy server, I checked with the Network Admin here and he says we don't have one.

---

### Post by rickyjones on 2008-04-24
> **dover19 said:**
> IP: 10.0.0.76
Subnet Mask: 255.255.255.0
Default Gateway: 10.0.0.1

Ubuntu actually detects the DNS and puts in the same address XP uses.

As for the the proxy server, I checked with the Network Admin here and he says we don't have one.

Can you ping the gateway? 

-Richard

---

### Post by dover19 on 2008-04-24
lol, wow...

connect: Network is unreachable

I can't even ping my ip either. 

It doesn't make a difference wether I'm setting up the Live CD or an actual installation right? They should both work just the same.

---

### Post by rickyjones on 2008-04-24
> **dover19 said:**
> lol, wow...

connect: Network is unreachable

I can't even ping my ip either. 

It doesn't make a difference wether I'm setting up the Live CD or an actual installation right? They should both work just the same.

Correct, it should work either way. Is it detecting your network card correctly? I'm not sure how to check...

-Richard

---

### Post by prshah on 2008-04-24
> **dover19 said:**
>  When I booted up the Live CD I wanted to setup the network so that I could have access to the outside for the install, but even after copying the network settings from Windows (except the host name, but that shouldn't matter right?) I still can't get out.

Any ideas?

> **rickyjones said:**
> Are you sure you have all the network settings correct? IP, Subnet, Gateway, DNS? Does your network contain a proxy server?

-Richard

When setting up a static IP, you need to manually setup your DNS servers in the /etc/resolv.conf file. Typically, it will just contain your router's address, or DNS addresses as suggested by your ISP.
> ```

cat /etc/resolv.conf
nameserver 192.168.1.1

```

---

### Post by prshah on 2008-04-24
> **rickyjones said:**
> Correct, it should work either way. Is it detecting your network card correctly? I'm not sure how to check...

-Richard

```
ifconfig
``` will give us a clue. Have you tried restarting the network after setting up your IP address?```
sudo /etc/init.d/networking restart
```

---

### Post by dover19 on 2008-04-24
> **prshah said:**
> When setting up a static IP, you need to manually setup your DNS servers in the /etc/resolv.conf file. Typically, it will just contain your router's address, or DNS addresses as suggested by your ISP.


Yeah but it's actually detecting the correct info. I opened up the resolv.conf file and it's the correct address. Makes no difference if I re-input it and save the file.

---

### Post by dover19 on 2008-04-24
Wow, restarting the network did it. I'll install it tomorrow then.

Thanks a lot, both of you!

---

