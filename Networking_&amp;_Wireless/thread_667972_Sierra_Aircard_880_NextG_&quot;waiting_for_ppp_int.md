---
title: "Sierra Aircard 880 NextG &quot;waiting for ppp interface to come up&quot;"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by tim356 on 2008-01-14
After searching and finding a whole bunch of info on getting these sierra aircards to work on linux, I finally seem to have it working - to a degree.  I've installed the driver and using KPPP I've setup the aircard to connect (Telstra NextG) however when I hit the "Connect" button, the connection doesn't complete.

I get "Modem Ready" then "Initializing Modem" then "Dialing *99#" then "Logging on to network" then it sits there for 20 secs or so and I get a dialog saying:
```
Timeout expired while waiting for the PPP interface to come up.
```

and the log shows:
```
Jan 15 14:37:47 farkineee pppd[5589]: pppd 2.4.4 started by tim, uid 1000
Jan 15 14:37:47 farkineee pppd[5589]: using channel 14
Jan 15 14:37:47 farkineee pppd[5589]: Using interface ppp0
Jan 15 14:37:47 farkineee pppd[5589]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 15 14:37:47 farkineee pppd[5589]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x43abac3b> <pcomp> <accomp>]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [LCP ConfReq id=0x3c <asyncmap 0x0> <auth chap MD5> <magic 0x11b8c9f9> <pcomp> <accomp>]
Jan 15 14:37:47 farkineee pppd[5589]: sent [LCP ConfNak id=0x3c <auth pap>]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x43abac3b> <pcomp> <accomp>]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [LCP ConfReq id=0x3d <asyncmap 0x0> <auth pap> <magic 0x11b8c9f9> <pcomp> <accomp>]
Jan 15 14:37:47 farkineee pppd[5589]: sent [LCP ConfAck id=0x3d <asyncmap 0x0> <auth pap> <magic 0x11b8c9f9> <pcomp> <accomp>]
Jan 15 14:37:47 farkineee pppd[5589]: sent [LCP EchoReq id=0x0 magic=0x43abac3b]
Jan 15 14:37:47 farkineee pppd[5589]: sent [PAP AuthReq id=0x1 user="0400311656@bigpond.com.au" password=<hidden>]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [LCP DiscReq id=0x3e magic=0x11b8c9f9]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [LCP EchoRep id=0x0 magic=0x11b8c9f9 43 ab ac 3b]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [PAP AuthAck id=0x1 ""]
Jan 15 14:37:47 farkineee pppd[5589]: PAP authentication succeeded
Jan 15 14:37:47 farkineee pppd[5589]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jan 15 14:37:47 farkineee pppd[5589]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jan 15 14:37:47 farkineee pppd[5589]: rcvd [LCP ProtRej id=0x3f 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jan 15 14:37:47 farkineee pppd[5589]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jan 15 14:37:48 farkineee pppd[5589]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
Jan 15 14:37:48 farkineee pppd[5589]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
Jan 15 14:38:17 farkineee pppd[5589]: Terminating on signal 15
Jan 15 14:38:17 farkineee pppd[5589]: sent [LCP TermReq id=0x2 "User request"]
Jan 15 14:38:20 farkineee pppd[5589]: sent [LCP TermReq id=0x3 "User request"]
Jan 15 14:38:23 farkineee pppd[5589]: Connection terminated.
Jan 15 14:38:23 farkineee pppd[5589]: Modem hangup
Jan 15 14:38:23 farkineee pppd[5589]: Exit.
```
the terminal (where I ran kppp from) shows:
```
Opener: received OpenResolv
Opener: received PPPDExitStatus
Opener: received OpenSysLog
Opener: received SetSecret
Opener: received OpenDevice
Opener: received ExecPPPDaemon
In parent: pppd pid 5589
Couldn't find interface ppp0: No such device
Couldn't find interface ppp0: No such device
Kernel supports ppp alright.
Couldn't find interface ppp0: No such device
Opener: received KillPPPDaemon
In killpppd(): Sending SIGTERM to 5589
It was pppd that died
pppd exited with return value 16
Sending 5527 a SIGUSR1
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received PPPDExitStatus
Opener: received OpenSysLog

```

It seems to be when it is starting pppd it fails or something.  And ppp0 is not configured?

Any help?

---

### Post by tim356 on 2008-01-15
Anyone got any ideas?  I'd really like to get this aircard working on Ubuntu.

---

### Post by McHenry on 2008-01-15
I am having problems with this cards too and receive exactly the same response.

Looking through your post for any differences to my setup I noticed you are using @bigpond.com.au are you sure it's not simply @bigpond.com ?

---

### Post by tim356 on 2008-01-16
Well that's another thing I was unsure about - do you need a username and password at all?  When you use this thing on windows, you simply install the software and connect - there is no username and password.

---

### Post by McHenry on 2008-01-17
Yes username and password are required.

Tell me how many green lights are showing on your card ?

Have you used it under Windows yet to check it's all working before trying Linux ?

---

### Post by tim356 on 2008-01-17
> **McHenry said:**
> Yes username and password are required.

Tell me how many green lights are showing on your card ?

Have you used it under Windows yet to check it's all working before trying Linux ?
I've found out that depending on your plan, a username and password may not be necessary.  There are 2 green lights on my modem - a power and a data light.  I have used the modem on windows and it connects fine.

---

### Post by McHenry on 2008-01-17
Do you have any other network adapters on the box wireless or otherwise ?

Can you post the contents of your /etc/network/interfaces

---

### Post by tim356 on 2008-01-17
Figured out the problem.  There are profiles on the telstra sim (ie pcpack, datapack and internet).  My windows machine was connecting through the telstra.datapack profile fine, but none of the others.  So I changed the profile it uses through ubuntu (dial *99***[profile #)#) and it connected fine.  Although then it was showing that it had a weird IP (10.64.64.64), which after adding a route through ppp0 didn't seem to affect anything.

So now it's all working.

---

### Post by McHenry on 2008-01-17
I think I only have 1 profile as when I plug the card in it shows in dmesg:

[ 1905.538429] usb 4-1: configuration #1 chosen from 1 choice

Glad it's working... I'm using *99# to dial.

---

### Post by timboe on 2008-04-26
> **tim356 said:**
> Anyone got any ideas?  I'd really like to get this aircard working on Ubuntu.

I was having the same problem, I worked out that phone number was incorrect.

Try phone number *99****3#, the 3 on the end seems to denote what plan you are on, eg 1 = telstra.pcpack, 2 = telstra.datapack & 3 = telstra.internet.

---

