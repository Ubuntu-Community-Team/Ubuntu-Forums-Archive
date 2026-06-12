---
title: "No Network Connection-CPQ Netelligent 10/100"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by chrisfah on 2008-02-16
Hi, I am a new user and new to the forum.  I recently installed version 7.1 OS and I cannot connect to my network to get to the Internet. It states there is no network connection detected with my ethernet Compaq Netelligent 10/100 TX PCI UTP.  In the past (with other OS)  I had to set the speed to 10/Full duplex to get an IP from my router but don't know how to do it.  I have tried with ifconfig options but no luck.

Thx,
Chris

---

### Post by jan quark on 2008-02-16
if you are using a cable connection read though this guide
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

it would be also good if you could post the output of these terminal commands to clarify your network status 

thank you

```

iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```

```
lspci
```
```

sudo lshw -C network
```

---

### Post by mrsteveman1 on 2008-02-16
ethtool is what you can set ethernet configs with

```

ethtool -s eth0 speed 10 duplex full autoneg off
```

will set eth0 to 10/full and turn off autonegotiation

---

