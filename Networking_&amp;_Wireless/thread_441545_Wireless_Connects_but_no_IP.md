---
title: "Wireless Connects but no IP"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by iAMbigFISH on 2007-05-12
Hi everyone, I've FINALLY decided to install Linux on my laptop and begin learning something new -- it's been a while!

My current issue is with my wireless mini-PCI card, it sees all available wireless networks, connects to mine but does not grab an IP -- I've even tried assigning one with no luck.

Any ideas?

Thanks in advance!

PS: I'm using the latest version of Ubuntu (7.04)

---

### Post by ricardovich on 2007-05-13
Do:
```
sudo iwlist scan
```
One of the interfaces should show a wireless access point. 
To get an IP, Ubuntu, like Debian uses dhclient.

```
sudo dhclient interface
```
where "interface" is replaced by eth1, or wlan0, or whatever Ubuntu defines as your wireless card.
 
If your network if encrypted with WEP or WPA then there are more steps involved.

---

### Post by iAMbigFISH on 2007-05-14
When I entered:

```
sudo iwlist scan
```

I received this msg:

ath0     Interface doesn't support scanning : Network is down




Any thoughts? :)

---

### Post by iAMbigFISH on 2007-05-14
I've done something and now I see my wireless, when I tried the next command 

```
sudo dhclient ath0
```

I don't get a DHCPOFFER -- although I know my router IS assigning IP's since my desktop get's one

---

### Post by ricardovich on 2007-05-15
"ath0 Interface doesn't support scanning" usually means that the interface isn't wireless but you say your seeing networks.
Is your wireless encrypted?

Display: 
```
more /proc/net/wireless 
```

Try to use iwconfig to connect:
```
iwconfig interface
```

Do:
```
man iwconfig
```
to see how to input essid.

---

