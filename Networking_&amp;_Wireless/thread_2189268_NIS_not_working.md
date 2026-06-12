---
title: "NIS not working"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by pinolo on 2013-11-21
In a local network, where a NIS server and some NIS clients are correctly working, a new installed ubuntu 12.04.3 machine seems not to like NIS. When NIS is not installed the network drive is mounted correctly on that machine, I have web access and so on. If I install nis on this machine, and do the following tasks

[LIST]
[*]set the right dominion /etc/defaultdomain -> XXXXXX)
[*]check that nis is included in /etc/nsswitch.conf
[*]add the following line to the file /etc/pam.d/common-auth
[*]auth  optional pam_group.so
[/LIST]
nothing works anymore: when I reboot, the lightdm doesn't start, a shell shows the message "mountall disconnected from plymouth", no network user can login, and only the local user can login, but it is veeeery slow.
Any idea?
Thank you!

---

