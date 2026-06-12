---
title: "Fritz box DNS"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Palmstroem on 2008-08-11
Hello Ubuntu friends,

following problem: I am running Kubuntu, Ubuntu (Hardy), and Windows from several PCs, all of them connected to an AVM Fritz Box DSL FON WLAN 7113. The box works as router with dhcp and dns.

BUT: only the Windows PCs get their names resolved and can be pinged by name. On the Ubuntu PCs I have set hostname, hosts, and, as someone advised in this forum, the "send host-name "myhostname"" in dhcp.conf. Nevertheless, it does not work.

Any ideas? Can someone explain to me how the Fritz box gets the computer names?

---

### Post by Palmstroem on 2008-08-12
The solution was already posted on a German wiki. Here it is:

Open (with root privileges) the file /etc/dhcp3/dhclient.conf, un-comment and correct the two lines:

send host-name "pc-name";
send dhcp-client-identifier 00:00:00:00:00:00;

pc-name should be your PC's name and 00:00:00:00:00:00 the relevant MAC address (i.e. from eth0 or wlan0 etc.) which you may probe with ifconfig.

Voila! That's all! Works fine! Enjoy!:)

Don't know why this feature isn't enabled by default, maybe security reasons...

---

