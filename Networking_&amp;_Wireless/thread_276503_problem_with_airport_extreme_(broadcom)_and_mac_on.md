---
title: "problem with airport extreme (broadcom) and mac on linux ?"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by techrush on 2006-10-13
im dual booting my powerbook and everything was great until suddenly my wireless stopped working. 

i installed the firmware with the .deb packages from this site:

[http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/dapper-cafuego/bcm43xx/)

i then installed wifi-radar and it detected my network immediately and everything was good.

now when i open wifi radar i can see my network and it even says i have an IP from my router but i cant ping out or anything. ive tried some of the tricks on this wiki to get it going with no luck...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-d0946e95811e2999580f6073e165fa66c3709f01](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-d0946e95811e2999580f6073e165fa66c3709f01)

the only major changes i made to my system recently was installing the mac on linux virtual machine using this tutorial 

[https://help.ubuntu.com/community/MacOnLinuxHowto#head-11a36cac4a033ef4bef636c1979016be90ac89b8](https://help.ubuntu.com/community/MacOnLinuxHowto#head-11a36cac4a033ef4bef636c1979016be90ac89b8). 

To get networking enabled within the virtual machine i had to install the following packages: ipmasq dnsmasq dhcpd


im wondering if these caused my problem......
for now im off to bed but any help would be -greatly- appreciated

---

### Post by techrush on 2006-10-13
i geuss writing thsi post kind of helped me walk through the issue. i removed the networking apps that i had installed for mac on linux and now everything is working fine. 

i just need to figure out how to setup internet access on mac on linux without dhcp.

---

