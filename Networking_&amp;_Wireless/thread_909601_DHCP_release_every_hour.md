---
title: "DHCP release every hour"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by swimb on 2008-09-03
Hi,
eth0 gets released every hour or so even though my router is set for a 1 week lease. It is a wired connection. The other PC on the router doesnt do this. I can see it happen in the system log. What can I do to fix it? What do I need to post from my system log? Thanks

forgot to say it is Ubuntu 7.10

---

### Post by swimb on 2008-09-03
This is from the syslog part of system log:


```
Sep  3 15:00:30 Mothra kernel: [601744.586808] skge eth0: Link is down.
Sep  3 15:00:30 Mothra NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Sep  3 15:00:30 Mothra NetworkManager: <info>  Deactivating device eth0. 
Sep  3 15:00:30 Mothra dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 12960
Sep  3 15:00:30 Mothra dhclient: killed old client process, removed PID file
Sep  3 15:00:30 Mothra dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Sep  3 15:00:30 Mothra avahi-daemon[4912]: Withdrawing address record for 192.168.0.102 on eth0.
Sep  3 15:00:30 Mothra avahi-daemon[4912]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Sep  3 15:00:30 Mothra avahi-daemon[4912]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep  3 15:00:31 Mothra NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Sep  3 15:00:31 Mothra NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Sep  3 15:00:31 Mothra avahi-daemon[4912]: Withdrawing address record for xxxx::xxx:xxxx:xxxx:xxx on eth0.
Sep  3 15:00:49 Mothra kernel: [601763.313626] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
Sep  3 15:00:49 Mothra kernel: [601763.318049] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep  3 15:00:49 Mothra NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Will activate connection 'eth0'. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Device eth0 activation scheduled... 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) started... 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep  3 15:00:49 Mothra NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep  3 15:00:50 Mothra NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Sep  3 15:00:50 Mothra NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep  3 15:00:50 Mothra NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Sep  3 15:00:50 Mothra dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Sep  3 15:00:50 Mothra avahi-daemon[4912]: Registering new address record for xxxx::xxx:xxxx:xxxx:xxx on eth0.*.
Sep  3 15:00:51 Mothra NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Sep  3 15:00:55 Mothra dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep  3 15:00:58 Mothra dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep  3 15:00:59 Mothra kernel: [601773.372038] eth0: no IPv6 routers present
Sep  3 15:01:05 Mothra dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep  3 15:01:05 Mothra dhclient: DHCPOFFER from 192.168.0.1
Sep  3 15:01:05 Mothra dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep  3 15:01:05 Mothra dhclient: DHCPACK from 192.168.0.1
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: New relevant interface eth0.IPv4 for mDNS.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Sep  3 15:01:05 Mothra NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Sep  3 15:01:05 Mothra NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep  3 15:01:05 Mothra dhclient: bound to 192.168.0.102 -- renewal in 269911 seconds.
Sep  3 15:01:05 Mothra NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Sep  3 15:01:05 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  3 15:01:05 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Sep  3 15:01:05 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  3 15:01:05 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  3 15:01:05 Mothra NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Sep  3 15:01:05 Mothra NetworkManager: <info>    address 192.168.0.102 
Sep  3 15:01:05 Mothra NetworkManager: <info>    netmask 255.255.255.0 
Sep  3 15:01:05 Mothra NetworkManager: <info>    broadcast 192.168.0.255 
Sep  3 15:01:05 Mothra NetworkManager: <info>    gateway 192.168.0.1 
Sep  3 15:01:05 Mothra NetworkManager: <info>    nameserver 192.168.0.1 
Sep  3 15:01:05 Mothra NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep  3 15:01:05 Mothra NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Sep  3 15:01:05 Mothra NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Withdrawing address record for 192.168.0.102 on eth0.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Withdrawing address record for xxxx::xxx:xxxx:xxxx:xxx on eth0.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.102.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: New relevant interface eth0.IPv4 for mDNS.
Sep  3 15:01:05 Mothra avahi-daemon[4912]: Registering new address record for 192.168.0.102 on eth0.IPv4.
Sep  3 15:01:06 Mothra NetworkManager: <info>  Clearing nscd hosts cache. 
Sep  3 15:01:06 Mothra NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Sep  3 15:01:06 Mothra NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Sep  3 15:01:06 Mothra NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Sep  3 15:01:06 Mothra NetworkManager: <info>  Activation (eth0) successful, device activated. 
Sep  3 15:01:06 Mothra ntpdate[27046]: the NTP socket is in use, exiting
Sep  3 15:01:07 Mothra avahi-daemon[4912]: Registering new address record for xxxx::xxx:xxxx:xxxx:xxx on eth0.*.
Sep  3 15:01:16 Mothra kernel: [601790.708470] eth0: no IPv6 routers present
```


I changed what looks like my mac address to xxx

---

### Post by pytheas22 on 2008-09-03
I think (I could be wrong) that the duration of a dhcp lease is set by the server, not dhclient (the Unix program that fetches a dhcp lease for you), so I don't know if there's any way to change it on your end.  Are you sure that your router gives out week-long leases?  That seems like a long time...I usually get an hour or two.

Also, you shouldn't be losing your connection when the lease expires--it should just be renewed seamlessly.  Is that happening, or is this causing some other kind of problem?  Or are you just wondering why the lease duration is shorter than you expect?

---

### Post by swimb on 2008-09-03
The router allows leases of 1, 2 or 3 hours, 1, 2, or 3 days and 1 week. I use 1 week to try to avoid the disconnects. Its a problem because i lose my connection to the internet every time it happens, only lasts about 10-30 seconds though. Thanks for the help.

---

### Post by pytheas22 on 2008-09-03
hmmm, as I said, you shouldn't be losing your connection every time you need to renew the lease.  The problem could be caused by something strange that Network Manager is doing.  You may want to try [wicd]("http://wicd.sourceforge.net") instead.

---

### Post by NadmanET on 2008-09-03
The first entry in the log indicates that the link went down.  The rest of it is the DHCP release and renew process which would normally happen after a connection reset.  The key is to figure out why the link got bumped in the first place.

The first thing I would do it check for a physical problem.  It sounds like it could be a loose connection.  Try a different Cat 5 cable and see if that fixes it.

> 
I think (I could be wrong) that the duration of a dhcp lease is set by the server, not dhclient (the Unix program that fetches a dhcp lease for you)

pytheas is correct; the lease time is controlled by the DHCP server.  However, there is no 'normal' lease time.  The administrator should set the lease time based on the environment.  For instance on my home network I have the lease time set to the max that the server will support which is on the order of months or years.  That's good for me because I can still manage my addresses dynamically and my network doesn't change much.  However this same setup wouldn't work at a wireless hotspot.  If you only have 250 usable addresses in your network and the lease was set for a week, but you have around 100 people logging on through your hotspot every day, you are going to run out of addresses by the middle of the week.

---

### Post by swimb on 2008-09-03
Thanks Ill have a look at wicd. In the log it says 'dhclient: bound to 192.168.0.102 -- renewal in 269911 seconds', thats about 3 days, but it still releases about every 1.5 hours.

---

### Post by swimb on 2008-09-03
Thanks Nadman, Ill run a different cable and report back.

---

### Post by swimb on 2008-09-03
A different cable didnt help, after an hour it did the same thing.

---

### Post by swimb on 2008-09-03
Every time it happens I get this in the userlog:

```
Sep  3 16:30:11 Mothra dhcdbd:  dhclient 26923 down (9) but si_code == 0 and releasing==0 !
Sep  3 16:30:51 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  3 16:30:51 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Sep  3 16:30:51 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  3 16:30:51 Mothra dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
```

The first line only appears sometimes.

---

### Post by pytheas22 on 2008-09-04
I googled a little for the bits about "dhclient 26923 down (9) but si_code == 0 and releasing==0 !"  This [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103258") (a bit dated) suggests that it's Network Manager's fault, and that it was fixed a long time ago, but maybe there's been a regression, or it has to do with your particular ethernet driver not liking NM.  If that's the case, try using wicd instead.

Also, do you have the problem if after a fresh reboot, and before connecting to anything, you kill Network Manager (sudo kill $(ps -e | grep Network)) and then connect manually with:
```

sudo dhclient eth0
```

Again, this would help to determine whether the problem lies with Network Manager, or a broader issue with your networking configuration.

---

### Post by swimb on 2008-09-05
I disabled the nic on my motherboard (yukon gigabit) and installed a pci card and it seems to be working fine now. This problem started when I moved and switched from DSL to cable and used a different router. But its working now so I'll mark this one solved. Thanks for the help.

---

### Post by swimb on 2008-09-18
Hi, I marked this as unsolved as its happening again with the different card too, it was not as frequent at first but is now back to every hour or so.
It only happens on this pc, the other 2 on the router are fine.
Im thinking I edited some files trying to get nfs working but I cant remember which ones were edited or what I changed. Is there any configs that could cause this? Thanks for any help on this

edit - I killed and restarted NM as suggested in post 11 and waiting to see if it still happens.

edit - Its been 8 hours now with no disconnects, Ill let it run overnight and check the logs and tell you how it went.

---

### Post by pytheas22 on 2008-09-18
You checked the make sure that the onboard NIC is still disabled, right?

Let us know if it goes down again with Network Manager out of the picture.

---

### Post by swimb on 2008-09-19
Yarrrrr, it ran all night without disconnecting, so seems t' be network manager causing the problem.

---

### Post by pytheas22 on 2008-09-19
hmmm, well that's good I suppose (insofar as you are more certain of the culprit).  I guess you should either switch to wicd or do the connection manually.

I like Network Manager, but it seems sometimes to cause more problems than it's worth...

---

