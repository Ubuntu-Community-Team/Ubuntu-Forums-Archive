---
title: "SONOS music system refuses to talk to my PC"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Music Alan on 2008-05-29
A recently purchased SONOS system will communicate readily with the Internet via a Netgear DG834G router (Napster is working fine), but fails utterly to communicate with my PC running Kubuntu 7.04. I have edited my smb.conf and added the following to the end.

[INDENT][musicshare]
path = /home/alan/Audio
read only = yes
printable = yes
guest ok = yes[/INDENT]

I have left the rest of the default smb.conf file as-is. I have done chmod 755 for my music folder.

Entering the Hostname "Eddie" on the SONOS controller, together with my login name and password returns the result "The computer eddie cannot be found". Using the IP address 192.168.0.2 returns "The computer 192.168.0.2 refused to let the ZonePlayer connect to it"

Any ideas where I might be going wrong?

---

### Post by RoadKill1313 on 2008-05-30
Try chmod -R 755 on your /home/alan/Audio directory.

-RK

---

### Post by Music Alan on 2008-05-30
chmod 755 has already been done (I have also tried chmod 777 although I hadn't expected that to be any different.)

---

### Post by Music Alan on 2008-05-30
To clarify. I did use chmod **_-R_** 755

---

