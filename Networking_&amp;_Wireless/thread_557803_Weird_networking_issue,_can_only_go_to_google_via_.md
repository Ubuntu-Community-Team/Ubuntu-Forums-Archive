---
title: "Weird networking issue, can only go to google via ip"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by chembro84 on 2007-09-23
Hello, I just installed 7.04, I am using an AMD x2 in 32-bit mode on a a33g motherboard (using onboard ethernet).  I also have a befw11s4 router (DMZ enabled on the port I'm using)

First when I installed I couldn't even install all the way because once it got to checking the apt mirrors, it'd hang forever, so I went into the BIOS and disabled the LAN to get it to even install.  

So I get it installed, Ubuntu detects my network adapter, but I can't ping anything (but it does resolve the domain name).  I can't go to any website that I type by name, but google does work if i put the ip in directly, but not every site works this way.  I have tried setting a static IP and disabling IPv6, still doesn't work right.  I've even tried setting my DNS to OpenDNS, still doesn't work.

Anyone have any idea??? Thank you very much!

---

### Post by noob12 on 2007-09-23
Check you name servers listed in **/etc/resolv.conf** and make sure you can ping them.  If your router is listed as the DNS server, it may not be a reliable proxy.

You may find this thread helpful:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by chembro84 on 2007-09-24
It is very weird I can ping my DNS servers (I use OpenDNS), and I can ping google and yahoo, but when I try to go to those sites in firefox, they don't work (neither does apt-get or synaptic)

---

### Post by noob12 on 2007-09-24
Can you post the output of these:

```

cat /etc/network/interfaces

cat /etc/dhcp3/dhclient.conf

cat /etc/resolv.conf

cat /etc/nsswitch.conf

```

---

