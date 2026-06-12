---
title: "Internet sharing and firewall???????"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by drakulaj on 2005-11-12
Heloo.
as first im totally **LAMA**. I need help to configure my PC with Kubuntu to internet sharing and how to setup firewall ( if there is? ). I would like to use my PC as internet routr for my local network ( Windows OS is not so much secure :) ) I have DSL modem with DHCP servr. I guess that i need some DHCP servr and proxy? 

Jirka :confused:

---

### Post by mips on 2005-11-12
I would suggest running Firestarter, can be installed from Synaptic. Firestarter allows for internet connection sharing. From there you can configure the one Ethernet card for Internet access and the other for your local LAN, where it will assign DHCP, DNS etc to the clients on the local LAN.

The documentation on the website [http://www.fs-security.com/](http://www.fs-security.com/) is pretty good.

Or have a look here:
[http://ubuntuforums.org/showthread.php?t=88294](http://ubuntuforums.org/showthread.php?t=88294)
[http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)

The above is written for wireless but in effect there is no real difference between wired and wireless.

---

### Post by drakulaj on 2005-11-12
hmm i have big problem with SUDO, after my first reboot it want akcept ny password anymore. I can login but i cant using SUDO. I have KUBUNTU.

---

### Post by mips on 2005-11-12
The sudo password should be the same as your user passwd ?

---

