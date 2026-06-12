---
title: "WEP info in INTERFACES file"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by flowersrj on 2007-03-31
Hi,

Trying without success to connect with WEP at startup in Feisty Fawn.  If WEP is turned off in my Linksys router then it automatically connects.  Interface file is as follows:

- - - - - - - - - - - - - - - - -

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.1.198
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ourplace
wireless-key 85c7f5bce1b75647788c4959c07397a86fdb4239

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

 - - - - - - - - - - - - - - -

I thought the 2 wireless entries for eth1 would allow me to skip having to log in.  I have noticed that the network manager disables the CONNECT button after I have typed 1/4 the length of my hex key but don't know why.  

Thanks for looking,
Rich

---

### Post by spd106 on 2007-04-02
WEP hex keys are only 10 or 26 digits in length, depending on whether you are using 64bit or 128bit WEP. 

Each character represents 4 bits, see [wikipedia]("http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy")

---

