---
title: "Slow Internet Connection"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by Klimax on 2005-04-09
I have been running Ubuntu for about a week now, and there's something bothering me: connecting to other computers is awefully slow for me - but that's it, once I'm connected I have fast internet, about 1.5x times as fast as my windows partition.
Can somebody help me please? Because internet this slow is really bothering me - in some cases it's slower than 56k.

---

### Post by Suvarin on 2005-04-09
[QUOTE=Klimax]I have been running Ubuntu for about a week now, and there's something bothering me: connecting to other computers is awefully slow for me - but that's it, once I'm connected I have fast internet, about 1.5x times as fast as my windows partition.
Can somebody help me please? Because internet this slow is really bothering me - in some cases it's slower than 56k.[/QUOTE]

Check what nameservers (DNS-servers) you use in windows and Linux. In Linux these settings are stored in /etc/resolv.conf (Places -> Computer -> Fileystem -> /etc -> resolv.conf).

My first bet is that you have windows configured to fall back on a secondary nameserver if the first one is slow.

Some people have also reported increased speed (particularly with opening connections in Firefox) after disabling IPv6.

---

### Post by Klimax on 2005-04-09
I searched the forums on disabling IPv6, and now I have set ipv6_disable to true in FF. Thanks alot, connecting now is loads faster :) As long as I get past Looking up... I guess this is a DNS problem, and I'm gonna reboot into XP now to see if there are any differences in my DNS lists.

EDIT:
I changed the order of my DNS list, and everything is working fine now, thanks! :)

(can a mod close this topic now then?

---

