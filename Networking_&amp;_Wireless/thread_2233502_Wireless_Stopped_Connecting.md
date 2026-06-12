---
title: "Wireless Stopped Connecting"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by tucker5 on 2014-07-08
I am using Ubuntu 14.04 on a Desktop, with a Netgear N-150 USB adapter, and all of a sudden Ubuntu refused to connect.

My wi-fi was working without a hitch and then I left my house for a few days and upon returning the wireless stopped connecting. I don't rember making any changes before I left. It tries to connect for a while, but then returns to showing that I am disconnected. I tried removing the WPA2-PSK, and updated but still nothing. Ethernet works fine though. All of my other devices connect without a problem.

lspci does not show the adapter but lsusb does.
```
Bus 001 Device 005: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]

```

A clean install would really not be fun.

---

### Post by Warren Hill on 2014-07-09
There is a troubleshooting procedure here:

[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

Follow it, create a question on Launchpad and one of us on that site will be happy to help.

---

