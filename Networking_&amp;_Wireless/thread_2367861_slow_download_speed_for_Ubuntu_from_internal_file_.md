---
title: "slow download speed for Ubuntu from internal file server"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by giobaxx on 2017-08-04
hello guys

We have some some problems with the download speed on ubuntu from an internal file server used to share ISO and application in general. We have windows and Ubuntu Workstation and from window we don't have problems. it downloads ISO in less then a minute. With ubuntu the download start... come slower and slower(6 kb/sec) and the fail. we download by https.

I suppose the problem is a network problem, probably a firewall configuration, but before to talk with the networking guys, you have idea what problems could limit the download speed  on linux  and not on windows?

Tanks GIO

---

### Post by BenginM on 2017-08-04
Hiya , on wired or wireless connection ..!

which network cards in use ..

lspci | egrep -i --color 'network|ethernet' 

consider following [this sticky thread]("https://ubuntuforums.org/showthread.php?t=370108")

---

### Post by giobaxx on 2017-08-04
wired card....

05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)

From what i saw this happened to all ubuntu workstation we have. The download start at fast speed as in Windows...then start to slow.....till fail...

this make me think that the problems is related to something on the networks site, just few minute ago i tried to download the iso of ubuntu desktop from ubuntu site and seems to works.
If i try from our internal server.....no.

I'm just curious, if is a firewall configuration why it affect only ubuntu.....and not windows...

---

### Post by BenginM on 2017-08-04
well if  the connection is working fine on the desktop , then it's some miss configuration on the internal server .. is it connecting through a proxy server/VPN ?

which driver in use for the Broadcom..

is the card Duplex mode, set to "full, 100" . see $ inxi -Nn

how is the server connection configured static IP, DHCP , using network manager , or ..

do you mind sharin' 

$ cat /etc/lsb-release; uname -a

$ ifconfig -a

On the server what entires are in $ cat /etc/network/interfaces

---

### Post by giobaxx on 2017-08-06
I will ask... but i don't thin there is any proxy/VPN. Is only an internal server in a different VLAN. Every Workstation with ubuntu has the same problems so i don't think is a river problem, even because if i tried to download from internet i don't have that problem and more this problems is not happening to the Windows workstation.

So i'm curios what configuration on firewall could affect only Ubuntu(or linux distro) and not windows.

---

### Post by BenginM on 2017-08-06
how would we know of your systems firewall configurations ..!

[https://ubuntuforums.org/showthread.php?t=1871177](https://ubuntuforums.org/showthread.php?t=1871177)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by giobaxx on 2017-08-07
My collegue that work on linux side will come back soon and i will ask to him. i don't have access to the server, but i think that the problem could be the Cisco Firewall.....and i'm still confused why afftect only linux and not windows.
I can investigate only linux client....but really and don't know what i can do...

---

### Post by BenginM on 2017-08-07
So far , you haven't provided us with your system setup / configuration .. Are these machines happens to be located somewhere in Asia, India, Pakistan  ..!

---

### Post by giobaxx on 2017-08-07
I cannot access to the server, i don't have enough right and i have to wait my collegue.....for the client, they are build with a clean installation and the firewall is disabled......

---

