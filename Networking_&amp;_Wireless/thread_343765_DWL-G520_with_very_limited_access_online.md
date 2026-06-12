---
title: "DWL-G520 with very limited access online"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by General Plot on 2007-01-21
I have a Dlink DWL-G520, which installs fine and is able to detect router SSID and obtain an IP on the wireless LAN. However, most sites (yahoo, google, etc....) will simply not open at all, as the browser either comes up blank or says it was unable to connect. Strangely enough, I can open this site (any links on ubuntu.com work, etc..). I've been messing with this for hours and can't sort it. If anyone has any info, I'd sure appreciate it. Thanks in advance.:)

---

### Post by Polygon on 2007-01-21
i dont think its the card at fault, as i have that exact same card (dlink g520) and internet works fine for me. It was configured out of the box, and i have yet to run into a site that has not worked for me..


maybe try reseting your router (as in unplug it, wait ten seconds then plug it back in), i find that solves 99% of my wireless internet problems.

---

### Post by mindwarp on 2007-01-21
[LIST=1]
[*]Post the output of "sudo route -n"
[*]Post the output of "ping www.yahoo.com"
[*]Post the output of "sudo traceroute www.yahoo.com"
[*]Post the output of "cat /etc/resolv.conf"
[*]Post the output of "ifconfig wirelessdevicename"[/LIST]

---

