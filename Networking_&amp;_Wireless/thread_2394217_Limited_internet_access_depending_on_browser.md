---
title: "Limited internet access depending on browser"
date: 2018-06-14
forum: Networking &amp; Wireless
---

### Post by joene2 on 2018-06-14
Hi,

I'm on 16.04 and every thing working fine for several years.
Since few days, i have a weird issue with internet access (wired) :

- I can access to my internal network,
- Others devices on my internal network have full access to the internet,
- On my specific Ubuntu PC (16.04), i have no access to internet (Firefox, Chromium, Opera, etc.) but *only* with "Tor browser". Command line is not working with sudo apt-get upgrade as it can not download librairies from the internet.
- I have no access to the internet from all virtual system hosted in my Ubuntu PC


Any clues will be appreciated.
Thx
______________________________
FYI : ifconfig
eno1      Link encap:Ethernet  HWaddr c8:60:00:c2:f7:b0  
          inet adr:10.0.0.7  Bcast:10.0.0.255  Masque:255.255.255.0
          adr inet6: fe80::7625:ae3c:5eb8:2974/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:40397 erreurs:0 :0 overruns:0 frame:0
          TX packets:24346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:47732305 (47.7 MB) Octets transmis:10558508 (10.5 MB)
          Interruption:20 Mémoire:f7f00000-f7f20000

---

### Post by joene2 on 2018-06-14
Bump

---

