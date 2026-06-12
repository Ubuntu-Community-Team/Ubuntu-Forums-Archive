---
title: "Execute script on connection"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by PsYcHo_SiB on 2008-01-14
Hi,

I would like to know if it is possible to execute a script when I'm connecting to my home wireless network. I would like to automatically mount some network share when I'm at home on my wireless network.

Thank You

---

### Post by sqrt2 on 2008-01-14
When an interface is brought up, everything in /etc/network/if-up.d is executed. So, what you also need is a way to detect your network.

You're saying that you want to connect to a network share. If this share is a Windows share, you could try parsing the output of "nmblookup <NetBIOS name>" to see if the computer hosting the share exists on the network.

---

### Post by PsYcHo_SiB on 2008-01-14
Okay thank you,

Ill try to cook a quick shell script with that information.

---

### Post by kevdog on 2008-01-14
Having an interface brought-up is much different than establishing a connection.  Im not sure where to put your script.

---

### Post by sqrt2 on 2008-01-14
It seems that at least the KDE network manager uses ifdown/ifup when connecting to a network. Makes sense to me, since it also has to take care of DHCP etc.

---

