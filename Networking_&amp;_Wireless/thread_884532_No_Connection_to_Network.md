---
title: "No Connection to Network"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by Webstyler on 2008-08-09
Hi,

I have build up my own Home Server with a Intel D945GCLF Board. [Intel ]("http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm")

My Problem is that the onboard network card does not work always. First it worked a few days. Then not. I reinstalled Ubuntu Server 8.04. And it worked. Today is broken again.

I try to PING the Gateway but.... :

```
ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.10 imcmp_sec=1 Destination Host Unreachable
From 192.168.1.10 imcmp_sec=2 Destination Host Unreachable
From 192.168.1.10 imcmp_sec=3 Destination Host Unreachable
...
```

I use a static ip configuration:

/etc/network/interfaces

```
auto eth0
iface eth0 inet static

adress 192.168.1.10
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255
netmask 255.255.255.0
```

if DHCP same result

(ethtool say Link detected: yes)

please help me! :confused:

PS: No Windows installed. (Because wake on lan)

---

### Post by tomy4ever on 2008-08-09
i have the same problem just im not using a server >.> 
i get the same display it's pinging and gets "host unreachable" 
i've got a windows partition though, with which i can use internet so the card is working

thx for any help

---

### Post by Webstyler on 2008-08-09
may be you have the wake on lan problem.

windows shuts the card down and linux dont get in on

try to enable the wake on lan funktion in the windows control panel

may that work (i read this in other forums)

good luck

---

### Post by tomy4ever on 2008-08-09
i have the wake on lan thing enable in my BIOS, is that what u mean?

---

### Post by Iowan on 2008-08-09
> **Webstyler said:**
> 
iface eth0 inet static

[COLOR="Red"]adress[/COLOR] 192.168.1.10
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255
netmask 255.255.255.0

Probably not the issue (cuz ping shows correct address), but try it as  "address".

---

### Post by Webstyler on 2008-08-09
Hi,

@tomy4ever

no try in windows the device manager. in the settings for the network card you have to enable wake on lan function. (Otherwise try google "network windows wake on lan" or so

@Iowan

no it is correct i had copied it by hand. thats very diffucult :lolflag:

@the rest of the world help me please!!!! THX :) :( :confused:

---

