---
title: "Verständnisfrage OpenVpn, ssh und ListenAddress"
date: 2019-01-21
forum: Networking &amp; Wireless
---

### Post by anutosho on 2019-01-21
Hallo zusammen
Ich habe ein Netzwerk (Netzwerk 1 mit Host 1..n) auf dem ein OpenVPN-Server läuft und ein anderes Netz (Netzwerk 2), von dem aus einzelne Rechner (Client 1..n) mittels VPN auf alle Rechner im Netzwerk 1 zugreifen können. Der VPN-Server läuft auf Host 1)
Alle Rechner im Netzwerk 1 hängen direkt im Internet (es handelt sich um Webserver).

ssh soll aber nur für Rechner aus Netzwerk1 und aus Netzwerk 2 erreichbar sein, nicht aus dem Internet.

Wie stelle ich das am besten an? ListenAddress, /etc/hosts.allow, ... ?
Netz 1 hat die ip 192.168.1.0/24, Netzwerk 2 hat 192.168.2.0/24 und die tun devices der OpenVPN-clients haben 10.10.1.0/24

Was wäre da jetzt auf den Servern von Netz 1 einzutragen?
Meine Vermutung:
ListenAddress 192.168.1.x
ListenAddress 10.10.1.x

Das Problem dabei:
192.168.1.x ist ja auch von "aussen" sichtbar und die vpn-Addresse 10.10.1.x gibt's ja nur bei den Clients im Netzwerk 2. Im Netzwerk 1 ist dieses Netz ja nur dem OpenVPN-Server bekannt. Die Rechner im Netzwerk 1 sollen aber auch untereinander Kommunizieren (bzw. ssh Verbindungen aufbauen) können.

Kann mir da mal jemand auf die Sprünge helfen?
Muss man da IPtables bemühen oder kriegt man das auch so hin?

Danke, Paul

---

### Post by praseodym on 2019-01-21
Hi,

this is an English Forum, please post again or go to

[https://forum.ubuntuusers.de/](https://forum.ubuntuusers.de/)

---

