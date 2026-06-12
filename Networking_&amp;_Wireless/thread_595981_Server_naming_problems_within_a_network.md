---
title: "Server naming problems within a network"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by popvulture on 2007-10-29
Hi,

I am setting up a server to develop a website within my company's network. I have installed Ubuntu Server 7.10, and named it stagingserver. I am not able to access this when I enter [http://stagingserver](http://stagingserver) into my browser. 

The IS team has opened the network so that this is feasible, and I have DHCP enabled, but I am unable to use the name (and therefore allow my bosses to access it).

Help!

---

### Post by Synflux on 2007-10-29
Hello,

Depending on what name resolution you're using (DNS or netbios) it might be worth going through the steps in here:

[http://ubuntuforums.org/showthread.php?t=190542&highlight=firestarter+real+story](http://ubuntuforums.org/showthread.php?t=190542&highlight=firestarter+real+story)

I had the same problem and it worked for me. Of course, it only helps if you're using firestarter to control your firewall. The basic idea is that netbios uses broadcasts to find hosts by name but iptables blocks these because of SPI rules. I think! :)

---

