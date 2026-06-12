---
title: "dsl does not start on boot with Shorewall"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by froebi on 2008-08-27
Hi,

my box connects to the network via dsl modem. The connection is established when booting. I also have the Shorewall firewall configured. Everything worked just fine -- until recently.

I somehow (not to be explained in further detail) mixed up the init script-links for networking and shorewall in /etc/rc?.d. To recover from that mess I removed all networking- and shorewall-links from /etc/rc?.d and did a dpkg-reconfigure for netbase and shorewall-common. The links where there again and both networking and shorewall were started upon boot again. But now my dsl connection will not be established anymore. I'm not even sure if networking is starting properly; but in the boot output it says something like "Configuring network interfaces -- OK".

* Issuing '/etc/init.d/networking restart' after boot, establishes the dsl connection without problems.
* When I disable shorewall in /etc/default/shorewall, the dsl connetion can be succesfully established upon boot.

That's strage -- especially considering that it worked before.

Any ideas what this could be all about?

PS: My network interface for the dsl connection is ppp0. And in /etc/default/shorewall I configured shorewall to wait for ppp0 to be ready.

I'd be happy for any hints.

regards,
  Christian

---

### Post by john.nicholls on 2008-08-27
> **froebi said:**
> Hi,

my box connects to the network via dsl modem. The connection is established when booting. I also have the Shorewall firewall configured. Everything worked just fine -- until recently.

I somehow (not to be explained in further detail) mixed up the init script-links for networking and shorewall in /etc/rc?.d. To recover from that mess I removed all networking- and shorewall-links from /etc/rc?.d and did a dpkg-reconfigure for netbase and shorewall-common. The links where there again and both networking and shorewall were started upon boot again. But now my dsl connection will not be established anymore. I'm not even sure if networking is starting properly; but in the boot output it says something like "Configuring network interfaces -- OK".

* Issuing '/etc/init.d/networking restart' after boot, establishes the dsl connection without problems.
* When I disable shorewall in /etc/default/shorewall, the dsl connetion can be succesfully established upon boot.

That's strage -- especially considering that it worked before.

Any ideas what this could be all about?

PS: My network interface for the dsl connection is ppp0. And in /etc/default/shorewall I configured shorewall to wait for ppp0 to be ready.

I'd be happy for any hints.

regards,
  Christian

My setup is similar, but I didn't need to configure shorewall to wait. So I'm more inclined to suspect the networking part. I don't use ppp0; the network config file uses eth0 and eth1.

You may get some clues from the outputs of ifconfig -a and route -n.

---

### Post by froebi on 2008-08-28
Hi John,

after booting with shorewall enabled:
```

# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:92:03:71:76
          inet6 addr: fe80::21a:92ff:fe03:7176/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:8591 (8.3 KB)  TX bytes:8824 (8.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:78.48.1.101  P-t-P:213.191.64.30  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:4977 (4.8 KB)  TX bytes:4670 (4.5 KB)

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.191.64.30   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

So it seems that the dsl connections was established. I just had a look at the contents of /etc/resolv.conf. It still contains the defaults:
```

search localdomain
nameserver 192.168.1.1

```

After /etc/init.d/networking restart, /etc/resolv.conf contains the two dns servers I receive from my dsl provider.

Hope this observation means something to you.

Thanks,
  Christian

---

### Post by john.nicholls on 2008-08-28
It doesn't mean much to me I'm afraid; the only thing I can comment on is that the route entry on my computer reads
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.50.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    100    0        0 eth1

but when the connection is not working there are only two lines; I forget which interface drops out.
John

---

### Post by froebi on 2008-08-28
Hi John,

I suspect that the only problem is the resolv.conf. Everything else -- including the routing -- is fine. I can ping out into the net when using an ip-address instead of a host name.

Something in the boot process after networking seems to override the resolv.conf with default values.

I had a similar behaviour when I recently installed network-manager (which I suspect was the root cause of my problems). But I uninstalled this beast now. And again, things are working properly now when I disable shorewall (which wasn't the case when network-manager was still installed).

Christian

---

### Post by john.nicholls on 2008-08-28
Christian

Some further thoughts: run the commands I suggested  (ifconfig -a and route -n) when thw internet conection is working and when it isn't and compare the results. I would imagine the first would be the same and the second different. Also while you're switching Shorewall and networking on and off, have a terminal open at /var/log running the command > tail -f syslog which will show a running list of what is going on. I may not be able to make sense of the results, but I'm sure somebody can.

John

---

### Post by froebi on 2008-08-29
Hi John,

I'm currently @work now. I'll do as you suggested this evening and post the results here...

Meanwhile, I did some workaround: I simply entered the nameservers into the default resolv.conf. As they are always the same with my dsl-provider, things are working now. This, of course, is not a satisfying solution.

I also have the feeling that shorewall is not the real cause of the problem. Maybe it's only masking the problem, making it harder to find. But that's just a guess. -- Hope we can clear things up after I posted the output of the commands you suggested.

Thanks,
  Christian

---

### Post by froebi on 2008-08-29
Ok, next try. I took a copy of syslog when booting in the following two scenarios:
1. shorewall disabled
2. shorewall enabled

After booting, both scenarios yield the equivalent results when doing ifconfig -a and route -n. The only difference (as far as I can tell) is /etc/resolv.conf. In 1. scenario I have the version pppd installs after retrieving the dns servers form my provider. In the 2. scenario I have the default resolv.conf leaving me without working dns.

Here are the syslogs now. The strange thing about it is that in scenario 2 I can see no sign of pppd connecting at all.

scenario 1:
```

Aug 30 00:47:51 froebi kernel: [   44.877168] PPP generic driver version 2.4.2
Aug 30 00:47:51 froebi kernel: [   44.896824] NET: Registered protocol family 17
Aug 30 00:47:51 froebi kernel: [   44.932162] NET: Registered protocol family 10
Aug 30 00:47:51 froebi kernel: [   44.932382] lo: Disabled Privacy Extensions
Aug 30 00:47:51 froebi kernel: [   45.228776] NET: Registered protocol family 24
Aug 30 00:47:51 froebi kernel: [   45.938220] No dock devices found.
Aug 30 00:47:51 froebi kernel: [   46.278440] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
Aug 30 00:47:51 froebi kernel: [   46.278182] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xc
Aug 30 00:47:51 froebi kernel: [   46.278187] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xd
Aug 30 00:47:51 froebi kernel: [   46.278189] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
Aug 30 00:47:51 froebi avahi-daemon[5270]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Aug 30 00:47:51 froebi avahi-daemon[5270]: Successfully dropped root privileges.
Aug 30 00:47:51 froebi avahi-daemon[5270]: avahi-daemon 0.6.22 starting up.
Aug 30 00:47:51 froebi avahi-daemon[5270]: Successfully called chroot().
Aug 30 00:47:51 froebi avahi-daemon[5270]: Successfully dropped remaining capabilities.
Aug 30 00:47:51 froebi avahi-daemon[5270]: No service file found in /etc/avahi/services.
Aug 30 00:47:51 froebi avahi-daemon[5270]: Network interface enumeration completed.
Aug 30 00:47:51 froebi avahi-daemon[5270]: Registering new address record for fe80::21a:92ff:fe03:7176 on eth0.*.
Aug 30 00:47:51 froebi avahi-daemon[5270]: Server startup complete. Host name is froebi.local. Local service cookie is 178183040.
Aug 30 00:47:51 froebi avahi-daemon[5270]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 30 00:47:52 froebi kernel: [   47.273266] ppdev: user-space parallel port driver
Aug 30 00:47:52 froebi kernel: [   47.410323] audit(1220050072.320:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5312 profile="/usr/sbin/cupsd" namespace="default"
Aug 30 00:47:52 froebi mysqld_safe[5388]: started
Aug 30 00:47:53 froebi mysqld[5391]: 080830  0:47:53  InnoDB: Started; log sequence number 0 500648312
Aug 30 00:47:53 froebi mysqld[5391]: 080830  0:47:53 [Note] /usr/sbin/mysqld: ready for connections.
Aug 30 00:47:53 froebi mysqld[5391]: Version: '5.0.51a-3ubuntu5.2'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Aug 30 00:47:53 froebi pppd[4650]: PAP authentication succeeded
Aug 30 00:47:53 froebi pppd[4650]: peer from calling number 00:30:88:03:86:66 authorized
Aug 30 00:47:53 froebi pppd[4650]: Cannot determine ethernet address for proxy ARP
Aug 30 00:47:53 froebi pppd[4650]: local  IP address 78.48.40.8
Aug 30 00:47:53 froebi pppd[4650]: remote IP address 213.191.64.31
Aug 30 00:47:53 froebi pppd[4650]: primary   DNS address 213.191.74.11
Aug 30 00:47:53 froebi pppd[4650]: secondary DNS address 213.191.92.82
Aug 30 00:47:53 froebi /etc/mysql/debian-start[5439]: Upgrading MySQL tables if necessary.
Aug 30 00:47:54 froebi kernel: [   49.194835] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 30 00:47:54 froebi kernel: [   49.194841] apm: disabled - APM is not SMP safe.
Aug 30 00:47:54 froebi /etc/mysql/debian-start[5445]: Looking for 'mysql' in: /usr/bin/mysql
Aug 30 00:47:54 froebi /etc/mysql/debian-start[5445]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Aug 30 00:47:54 froebi /etc/mysql/debian-start[5445]: This installation of MySQL is already upgraded to 5.0.51a, use --force if you still need to run mysql_upgrade
Aug 30 00:47:54 froebi /etc/mysql/debian-start[5479]: Checking for insecure root accounts.
Aug 30 00:47:54 froebi /etc/mysql/debian-start[5483]: WARNING: mysql.user contains 2 root accounts without password!
Aug 30 00:47:54 froebi /etc/mysql/debian-start[5485]: Checking for crashed MySQL tables.
Aug 30 00:47:54 froebi atieventsd[5497]: ATI External Events Daemon started... 
Aug 30 00:47:54 froebi atieventsd[5497]: Event daemon control socket created 
Aug 30 00:47:54 froebi atieventsd[5497]: acpid connection established 
Aug 30 00:47:59 froebi kernel: [   54.989451] eth0: no IPv6 routers present
Aug 30 00:48:01 froebi kernel: [   56.341691] pktcdvd: writer pktcdvd0 mapped to sr0
Aug 30 00:48:01 froebi dhcdbd: Started up.
Aug 30 00:48:03 froebi kernel: [   58.128012] Clocksource tsc unstable (delta = -236845768 ns)
Aug 30 00:48:05 froebi hcid[6138]: Bluetooth HCI daemon
Aug 30 00:48:05 froebi kernel: [   59.233147] Bluetooth: Core ver 2.11
Aug 30 00:48:05 froebi kernel: [   59.233233] NET: Registered protocol family 31
Aug 30 00:48:05 froebi kernel: [   59.233235] Bluetooth: HCI device and connection manager initialized
Aug 30 00:48:05 froebi kernel: [   59.233240] Bluetooth: HCI socket layer initialized
Aug 30 00:48:05 froebi hcid[6138]: Starting SDP server
Aug 30 00:48:05 froebi kernel: [   59.249523] Bluetooth: L2CAP ver 2.9
Aug 30 00:48:05 froebi kernel: [   59.249528] Bluetooth: L2CAP socket layer initialized
Aug 30 00:48:05 froebi hcid[6138]: Created local server at unix:abstract=/var/run/dbus-2ZEBjNcVJg,guid=8db7bac9e240ebaada1b18e748b87ca5
Aug 30 00:48:05 froebi audio[6156]: Bluetooth Audio daemon
Aug 30 00:48:05 froebi audio[6156]: Unix socket created: 5
Aug 30 00:48:05 froebi audio[6156]: audio.conf: Key file does not have key 'Enable'
Aug 30 00:48:05 froebi audio[6156]: audio.conf: Key file does not have key 'Disable'
Aug 30 00:48:05 froebi input[6157]: Bluetooth Input daemon
Aug 30 00:48:05 froebi input[6157]: Registered input manager path:/org/bluez/input
Aug 30 00:48:05 froebi kernel: [   59.285758] Bluetooth: RFCOMM socket layer initialized
Aug 30 00:48:05 froebi kernel: [   59.285776] Bluetooth: RFCOMM TTY layer initialized
Aug 30 00:48:05 froebi kernel: [   59.285778] Bluetooth: RFCOMM ver 1.8
Aug 30 00:48:05 froebi audio[6156]: add_service_record: got record id 0x10000
Aug 30 00:48:05 froebi audio[6156]: audio.conf: Key file does not have key 'Disable'
Aug 30 00:48:05 froebi audio[6156]: audio.conf: Key file does not have group 'A2DP'
Aug 30 00:48:05 froebi last message repeated 3 times
Aug 30 00:48:05 froebi audio[6156]: SEP 0x806d5b0 registered: type:0 codec:0 seid:1
Aug 30 00:48:05 froebi audio[6156]: add_service_record: got record id 0x10001
Aug 30 00:48:05 froebi audio[6156]: add_service_record: got record id 0x10002
Aug 30 00:48:05 froebi audio[6156]: add_service_record: got record id 0x10003
Aug 30 00:48:05 froebi audio[6156]: Registered manager path:/org/bluez/audio
Aug 30 00:48:05 froebi noip2[6175]: v2.1.4 daemon started 
Aug 30 00:48:05 froebi anacron[6192]: Anacron 2.3 started on 2008-08-30
Aug 30 00:48:05 froebi anacron[6192]: Normal exit (0 jobs run)
Aug 30 00:48:05 froebi /usr/sbin/cron[6219]: (CRON) INFO (pidfile fd = 3)
Aug 30 00:48:05 froebi /usr/sbin/cron[6220]: (CRON) STARTUP (fork ok)
Aug 30 00:48:05 froebi /usr/sbin/cron[6220]: (CRON) INFO (Running @reboot jobs)
Aug 30 00:48:08 froebi kdm[6337]: StartServerSucces

```

scenario 2:
```

Aug 30 00:57:53 froebi kernel: [   61.530114] PPP generic driver version 2.4.2
Aug 30 00:57:53 froebi kernel: [   61.549810] NET: Registered protocol family 17
Aug 30 00:57:53 froebi kernel: [   61.592629] NET: Registered protocol family 10
Aug 30 00:57:53 froebi kernel: [   61.592862] lo: Disabled Privacy Extensions
Aug 30 00:57:53 froebi kernel: [   61.839227] NET: Registered protocol family 24
Aug 30 00:57:53 froebi kernel: [   63.410195] Netfilter messages via NETLINK v0.30.
Aug 30 00:57:53 froebi kernel: [   63.442671] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Aug 30 00:57:53 froebi kernel: [   63.528070] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 30 00:57:53 froebi kernel: [   63.636313] ctnetlink v0.93: registering with nfnetlink.
Aug 30 00:57:53 froebi kernel: [   63.787110] ClusterIP Version 0.8 loaded successfully
Aug 30 00:57:53 froebi kernel: [   65.875933] No dock devices found.
Aug 30 00:57:53 froebi kernel: [   66.225743] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
Aug 30 00:57:53 froebi kernel: [   66.225306] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xc
Aug 30 00:57:53 froebi kernel: [   66.225311] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xd
Aug 30 00:57:53 froebi kernel: [   66.225314] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
Aug 30 00:57:54 froebi avahi-daemon[7358]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Aug 30 00:57:54 froebi avahi-daemon[7358]: Successfully dropped root privileges.
Aug 30 00:57:54 froebi avahi-daemon[7358]: avahi-daemon 0.6.22 starting up.
Aug 30 00:57:54 froebi avahi-daemon[7358]: Successfully called chroot().
Aug 30 00:57:54 froebi avahi-daemon[7358]: Successfully dropped remaining capabilities.
Aug 30 00:57:54 froebi avahi-daemon[7358]: No service file found in /etc/avahi/services.
Aug 30 00:57:54 froebi avahi-daemon[7358]: Network interface enumeration completed.
Aug 30 00:57:54 froebi avahi-daemon[7358]: Registering new address record for fe80::21a:92ff:fe03:7176 on eth0.*.
Aug 30 00:57:54 froebi avahi-daemon[7358]: Server startup complete. Host name is froebi.local. Local service cookie is 345480988.
Aug 30 00:57:54 froebi avahi-daemon[7358]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 30 00:57:54 froebi kernel: [   67.270624] ppdev: user-space parallel port driver
Aug 30 00:57:54 froebi kernel: [   67.407585] audit(1220050674.634:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=7400 profile="/usr/sbin/cupsd" namespace="default"
Aug 30 00:57:55 froebi mysqld_safe[7476]: started
Aug 30 00:57:55 froebi mysqld[7479]: 080830  0:57:55  InnoDB: Started; log sequence number 0 500648332
Aug 30 00:57:55 froebi mysqld[7479]: 080830  0:57:55 [Note] /usr/sbin/mysqld: ready for connections.
Aug 30 00:57:55 froebi mysqld[7479]: Version: '5.0.51a-3ubuntu5.2'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7518]: Upgrading MySQL tables if necessary.
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7523]: Looking for 'mysql' in: /usr/bin/mysql
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7523]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7523]: This installation of MySQL is already upgraded to 5.0.51a, use --force if you still need to run mysql_upgrade
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7546]: Checking for insecure root accounts.
Aug 30 00:57:56 froebi kernel: [   69.133699] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 30 00:57:56 froebi kernel: [   69.133705] apm: disabled - APM is not SMP safe.
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7553]: WARNING: mysql.user contains 2 root accounts without password!
Aug 30 00:57:56 froebi /etc/mysql/debian-start[7554]: Checking for crashed MySQL tables.
Aug 30 00:57:56 froebi atieventsd[7575]: ATI External Events Daemon started... 
Aug 30 00:57:56 froebi atieventsd[7575]: Event daemon control socket created 
Aug 30 00:57:56 froebi atieventsd[7575]: acpid connection established 
Aug 30 00:57:59 froebi kernel: [   72.202643] eth0: no IPv6 routers present
Aug 30 00:58:02 froebi kernel: [   75.515173] Shorewall:net2fw:DROP:IN=ppp0 OUT= MAC= SRC=85.179.131.70 DST=92.227.199.178 LEN=103 TOS=0x00 PREC=0x20 TTL=124 ID=13211 PROTO=UDP SPT=52525 DPT=22718 LEN=83 
Aug 30 00:58:28 froebi kernel: [  101.016994] pktcdvd: writer pktcdvd0 mapped to sr0
Aug 30 00:58:28 froebi dhcdbd: Started up.
Aug 30 00:58:30 froebi kernel: [  103.314993] Clocksource tsc unstable (delta = -88660204 ns)
Aug 30 00:58:32 froebi hcid[8214]: Bluetooth HCI daemon
Aug 30 00:58:32 froebi kernel: [  104.251556] Bluetooth: Core ver 2.11
Aug 30 00:58:32 froebi kernel: [  104.251641] NET: Registered protocol family 31
Aug 30 00:58:32 froebi kernel: [  104.251643] Bluetooth: HCI device and connection manager initialized
Aug 30 00:58:32 froebi kernel: [  104.251648] Bluetooth: HCI socket layer initialized
Aug 30 00:58:32 froebi hcid[8214]: Starting SDP server
Aug 30 00:58:32 froebi kernel: [  104.260472] Bluetooth: L2CAP ver 2.9
Aug 30 00:58:32 froebi kernel: [  104.260479] Bluetooth: L2CAP socket layer initialized
Aug 30 00:58:32 froebi hcid[8214]: Created local server at unix:abstract=/var/run/dbus-SDQuZIlFcs,guid=783f73180b519b943a63e09f48b87f18
Aug 30 00:58:32 froebi audio[8230]: Bluetooth Audio daemon
Aug 30 00:58:32 froebi input[8233]: Bluetooth Input daemon
Aug 30 00:58:32 froebi input[8233]: Registered input manager path:/org/bluez/input
Aug 30 00:58:32 froebi audio[8230]: Unix socket created: 5
Aug 30 00:58:32 froebi audio[8230]: audio.conf: Key file does not have key 'Enable'
Aug 30 00:58:32 froebi audio[8230]: audio.conf: Key file does not have key 'Disable'
Aug 30 00:58:32 froebi kernel: [  104.296679] Bluetooth: RFCOMM socket layer initialized
Aug 30 00:58:32 froebi kernel: [  104.296695] Bluetooth: RFCOMM TTY layer initialized
Aug 30 00:58:32 froebi kernel: [  104.296698] Bluetooth: RFCOMM ver 1.8
Aug 30 00:58:32 froebi audio[8230]: add_service_record: got record id 0x10000
Aug 30 00:58:32 froebi audio[8230]: audio.conf: Key file does not have key 'Disable'
Aug 30 00:58:32 froebi audio[8230]: audio.conf: Key file does not have group 'A2DP'
Aug 30 00:58:32 froebi last message repeated 3 times
Aug 30 00:58:32 froebi audio[8230]: SEP 0x806d5b0 registered: type:0 codec:0 seid:1
Aug 30 00:58:32 froebi audio[8230]: add_service_record: got record id 0x10001
Aug 30 00:58:32 froebi audio[8230]: add_service_record: got record id 0x10002
Aug 30 00:58:32 froebi audio[8230]: add_service_record: got record id 0x10003
Aug 30 00:58:32 froebi audio[8230]: Registered manager path:/org/bluez/audio
Aug 30 00:58:32 froebi noip2[8251]: v2.1.4 daemon started 
Aug 30 00:58:32 froebi anacron[8268]: Anacron 2.3 started on 2008-08-30
Aug 30 00:58:32 froebi anacron[8268]: Normal exit (0 jobs run)
Aug 30 00:58:32 froebi /usr/sbin/cron[8295]: (CRON) INFO (pidfile fd = 3)
Aug 30 00:58:32 froebi /usr/sbin/cron[8296]: (CRON) STARTUP (fork ok)
Aug 30 00:58:32 froebi /usr/sbin/cron[8296]: (CRON) INFO (Running @reboot jobs)
Aug 30 00:58:34 froebi kdm[8410]: StartServerSucces

```

Hope someone can see the cause of the trouble.

Anyway, thanks for the help,
  Christian

---

