---
title: "Network connection frequently cuts out, needs manual restart"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by TheOneBlackMage on 2008-10-06
Hello,

I'm running Xubuntu Hardy 8.04 (Kernel 2.6.24-19-generic).

The machine has been running fine on the current hardware with no real changes for years.  Recently I've been using this machine for a lot of downloads, and a central point for copying files around.  I've got a number of USB hard drives mounted locally, as well as a SAMBA share for my RAID array on another computer.

I've found when I'm running a lot of downloads, or file transfers, sometimes the networking will just stop working.  I can ping locally, but not to the gateway, or out to the internet.  To fix it I have to restart the networking:

```
sudo /etc/init.d/networking restart
```

Any torrents have to be restarted as they've gone to [CLOSED] in rtorrent, but hellanzb seems to recover on its own, once it can resolve the host address again.

dmesg just shows this for the eth0 restart:

[388006.122108] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[388016.901461] eth0: no IPv6 routers present


I checked in /var/log/messages, and I can't see any errors for the networking, just a lot for the hard drives and RAID connections.  No problems with the USB drives, I assume the RAID connections are for when the networking goes down.

I was hoping to get some ideas on how to increase logging for the network connection to troubleshoot, or get some ideas on how to fix this problem.  I do a lot of work on this machine remotely, so when it cuts out like this, it's a real pain.

---

### Post by cariboo on 2008-10-06
It might be quicker and easier to replace the network card to see if this repairs the problem. I have a builtin nic on the motherboard of my server, that was doing the same thing. Replacing the nic repaired the problem.

Jim

---

