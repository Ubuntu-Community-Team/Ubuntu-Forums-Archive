---
title: "IBM Thinkpad network problems"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by zachtib on 2005-08-21
I just installed Ubuntu 5.04 onto my R51 IBM Thinkpad,
All three of the network card, wireless card, and modem seem to be detected (they appear in the networking dialog) but I can't get them to work.
I went and configured and activated the wired card (don't have access to wireless yet, my university is "working" on a linux client for the wireless)
I got an ipv6 address, which did me no good.  Then I disabled ipv6 and rebooted, now I get no address.
Any ideas as to what is wrong?

---

### Post by heimo on 2005-08-21
We need more information.

What happens if you run 
 ```
sudo dhclient eth0
``` (assumes your wired card is eth0, check with ifconfig)

---

### Post by zachtib on 2005-08-21
[QUOTE=heimo]We need more information.

What happens if you run 
 ```
sudo dhclient eth0
``` (assumes your wired card is eth0, check with ifconfig)[/QUOTE]
 ```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval X
No DHCP offers received
No working leases in persistent database - sleeping
```

---

### Post by heimo on 2005-08-21
And you know that it should be using DHCP? Seems like everything would be working on your end, but no DHCP server is answering.

You can try dhclient3. I don't know if it's installed by default or available on install CD, it's in package dhcp3-client.

---

### Post by zachtib on 2005-08-21
[QUOTE=heimo]And you know that it should be using DHCP? Seems like everything would be working on your end, but no DHCP server is answering.

You can try dhclient3. I don't know if it's installed by default or available on install CD, it's in package dhcp3-client.[/QUOTE]
 yeah, I'm using dhcp, and the network worked fine with SuSE earlier

---

### Post by zachtib on 2005-08-22
ok, now it seems that NO linux distro can connect to the network

could it be a problem with my University's Network?

---

### Post by Talomon on 2005-08-22
I'm running a IBM Thinkpad R40 on ubuntu and the wireless works great if I don't mess around with it. =) 

I had the same kinda problem when I tried to connect to the university network. When I tried to connect with my wireless card, dhclient would try to get an IP without any luck.

I managed finally to connect by giving the wireless card an essid, by typing "iwconfig eth0 essid Your_Essid". That worked like a charm, dhclient fount an IP and everybody was happy.

I don't know if your problem is that simple...I'm still new to the whole linux experience so for me everything is news. =)

---

