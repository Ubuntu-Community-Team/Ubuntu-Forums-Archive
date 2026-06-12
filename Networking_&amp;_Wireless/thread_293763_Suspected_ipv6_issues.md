---
title: "Suspected ipv6 issues"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by matt_b on 2006-11-05
I have 6.06 installed on a Sony TR1MP laptop, and initially had many connection issues with my wireless D-link G604T router. Basically I connected fine to the router but could not browse using firefox. I could do everything via terminal (ping, telnet, traceroute, apt-get update), but FF and package manager GUI would not connect. I read a few posts on disabling ipv6, which I followed like so:
[LIST=1]
[*]Created a blacklist-ipv6 file in /etc/modprobe.d/ containing "blacklist-ipv6"
[*]created a bad_list file in the same directory containing "alias net-pf-10 off"
[/LIST]
Once this was done, I rebooted and firefox got out on the web just fine, browsing is no problem. However, neither the "software updates" GUI nor the "Add/Remove Applications" GUI will get out on the web - both of them time out. Software updates reports "failed to download the list of changes. Please check your internet connection" and upon attempting to download Pan Newsreader Add/Remove reports "Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnet/libgnet2.0-0_2.0.7-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnet/libgnet2.0-0_2.0.7-1_i386.deb) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0) connection timed out". (The link to libgnet works in FF).

Is there something further I need to do to disable ipv6 (if this is what's causing me problems)?

Thanks for helping a n00b!

---

### Post by mips on 2006-11-05
First, remove the **gb.** part in your sources list.

Next do a search in this forum for d-link or 604T and you will find some stuff.

---

### Post by matt_b on 2006-11-06
Thanks for the tip - it seems my router needed a firmware update, after that all of my network issues have gone away :)

---

### Post by mips on 2006-11-06
> **matt_b said:**
> Thanks for the tip - it seems my router needed a firmware update, after that all of my network issues have gone away :)


Yea, that usllualy does the trick

---

