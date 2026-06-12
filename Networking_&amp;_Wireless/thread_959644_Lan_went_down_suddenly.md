---
title: "Lan went down suddenly"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-10-26
Lan went down suddenly

I'm running ubuntu 8.04 as a gateway with a windows client pc.

Today at about 3:20 pm my lan suddenly went down.  I checked syslog to see what happened.  Eth1 faces lan, eth0 faces internet.

```

Oct 26 15:17:01 desktop /USR/SBIN/CRON[25233]: (root) CMD (   cd / && run-parts --report /etc/cro
n.hourly)
Oct 26 15:20:40 desktop kernel: [794086.440326] atl1 0000:01:00.0: eth0 link is down
Oct 26 15:21:33 desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 26 15:21:33 desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.fr
eedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

```

Is it just a coincidence that the hourly cron job ran 3 minutes before nm_dbus_get_networks_cb()?  I don't have any scripts in /etc/cron.hourly.  Also, what is nm_dbus_get_networks_cb().  I don't have any wireless cards in my gateway.

I decided to "sudo /etc/init.d/networking restart", results below.

```

Oct 26 15:24:08 desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid
 6253
Oct 26 15:24:08 desktop dhclient: killed old client process, removed PID file
Oct 26 15:24:08 desktop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct 26 15:24:08 desktop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Oct 26 15:24:08 desktop dhclient: All rights reserved.
Oct 26 15:24:08 desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct 26 15:24:08 desktop dhclient: 
Oct 26 15:24:08 desktop dhclient: Listening on LPF/eth0/00:1d:60:17:e4:02
Oct 26 15:24:08 desktop dhclient: Sending on   LPF/eth0/00:1d:60:17:e4:02
Oct 26 15:24:08 desktop dhclient: Sending on   Socket/fallback
Oct 26 15:24:08 desktop dhclient: DHCPRELEASE on eth0 to 99.246.62.1 port 67
Oct 26 15:24:08 desktop avahi-daemon[4853]: Withdrawing address record for [my ipaddress] on eth0.
Oct 26 15:24:08 desktop avahi-daemon[4853]: Leaving mDNS multicast group on interface eth0.IPv4 w
ith address [my ipaddress].
Oct 26 15:24:08 desktop avahi-daemon[4853]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 26 15:24:08 desktop avahi-daemon[4853]: Withdrawing address record for fe80::21d:60ff:fe17:e4
02 on eth0.
Oct 26 15:24:08 desktop avahi-daemon[4853]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 26 15:24:08 desktop avahi-daemon[4853]: Leaving mDNS multicast group on interface eth1.IPv4 w
ith address 192.168.0.1.
Oct 26 15:24:08 desktop dhcpd: receive_packet failed on eth1: Network is down
Oct 26 15:24:08 desktop avahi-daemon[4853]: Withdrawing address record for fe80::208:54ff:fedd:35
c4 on eth1.
Oct 26 15:24:08 desktop avahi-daemon[4853]: Withdrawing address record for 192.168.0.1 on eth1.
Oct 26 15:24:08 desktop kernel: [794294.135093] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 26 15:24:08 desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid
 0
Oct 26 15:24:08 desktop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct 26 15:24:08 desktop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Oct 26 15:24:08 desktop dhclient: All rights reserved.
Oct 26 15:24:08 desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct 26 15:24:08 desktop dhclient: 
Oct 26 15:24:09 desktop dhclient: Listening on LPF/eth0/00:1d:60:17:e4:02
Oct 26 15:24:09 desktop dhclient: Sending on   LPF/eth0/00:1d:60:17:e4:02
Oct 26 15:24:09 desktop dhclient: Sending on   Socket/fallback

```

I did an ifconfig, and it looks like both interfaces are up.

```

eth0      Link encap:Ethernet  HWaddr 00:1d:60:17:e4:02  
          inet addr:[my ipaddress]  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::21d:60ff:fe17:e402/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7990 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:18597945 (17.7 MB)  TX bytes:701004 (684.5 KB)

eth1      Link encap:Ethernet  HWaddr 00:08:54:dd:35:c4  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104359 (101.9 KB)  TX bytes:104359 (101.9 KB)

```

From ubuntu I can ping hostnames that are listening on eth1 and I get a response from bind.  I restarted dhcpd3 in debug mode and it looks like it's listening on eth1.  

I did some tests on both network cards in the gateway and on the windows machine and they seem to be working properly.

I'm sort of stumped on how to proceed with this, it was just so random.  Everything was working properly.

---

### Post by Shwick2 on 2008-10-26
I remember that I executed "hdparm -Tt /dev/sda" to test the network card speed, and I just found out that could cause "unexpected data corruption", [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html).  That might be a problem.

---

### Post by cariboo on 2008-10-26
The command you issued is to check hard drive transfer speeds, it has nothing to do with networking. Are you actually using both network interfaces, eth 0 and eth1? If not why not disable one in the bios and then check your networking again. Elimintate every thing you don't need and then start diagnosing.

To check internal network speed you need to use something like iperf on two computers, one to act as a server and the other as the client.

Jim

---

### Post by Shwick2 on 2008-10-27
I got it working.  I disabled avahi, and blew compressed air over my NIC.  Which one worked I dunno.  Also I temporarily switched the interfaces using udev, i.e. I made the lan point to internet and internet point to lan.  No idea how this happened still.

---

