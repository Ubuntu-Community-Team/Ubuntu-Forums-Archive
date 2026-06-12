---
title: "Probem with ethernet card"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by odwyerda on 2008-04-18
Having a real problem here I need to give a mate back his laptop, he ruined it because of windows and IE and too much porn with out protection so I wiped it and was planning to give him a nice new Ubuntu desktop to spread the word and also to protect him from himself on the internet.

1 problem cannot access internet at all.
Doesnt do anything when i plug in and out the cable
Packard Bell Easynote E2560
Ethernet board is 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem controller
ifconfig is attached as a jpg

---

### Post by chili555 on 2008-04-18
What happens when you connect the wire and do:```
sudo dhclient eth0
```Also, when I look at RX bytes and TX bytes, it looks like you have been connected pretty well!

Are you expecting it to just grab an IP address as soon as you connect the wire? Are you using NetworkManager? What does:```
cat /etc/network/interfaces
```look like?

---

### Post by dstew on 2008-04-18
Looks like it is working. Is says you got 800 Mb of received data. But, there is not IPv4 address. How is it set up? Post the output of```
cat /etc/network/interfaces
dhclient eth0
```
EDIT: OK, chili and dstew sharing a channel...lol

---

### Post by chili555 on 2008-04-18
Looks like we posted virtually simultaneously!

---

### Post by sdowney717 on 2008-04-18
DNS server settings?
does it have a DNS server assigned?
If you can ping the numbered octets but cant ping the name, you dont have a DNS server assigned

scott@scott-desktop:~$ ping en.wikipedia.org
PING rr.pmtpa.wikimedia.org (208.80.152.2) 56(84) bytes of data.
64 bytes from rr.pmtpa.wikimedia.org (208.80.152.2): icmp_seq=1 ttl=55 time=37.3 ms

scott@scott-desktop:~$ ping 208.80.152.2
PING 208.80.152.2 (208.80.152.2) 56(84) bytes of data.
64 bytes from 208.80.152.2: icmp_seq=1 ttl=55 time=37.3 ms
64 bytes from 208.80.152.2: icmp_seq=2 ttl=55 time=37.3 ms
64 bytes from 208.80.152.2: icmp_seq=3 ttl=55 time=36.0 ms
64 bytes from 208.80.152.2: icmp_seq=4 ttl=55 time=35.5 ms
64 bytes from 208.80.152.2: icmp_seq=5 ttl=55 time=35.5 ms

--- 208.80.152.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 35.562/36.373/37.332/0.825 ms
scott@scott-desktop:~$

---

