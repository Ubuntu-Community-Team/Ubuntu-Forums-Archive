---
title: "help: vpnc requires network-admin magic to get vpn to work"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by d0nv on 2007-10-03
[COLOR=Black]I've managed to get vpnc working to connect to my company's Cisco VPN. However, I've only been able to make it work by using a set of steps I've stumbled on by trial and error.  They are 100% repeatable and once followed I can access the company network, but there's got to be a better way.](*,)  Googling for solutions has not found anything so far that works... hoping someone here might have the solution.

Here's my magic sequence:
[/COLOR][LIST=1]
[*][COLOR=Black]Boot my Dapper machine[/COLOR]
[*][COLOR=Black]open terminal, start vpnc[/COLOR]
[*][COLOR=Black]enter password from token card, get the response that I'm connected, but with a message "RTNETLINK answers: File exists"[/COLOR]
[*][COLOR=Black]can't access/ping any hosts, either within the company network or on the internet[/COLOR]
[*][COLOR=Black]stop vpnc[/COLOR]
[*][COLOR=Black]start GNOME networking app (network-admin is what shows under a ps -ef)[/COLOR]
[*][COLOR=Black]deactivate and reactivate the primary ethernet interface[/COLOR]
[*][COLOR=Black]restart vpnc[/COLOR]
[*][COLOR=Black]enter password from token card, get the response that I'm connected, but with NO additional message about "RTNETLINK answers: File exists"[/COLOR]
[*][COLOR=Black]can ping anything I wish, access company intranet and internet sites fine with browser or ssh session, etc. - life is good.
[/COLOR]
[*][COLOR=Black]can go on and off vpnc connection all day just fine (sudo vpnc, sudo vpnc-disconnect) , so long as I don't reboot
[/COLOR][/LIST][COLOR=Black]If I don't do the network-admin trick after the initial start and stop of vpnc, my machine will not access either the company network or my direct internet connection unless I reboot.

BTW, I also checked to see if vpnc is doing the right thing with resolv.conf and all appears OK there.  On vpnc, it adds the company domain to the search list and lists the company nameservers, etc. and on vpnc-disconnect I'm back to my default comcast connection info only.  It is the same content before and after I do the network-admin trick.

Actual terminal sequence captured below - I'm masking out what could be sensitive items with '*' characters.

Hope this is something really simple, just not so obvious to me.

Thanks,
Don[/COLOR]

```

donv@AMD64-Ubuntu:~$ sudo vpnc
Password:
Enter password for ****@vpn@ivpn-***.com:
Connect Banner:
| WARNING: This is a restricted access server. If you do not have explicit permission to be accessing this system, please leave immediately. Unauthorized access to this system is illegal. Attempts to access this server by any person not authorized will be reported to the appropriate
| law enforcement agencies including the FBI.
|
| PLEASE READ: This VPN Gateway is now DIA enabled.
| You may set your browser for a Direct Internet connection.
| See http://surl/dia for browser instructions.

RTNETLINK answers: File exists
VPNC started in background (pid: 5278)...
donv@AMD64-Ubuntu:~$ ping mit.edu
ping: unknown host mit.edu
donv@AMD64-Ubuntu:~$ sudo vpnc-disconnect
Terminating vpnc daemon (pid: 5278)
donv@AMD64-Ubuntu:~$ ping mit.edu
connect: Network is unreachable
donv@AMD64-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:49:63:36:2D
          inet addr:192.168.15.103  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fe63:362d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9092 (8.8 KiB)  TX bytes:12379 (12.0 KiB)
          Interrupt:177 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:14:85:C8:34:2A
          inet addr:192.168.15.104  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fec8:342a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9342 (9.1 KiB)  TX bytes:810 (810.0 b)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1240 (1.2 KiB)  TX bytes:1240 (1.2 KiB)

************************************************************************
At this point, I open System > Administration > Networking and
deactivate then reactivate eth0.
************************************************************************
donv@AMD64-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:49:63:36:2D
          inet addr:192.168.15.103  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fe63:362d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10147 (9.9 KiB)  TX bytes:12781 (12.4 KiB)
          Interrupt:177 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:14:85:C8:34:2A
          inet addr:192.168.15.104  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fec8:342a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10833 (10.5 KiB)  TX bytes:1802 (1.7 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1240 (1.2 KiB)  TX bytes:1240 (1.2 KiB)

donv@AMD64-Ubuntu:~$ ping mit.edu
PING mit.edu (18.7.22.69) 56(84) bytes of data.
64 bytes from mit.edu (18.7.22.69): icmp_seq=1 ttl=245 time=13.7 ms
64 bytes from mit.edu (18.7.22.69): icmp_seq=2 ttl=245 time=7.70 ms

--- mit.edu ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 7.709/10.743/13.777/3.034 ms
donv@AMD64-Ubuntu:~$ sudo vpnc
Enter password for ***@vpn@ivpn-***.com:
Connect Banner:
| WARNING: This is a restricted access server. If you do not have explicit permission to be accessing this system, please leave immediately. Unauthorized access to this system is illegal. Attempts to access this server by any person not authorized will be reported to the appropriate
| law enforcement agencies including the FBI.
|
| PLEASE READ: This VPN Gateway is now DIA enabled.
| You may set your browser for a Direct Internet connection.
| See http://surl/dia for browser instructions.

VPNC started in background (pid: 5817)...
donv@AMD64-Ubuntu:~$ ping mit.edu
PING mit.edu (18.7.22.69) 56(84) bytes of data.
64 bytes from WEB.MIT.EDU (18.7.22.69): icmp_seq=1 ttl=242 time=89.7 ms
64 bytes from WEB.MIT.EDU (18.7.22.69): icmp_seq=2 ttl=242 time=91.8 ms

--- mit.edu ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 89.780/90.833/91.887/1.095 ms
donv@AMD64-Ubuntu:~$

```

---

### Post by Cryptog on 2007-10-04
Try looking at the routing table before and after the "hack":    sudo netstat -rn

---

