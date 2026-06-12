---
title: "apt-get update not able to get repositories"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by neilbmehta on 2007-06-17
I have just installed Ubuntu (dapper) and was attempting to update using synaptice (and apt-get) howver it was unable to find any of the repositories I believe it is having a problem resolving the url.
My internet connection is through the net-gear wgr614 v6. My internet connection works fine as shown by the ifconfig file below.

eth0 Link encap:Ethernet HWaddr 00:01:03:1E:66:C4
inet addr:192.168.1.138 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4950 errors:0 dropped:0 overruns:1 frame:0
TX packets:3569 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:6348368 (6.0 MiB) TX bytes:364177 (355.6 KiB)
Interrupt:11 Base address:0x6000

The command sudo apt-get update gives the following result.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Connection failed [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Connection failed
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg
Connection failed [IP: 88.198.37.77 80]
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Connection failed [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Connection failed [IP: 91.189.89.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Connection failed [IP: 88.198.37.77 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Connection failed [IP: 81.169.138.125 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Connection failed [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Connection failed [IP: 91.189.89.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Connection failed [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...er/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...er/Release.gpg) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...es/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...es/Release.gpg) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ts/Release.gpg](http://archive.ubuntu.com/ubuntu/dis...ts/Release.gpg) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://packages.medibuntu.org/dists/dapper/Release.gpg](http://packages.medibuntu.org/dists/dapper/Release.gpg) Connection failed [IP: 88.198.37.77 80]
Failed to fetch [http://archive.canonical.com/ubuntu/...al/Release.gpg](http://archive.canonical.com/ubuntu/...al/Release.gpg) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/...86/Packages.gz](http://packages.medibuntu.org/dists/...86/Packages.gz) Connection failed [IP: 88.198.37.77 80]
Failed to fetch [http://archive.canonical.com/ubuntu/...86/Packages.gz](http://archive.canonical.com/ubuntu/...86/Packages.gz) Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.88.31 80]Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) Connection failedFailed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://packages.medibuntu.org/dists/...86/Packages.gz](http://packages.medibuntu.org/dists/...86/Packages.gz) Connection failed [IP: 81.169.138.125 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) Connection failedFailed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...86/Packages.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz](http://archive.ubuntu.com/ubuntu/dis...rce/Sources.gz) Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) Connection failed
Reading package lists... Done

Any help would be apreciated. Thanks.

---

### Post by zvacet on 2007-06-18
Do you have all repositories open?If you don´t look here

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

After that replace your source list with this one

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")

---

### Post by neilbmehta on 2007-06-20
The problem is synaptic or apt-get are not able to connect to the internet....Due to that I am not able to open my repositories as well....I think its a networking problem.  I connect to the internet through a router which I believe is the cause of the problem. I have even modified my /etc/hosts file and given the IP address of the repositories but to no avail. I have also tried going on a static IP connection instead of DHCP and directly given DNS of IP provider. Even my IPV6 has been disabled. Despite that I seem to be having problems.

---

### Post by corax on 2007-06-20
Hi !

I think it is a network issue if you get a network address from your router it doesn't mean anything !
Do you have a connection from your router to your ISP ? Is firefox working ? Can you browse the web ?

I can ping the repository 88.198.37.77 for example so try to ping it first (ping -c 4 88.198.37.77) if it is working then your network is fine (only the DNS lookup can be wrong but as you see the program tries to connect an IP address so I assume the lookup works ... )

Good luck !

---

### Post by neilbmehta on 2007-06-20
Yes im able to browse the internet.....ping, firefox, gaim all work well...i even tried to ping the repositories...that works well also....

---

### Post by corax on 2007-06-21
Have you tried to connect without router ? Maybe the router refuses your connections ...
For example :

1, In my case on wireless interface the router (Netgear WGT624) can't handle more than 100 connection at a time (on wired I haven't experienced such an issue).

2, If synaptic sends request to all the repositories at the same time maybe your router considers it as a DDOS attack and refuses all the connections form your host for a specified amount of time.

...

Try to skip the router and connect directly to the cable / xDSL line if it works then you have to tweak only your router ... if not you have to tweak your machine (and maybe your router).

(If you have problems connecting through xDSL read this : [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

good luck ! :)

---

### Post by neilbmehta on 2007-06-22
Thanks for the help...I figured out the problem.....It was with the router config...It was blocking the repository sites....I had to diable the config for my router....

---

