---
title: "Broadcom BCM4401 instability"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by gp2x on 2007-01-09
Hi all

I have a Dell Inspiron 9400 run Ubuntu EE. 

Recently I noticed that whenever network load increase significantly, NetworkManager would kill eth0 stating 'terminating current connection 'eth0' because it's no longer valid'. Then after a few seconds it would bring it up again, dhcp would get an IP etc.... only to have it happen again a few seconds later,

Basically I think NetworkManager believes Im pulling the cable when Im not. Ive try different network hardware (cables, switches etc) so i think this is a driver issue?

From syslog:


Jan 10 10:57:48 beast NetworkManager: <information>^ISWITCH: **terminating current connection 'eth0' because it's no longer valid. **
Jan 10 10:57:48 beast NetworkManager: <information>^I**Deactivating device eth0**. 
Jan 10 10:57:48 beast dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 30567
Jan 10 10:57:48 beast dhclient: killed old client process, removed PID file
Jan 10 10:57:48 beast kernel: [17268520.984000] **b44: eth0: Link is down.**
Jan 10 10:57:48 beast dhclient: DHCPRELEASE on eth0 to 172.20.14.235 port 67
Jan 10 10:57:49 beast NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jan 10 10:57:49 beast NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jan 10 10:57:51 beast kernel: [17268523.984000] b44: eth0: **Link is up at 100 Mbps, full duplex.**
Jan 10 10:57:51 beast kernel: [17268523.984000] b44: eth0: Flow control is off for TX and off for RX.
Jan 10 10:57:51 beast kernel: [17268523.984000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 10 10:57:51 beast NetworkManager: <information>^I**Will activate wired connection 'eth0' because it now has a link. **
Jan 10 10:57:51 beast NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Jan 10 10:57:51 beast NetworkManager: <information>^I**Will activate connection 'eth0'. **
Jan 10 10:57:51 beast NetworkManager: <information>^IDevice eth0 activation scheduled... 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) started... 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jan 10 10:57:51 beast NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jan 10 10:57:52 beast NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Jan 10 10:57:52 beast dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Jan 10 10:57:52 beast NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 10 10:57:52 beast NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Jan 10 10:57:53 beast NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Jan 10 10:57:57 beast dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 10 10:57:57 beast dhclient: DHCPOFFER from 172.20.14.235
Jan 10 10:57:57 beast dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan 10 10:57:57 beast dhclient: DHCPACK from 172.20.14.235
Jan 10 10:57:57 beast NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Jan 10 10:57:57 beast NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 10 10:57:57 beast dhclient: bound to 172.20.8.119 -- renewal in 1219380 seconds.
Jan 10 10:57:57 beast NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jan 10 10:57:57 beast dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jan 10 10:57:57 beast dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan 10 10:57:57 beast dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan 10 10:57:57 beast NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Jan 10 10:57:57 beast NetworkManager: <information>^I  address 172.20.8.119 
Jan 10 10:57:57 beast NetworkManager: <information>^I  netmask 255.255.248.0 
Jan 10 10:57:57 beast NetworkManager: <information>^I  broadcast 172.20.15.255 
Jan 10 10:57:57 beast NetworkManager: <information>^I  gateway 172.20.15.240 
Jan 10 10:57:57 beast NetworkManager: <information>^I  nameserver 172.20.14.235 
Jan 10 10:57:57 beast NetworkManager: <information>^I  nameserver 172.26.2.235 
Jan 10 10:57:57 beast NetworkManager: <information>^I  domain name 'xxxxxxx.internal' 
Jan 10 10:57:57 beast NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 10 10:57:57 beast NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jan 10 10:57:57 beast NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jan 10 10:57:58 beast NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification! 
Jan 10 10:57:58 beast NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Jan 10 10:57:58 beast NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Jan 10 10:57:58 beast NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 


So the b44 driver is saying the link is dead? 

Help!

---

### Post by gp2x on 2007-01-10
Just as a followup, I believe the problem doesnt occur when you dont hibernate/resume. I have a feeling its an interrupt related problem. Ive raised an issue with broadcom to see if they cant make the driver play with hibernate.

I *think* the issue is gone - Ill test further tho.

EDIT: nope! still there. anyone have any clues?

---

### Post by SebbeJohan on 2007-01-13
Hi

I'm a newbie but I think I have the same problem and it's  been now 2 months I'm trying to find a solution. From your log, I can see the same pattern. I reinstalled everything so many times and finally changed to kubuntu hoping it would change something. Still the same problem: internet disappers without any apparent reason. I saw on broadcom that there are drivers to install for the Broadcom 4401, but I'm not sure how to do it and if that's the real problem.

Any idea?

---

