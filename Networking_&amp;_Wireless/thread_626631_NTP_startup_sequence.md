---
title: "NTP startup sequence"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by ccprog on 2007-11-29
I have a problem with startup sequences that result in a failure to get NTP runing. The goal is easy enough: a single machine (Gutsy in single user mode) to be synchronized with external servers.

My computer, included its DSL router sits on a switchable power outlet and gets booted simply by turning power on. As a result, the DSL box in its role as DHCP server is not immediately available, and thus it takes a few seconds longer since the eth socket is connected.

Unfortunately, ntpd starts before this sequence is completed and it can connect to its interfaces. As far as I can make out, ntpd itself is runing, but when ntpdate tries to synchronize, it fails. Only  5 minutes later, ntpd establshes its connection to eth, but does not associate with the external servers:
```
Nov 29 14:25:33 Copernicus ntpd[5949]: unable to create socket on eth0 (5) for fe80::210:5aff:fe5b:e0a9#123
Nov 29 14:25:33 Copernicus ntpd[5949]: failed to initialize interface for address fe80::210:5aff:fe5b:e0a9
(DHCP starts at this point)
Nov 29 14:25:51 Copernicus ntpdate[6741]: the NTP socket is in use, exiting
Nov 29 14:30:33 Copernicus ntpd[5949]: Listening on interface #6 eth0, fe80::210:5aff:fe5b:e0a9#123 Enabled
Nov 29 14:30:33 Copernicus ntpd[5949]: Listening on interface #7 eth0, 192.168.178.21#123 Enabled
```
This is the last log entry. I have attached a longer excerpt from daemon.log below

ntpq gives back:
```
root@Copernicus# ntpq -p
No association ID's returned
```

A manual restart of ntpd at this point gets everything runing correctly.

How could I delay the start of ntpd, or schedule a later restart?

---

### Post by md2020 on 2007-11-29
I have the same issue except mine is due to my USB LAN card not starting up completely before NTP starts. Therefore I have to restart NTP to get it to connect. I have looked into having NTP start up later as well. Here is a link to another thread that describes how to change the order of startup programs. [http://ubuntuforums.org/showthread.php?t=231059]("http://ubuntuforums.org/showthread.php?t=231059")
I have not messed with it myself yet.

Several months ago when I first encountered this issue, I stumbled upon a discussion about future changes to the NTP daemon that would resolve this issue. Basically they were talking about making it smart enough to know that when it does not have a connection, it will connect automatically after a connection is established on the LAN card. Should I find that again I will post the link here. Obviously it is not fixed yet.

Found another thread with the same kind of play on startup scripts specifically dealing with NTP:  [http://ubuntuforums.org/showthread.php?t=17654]("http://ubuntuforums.org/showthread.php?t=17654")

Another option to fix is here: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505]("https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505")
After reading this I think I will attempt to modify the "enter" and "exit" hooks of DHCP. Seems to be a cleaner way to go. I am sure there are probably several other methods available.

---

### Post by ccprog on 2007-11-30
Especially the last link was helpfull, thanks for that. My main conclusion is this: there are a lot of issues that influence which of the different solutions work. As I understand it there are two main variants:

1. Moving "_/etc/dhcp3/dhclient-enter-hooks.d/ntp_" to "_/etc/dhcp3/dhclient-exit-hooks.d/ntp_"
For me, that resolved nothing. The NTP startup still happened before the network interfaces were ready. But also in the case it works, you still depend on your DHCP server passing on the adresses of the NTP servers. If the server is or can be configured that way, you next have to check that the DHCP client is listening. 
Check _/etc/dhcp3/dhclient.conf_; the "request" command needs to have "ntp-servers" in its list of parameters.

2. Set the NTP server entries to "dynamic"
If the DHCP cannot pass the NTP server adresses, you depend on those listed in /etc/ntp.conf. Labeling them as dynamic enables a configuration without an actual connection, delaying that for a later point in time.
Every "server" line in _/etc/ntp.conf_ should look like this:
```
server ntp.ubuntu.com dynamic
```
Unfortunately, this does not work immediately. Since the network interface is not up, there also is no DNS, and the configuration fails again. You can tackle that in two ways. Either you install a proxy DNS ([http://packages.ubuntu.com/gutsy/net/pdnsd](http://packages.ubuntu.com/gutsy/net/pdnsd))  - which has to be configured, then, by hand! -, or you exchange the NTP server adresses with their IP adresses, like this:
```
server 91.189.94.4 dynamic
```

This is what I have done in the end, and it works, albeit it takes some time. Synchronization finally started ca. 10 minutes after bootup.

---

