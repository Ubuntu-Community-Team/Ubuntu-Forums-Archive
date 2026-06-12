---
title: "Can't get NTP working on network"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by chriso0258 on 2015-05-12
Hello,

I'm running ubuntu 14.04 server. I've installed ntp on the server. It's getting it's time via eth0. I've set up another nic (eth1) with a private IP. In the workshop, I've set up a windows xp machine for testing to see if it will pick up the time from the server. I've installed NetTime to do this since there doesn't seem to be a way to configure a windows xp/7 machine to get ntp from a private server. NetTime is configured with the private IP address of the ntp server.

I can't get the workstation to sync time with the server. Under status it says "Kiss of death". I can ping the server.

I'm open to any ideas as to how to get a windows xp/7 machine to sync with this server.

The interface file is set up like this (they are both connected to the same switch so I have no gateway):

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 172.26.1.51
netmask 255.255.255.0
broadcast 172.26.1.255

Thanks for your assistance.

---

### Post by TheFu on 2015-05-12
Please post your /etc/ntp.conf file from the server. Remove all comments please and use "code tags".

XP doesn't support NTP natively - I used d4-time program and it works.

Vista and later (Win7) do support NTP natively.  "Internet time" - just put the IP address for your ntp server in there.  Also, you may want to change the registry setting to decrease the time between sync from Windows. I found anything less than 15 minutes was too long for time to be maintained correctly on my Windows systems. I've had this issue for 20 yrs with Windows no keeping time correctly. Had access to MSFT engineers - they claimed that within 5 min was close enough. The fact that msec accuracy has been easily available for 30+ yrs didn't matter.

---

