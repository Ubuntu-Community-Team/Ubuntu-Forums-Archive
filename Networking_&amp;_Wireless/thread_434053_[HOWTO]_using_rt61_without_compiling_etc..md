---
title: "[HOWTO] using rt61 without compiling etc."
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by conloos on 2007-05-05
Hi,

i spend two days to get my rt61 working without recompiling etc. Now it works stable ...

First use [apt-get/ aptitude / adept] to install the 368 version of the kernel (better remove the generic or 686).

```

apt-get install linux-headers-386 linux-image-368 linux-restricted-modules-368 
apt-get remove [all generic or 686 stuff]

```

To connet my accesspoint i modified the /etc/notwork/interfaces:

```

auto lo
iface lo inet loopback


iface ra1 inet dhcp
pre-up /sbin/ifconfig ra1 up
pre-up /sbin/ifconfig > /tmp/test.out
pre-up echo "--- schnipp ---" >> /tmp/test.out
pre-up /sbin/iwconfig >> /tmp/test.out
pre-up echo "--- schnipp ---" >> /tmp/test.out
pre-up /sbin/iwpriv ra1 set SSID=[YOUR-ESSID] 
pre-up /sbin/iwpriv ra1 set NetworkType=Infra
pre-up /sbin/iwpriv ra1 set Channel=11
pre-up /sbin/iwpriv ra1 set AuthMode=SHARED
pre-up /sbin/iwpriv ra1 set EncrypType=WEP
pre-up /sbin/iwpriv ra1 set DefaultKeyID=1
pre-up /sbin/iwpriv ra1 set Key1=[YOUR-KEY]
pre-up /sbin/iwpriv ra1 set TxRate=0
pre-up /sbin/iwconfig >> /tmp/test.out
pre-up /sbin/ifconfig >> /tmp/test.out
auto ra1

```

---

### Post by cyberlion on 2007-06-09
What the version of Ubuntu of this how-to?

---

### Post by conloos on 2007-08-08
this howto is for feisty

greets con

---

