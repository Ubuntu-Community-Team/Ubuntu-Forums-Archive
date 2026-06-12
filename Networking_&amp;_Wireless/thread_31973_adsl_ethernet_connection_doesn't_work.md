---
title: "adsl ethernet connection doesn't work"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by mila80 on 2005-05-05
Hi all,
   I have a problem with my adsl ethernet connection.
I set all with pppoeconf and start the connection con pon dsl-provider, but, if I'm lucky, I can surf only for some seconds. 

[COLOR=Red]marco@ubuntu:~$ sudo pon dsl-provider[/COLOR]
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
[COLOR=Red]marco@ubuntu:~$ plog[/COLOR]
May  5 20:58:01 localhost pppd[8330]: Couldn't increase MRU to 1500
May  5 20:58:01 localhost pppd[8330]: Couldn't increase MRU to 1500
May  5 20:58:01 localhost pppd[8330]: Remote message: Request Denied
May  5 20:58:01 localhost pppd[8330]: PAP authentication failed
May  5 20:58:01 localhost pppd[8330]: Couldn't increase MTU to 1500
May  5 20:58:01 localhost pppd[8330]: Couldn't increase MRU to 1500
May  5 20:58:01 localhost pppd[8330]: Connection terminated.

[COLOR=Red]marco@ubuntu:~$ ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:04:76:24:82:A7
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe24:82a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:333351 (325.5 KiB)  TX bytes:66597 (65.0 KiB)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:257008 (250.9 KiB)  TX bytes:257008 (250.9 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:82.50.90.197  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:295314 (288.3 KiB)  TX bytes:35218 (34.3 KiB)

 ](*,)  ](*,)  ](*,) 

With my windows all works well. I tell this only to exclude an hardware problem.

Someone can help me???

many thanks,

MARCO

---

### Post by alastair on 2005-05-05
May 5 20:58:01 localhost pppd[8330]: Remote message: Request Denied
May 5 20:58:01 localhost pppd[8330]: PAP authentication failed

There are probably more messages than these (above) - see /var/log/syslog

Whatever - you are not talking to the ISP correctly and authentication is failing. Either try setting up your connection again (ppp config program) - or check the config files like :

/etc/ppp/peers/dsl-provider
/etc/chatscripts/dsl-provider

Maybe. I am guessing these files.

---

### Post by momo66 on 2005-05-05
Get a wireless router and setup PPPOE on it.  If you dont have another computer you now have a reason to get one. :smile:

---

### Post by mila80 on 2005-05-05
[QUOTE=alastair]May 5 20:58:01 localhost pppd[8330]: Remote message: Request Denied
May 5 20:58:01 localhost pppd[8330]: PAP authentication failed

There are probably more messages than these (above) - see /var/log/syslog

Whatever - you are not talking to the ISP correctly and authentication is failing. Either try setting up your connection again (ppp config program) - or check the config files like :

/etc/ppp/peers/dsl-provider
/etc/chatscripts/dsl-provider

Maybe. I am guessing these files.[/QUOTE]

Dear alastair thanks for your help.
I tryed to look out 
/etc/ppp/peers/dsl-provider
/etc/chatscripts/dsl-provider
and in my opinion all is ok. However I redo pppoeconf, but without positive results.
The situation is the same.
 :confused: 
What can I do now???
Marco

---

### Post by Rhawi Dantas on 2005-05-05
I have the same problem...
After a while the system disconnects and I just stay connected to GAIM...

Look in my post:

[http://ubuntuforums.org/showthread.php?t=31920](http://ubuntuforums.org/showthread.php?t=31920)

I just don't know how to deal with it...

---

### Post by alastair on 2005-05-05
There is really not enough information to go. However, both PPP and "chat" (for login) have a debug or verbose mode - you could try setting that and looking at the logs. Assuming the files above are the right ones!

Make sure that "chat" is called with "-v" (verbose) in :

/etc/ppp/peers/dsl-provider

and also add a "debug" option (on a separate (new) line) to this file.

/etc/ppp/peers/dsl-provider

+

debug

line. Then dial-out and look at the logs. More logs!

---

### Post by mila80 on 2005-05-06
All done, but now I can only use gaim, I can't download mail and surf...
Here are the log...

Sorry, but I can't understand what is happening.


root@ubuntu:/home/marco # plog
May  6 10:59:15 localhost pppd[8997]: sent [IPCP ConfReq id=0x2 <addr 82.54.132.165> <ms-dns1 85.37.17.15> <ms-dns3 151.99.125.1>]
May  6 10:59:15 localhost pppd[8997]: rcvd [IPCP ConfAck id=0x2 <addr 82.54.132.165> <ms-dns1 85.37.17.15> <ms-dns3 151.99.125.1>]
May  6 10:59:15 localhost pppd[8997]: Cannot determine ethernet address for proxy ARP
May  6 10:59:15 localhost pppd[8997]: local  IP address 82.54.132.165
May  6 10:59:15 localhost pppd[8997]: remote IP address 192.168.100.1
May  6 10:59:15 localhost pppd[8997]: primary   DNS address 85.37.17.15
May  6 10:59:15 localhost pppd[8997]: secondary DNS address 151.99.125.1
May  6 10:59:15 localhost pppd[8997]: Script /etc/ppp/ip-up started (pid 9008)
May  6 10:59:15 localhost pppd[8997]: Script /etc/ppp/ip-up finished (pid 9008), status = 0x0



root@ubuntu:/home/marco # plog
May  6 11:02:50 localhost pppd[9199]: rcvd [PAP AuthNak id=0x1 "Request Denied"]
May  6 11:02:50 localhost pppd[9199]: Remote message: Request Denied
May  6 11:02:50 localhost pppd[9199]: PAP authentication failed
May  6 11:02:50 localhost pppd[9199]: Couldn't increase MTU to 1500
May  6 11:02:50 localhost pppd[9199]: Couldn't increase MRU to 1500
May  6 11:02:50 localhost pppd[9199]: sent [LCP TermReq id=0x2 "Failed to authenticate ourselves to peer"]
May  6 11:02:50 localhost pppd[9199]: rcvd [LCP TermReq id=0x2]
May  6 11:02:50 localhost pppd[9199]: sent [LCP TermAck id=0x2]
May  6 11:02:50 localhost pppd[9199]: rcvd [LCP TermAck id=0x2]
May  6 11:02:50 localhost pppd[9199]: Connection terminated.



and here the syslog

May  6 11:45:16 localhost pppd[8212]: Plugin rp-pppoe.so loaded.
May  6 11:45:16 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
May  6 11:45:16 localhost kernel: PPP generic driver version 2.4.2
May  6 11:45:17 localhost pppd[8212]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
May  6 11:45:17 localhost pppd[8256]: pppd 2.4.2 started by root, uid 0
May  6 11:45:17 localhost udev[8258]: creating device node '/dev/ppp'
May  6 11:45:17 localhost pppd[8256]: PADS: Service-Name: ''
May  6 11:45:17 localhost pppd[8256]: PPP session is 51491
May  6 11:45:17 localhost kernel: NET: Registered protocol family 24
May  6 11:45:17 localhost pppd[8256]: using channel 1
May  6 11:45:17 localhost pppd[8256]: Using interface ppp0
May  6 11:45:17 localhost pppd[8256]: Connect: ppp0 <--> eth0
May  6 11:45:17 localhost pppd[8256]: Couldn't increase MTU to 1500
May  6 11:45:17 localhost pppd[8256]: Couldn't increase MRU to 1500
May  6 11:45:17 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:17 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:20 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:20 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:23 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:23 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:26 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:26 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:29 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:29 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:32 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
May  6 11:45:32 localhost dhclient: DHCPACK from 192.168.1.1
May  6 11:45:32 localhost dhclient: bound to 192.168.1.2 -- renewal in 28 seconds.
May  6 11:45:32 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:32 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:35 localhost pppd[8256]: sent [LCP ConfReq id=0x1 <magic 0xd3b57cd>]
May  6 11:45:35 localhost pppd[8256]: rcvd [LCP ConfAck id=0x1 <magic 0xd3b57cd>]
May  6 11:45:37 localhost pppd[8256]: rcvd [LCP ConfReq id=0x2 <mru 1492> <auth pap> <magic 0x5c3c5ae5>]
May  6 11:45:37 localhost pppd[8256]: sent [LCP ConfAck id=0x2 <mru 1492> <auth pap> <magic 0x5c3c5ae5>]
May  6 11:45:37 localhost pppd[8256]: Couldn't increase MRU to 1500
May  6 11:45:37 localhost pppd[8256]: sent [LCP EchoReq id=0x0 magic=0xd3b57cd]
May  6 11:45:37 localhost pppd[8256]: sent [PAP AuthReq id=0x1 user="marco.milanesi" password=<hidden>]
May  6 11:45:37 localhost pppd[8256]: rcvd [LCP EchoRep id=0x0 magic=0x5c3c5ae5]
May  6 11:45:37 localhost pppd[8256]: rcvd [PAP AuthAck id=0x1 ""]
May  6 11:45:37 localhost pppd[8256]: PAP authentication succeeded
May  6 11:45:37 localhost pppd[8256]: peer from calling number 00:09:B6:8D:B0:62 authorized
May  6 11:45:37 localhost pppd[8256]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
May  6 11:45:37 localhost pppd[8256]: rcvd [IPCP ConfReq id=0x1 <addr 192.168.100.1>]
May  6 11:45:37 localhost pppd[8256]: sent [IPCP ConfAck id=0x1 <addr 192.168.100.1>]
May  6 11:45:37 localhost pppd[8256]: rcvd [IPCP ConfNak id=0x1 <addr 82.50.160.224> <ms-dns1 85.37.17.15> <ms-dns3 151.99.125.1>]
May  6 11:45:37 localhost pppd[8256]: sent [IPCP ConfReq id=0x2 <addr 82.50.160.224> <ms-dns1 85.37.17.15> <ms-dns3 151.99.125.1>]
May  6 11:45:37 localhost pppd[8256]: rcvd [IPCP ConfAck id=0x2 <addr 82.50.160.224> <ms-dns1 85.37.17.15> <ms-dns3 151.99.125.1>]
May  6 11:45:37 localhost pppd[8256]: replacing old default route to eth0 [192.168.1.1]
May  6 11:45:37 localhost pppd[8256]: Cannot determine ethernet address for proxy ARP
May  6 11:45:37 localhost pppd[8256]: local  IP address 82.50.160.224
May  6 11:45:37 localhost pppd[8256]: remote IP address 192.168.100.1
May  6 11:45:37 localhost pppd[8256]: primary   DNS address 85.37.17.15
May  6 11:45:37 localhost pppd[8256]: secondary DNS address 151.99.125.1
May  6 11:45:37 localhost pppd[8256]: Script /etc/ppp/ip-up started (pid 8349)
May  6 11:45:38 localhost kernel: ip_tables: (C) 2000-2002 Netfilter core team
May  6 11:45:40 localhost postfix/master[6834]: reload configuration
May  6 11:45:40 localhost pppd[8256]: Script /etc/ppp/ip-up finished (pid 8349), status = 0x0
May  6 11:46:00 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
May  6 11:46:00 localhost dhclient: DHCPACK from 192.168.1.1
May  6 11:46:00 localhost dhclient: bound to 192.168.1.2 -- renewal in 30 seconds.
May  6 11:46:30 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
May  6 11:46:30 localhost dhclient: DHCPACK from 192.168.1.1
May  6 11:46:30 localhost dhclient: bound to 192.168.1.2 -- renewal in 27 seconds.
May  6 11:46:57 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
May  6 11:46:57 localhost dhclient: DHCPACK from 192.168.1.1
May  6 11:46:57 localhost dhclient: bound to 192.168.1.2 -- renewal in 29 seconds.
May  6 11:47:26 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
May  6 11:47:26 localhost dhclient: DHCPACK from 192.168.1.1
May  6 11:47:26 localhost dhclient: bound to 192.168.1.2 -- renewal in 30 seconds.
May  6 11:47:56 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
May  6 11:47:56 localhost dhclient: DHCPACK from 192.168.1.1
May  6 11:47:56 localhost dhclient: bound to 192.168.1.2 -- renewal in 29 seconds

Thanks, 

Marco

---

### Post by mila80 on 2005-05-06
[QUOTE=Rhawi Dantas]I have the same problem...
After a while the system disconnects and I just stay connected to GAIM...

Look in my post:

[http://ubuntuforums.org/showthread.php?t=31920](http://ubuntuforums.org/showthread.php?t=31920)

I just don't know how to deal with it...[/QUOTE]
 ok, but what did you do to solve your problem???

---

### Post by Rhawi Dantas on 2005-05-06
That's the problem, I'm also asking for help  ;-) 

I already add the debug line in the /etc/ppp/peers/dsl-provider but didn't show anything anormal... then, I installed the pppoe that comes with synaptic and the dsl-provider and options were with total different configurantions and I thought that this would work... WRONG

I don't know why this is still happens but I was a SuSE user and I didn't have this problem with it...

---

### Post by mila80 on 2005-05-06
I have this problem since I upgrade from 4.10 to 5.04 but I think the two things are not correleted....

Someone can help us???

---

### Post by Rhawi Dantas on 2005-05-06
With the installation of pppoe that comes with Synaptic I don't get that old messages with PADO packets and Couldn't increase MRU to 1500 BUT... the problem persists... 

/var/log/messages/
```

May  7 11:52:23 localhost pppd[6346]: pppd 2.4.2 started by root, uid 0
May  7 11:52:23 localhost pppd[6346]: Serial connection established.
May  7 11:52:23 localhost pppd[6346]: Using interface ppp0
May  7 11:52:23 localhost pppd[6346]: Connect: ppp0 <--> /dev/pts/0
May  7 11:52:24 localhost kernel: ACPI: Power Button (FF) [PWRF]
May  7 11:52:24 localhost kernel: ACPI: Sleep Button (CM) [SLPB]
May  7 11:52:24 localhost hal.hotplug[3501]: timout(10000 ms) waiting for /bus/pci/slots
May  7 11:52:24 localhost pci.agent[6594]: Bad PCI agent invocation
May  7 11:52:24 localhost kernel: drivers/usb/input/hid-input.c: event field not found
May  7 11:52:25 localhost kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
May  7 11:52:25 localhost kernel: apm: overridden by ACPI.
May  7 11:52:28 localhost pppd[6346]: PAP authentication succeeded
May  7 11:52:28 localhost kernel: PPP BSD Compression module registered
May  7 11:52:29 localhost kernel: PPP Deflate Compression module registered
May  7 11:52:29 localhost pppd[6346]: local  IP address 201.9.134.217
May  7 11:52:29 localhost pppd[6346]: remote IP address 200.164.195.25
May  7 11:52:29 localhost pppd[6346]: primary   DNS address 200.165.132.155
May  7 11:52:29 localhost pppd[6346]: secondary DNS address 200.149.55.142
May  7 11:52:47 localhost gconfd (rhawi-7575): starting (version 2.10.0), pid 7575 user 'rhawi'


```

This was my last syslog failure connection report
/var/log/syslog
```

May  7 01:13:00 localhost pppd[8941]: pppd 2.4.2 started by root, uid 0
May  7 01:13:00 localhost pppd[8941]: Serial connection established.
May  7 01:13:00 localhost pppd[8941]: Using interface ppp0
May  7 01:13:00 localhost pppd[8941]: Connect: ppp0 <--> /dev/pts/2
May  7 01:13:00 localhost pppoe[8942]: PADS: Service-Name: ''
May  7 01:13:00 localhost pppoe[8942]: PPP session is 51149
May  7 01:13:05 localhost pppd[8941]: PAP authentication succeeded
May  7 01:13:05 localhost pppd[8941]: Cannot determine ethernet address for proxy ARP
May  7 01:13:05 localhost pppd[8941]: local  IP address 201.9.133.193
May  7 01:13:05 localhost pppd[8941]: remote IP address 200.164.195.25
May  7 01:13:05 localhost pppd[8941]: primary   DNS address 200.165.132.155
May  7 01:13:05 localhost pppd[8941]: secondary DNS address 200.149.55.142
May  7 01:53:16 localhost pppd[8941]: Terminating on signal 15.
May  7 01:53:16 localhost pppd[8941]: Connect time 40.2 minutes.
May  7 01:53:16 localhost pppd[8941]: Sent 1876342 bytes, received 6697808 bytes.
May  7 01:53:16 localhost pppd[8941]: Connection terminated.
May  7 01:53:16 localhost pppoe[8942]: read (asyncReadFromPPP): Session 51149: Input/output error
May  7 01:53:16 localhost pppoe[8942]: Sent PADT

```

---

### Post by Rhawi Dantas on 2005-05-07
Please... I'm begging for help  ](*,)

---

### Post by xbaez on 2005-05-27
I had the excact same problems, run pppconfig, edited some files at /etc/ppp
and the only solution was to run kppp as a non-privileged user (root), that is in the 'dialout' group

So now I use root, and I am able to connect to the internet

Hopefully that will be your case too

However I wasn't able to connect to the internet, you surely have done that

---

### Post by mila80 on 2005-05-27
Hi all,
i find it with a my friends. It solves our problem...
Try with it... ok???


[http://ubuntuforums.org/showpost.ph...316&postcount=2](http://ubuntuforums.org/showpost.ph...316&postcount=2)

bye, Marco

---

### Post by tim@bigredtree.com on 2005-05-27
You probably already took care of this, but are there filters on all of the phone lines except for your dsl modem?

---

