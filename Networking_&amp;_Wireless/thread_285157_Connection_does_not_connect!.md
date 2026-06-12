---
title: "Connection does not connect!"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by _Manuel_ on 2006-10-26
Hi!
I write from Italy, so my English is not so good, but I'll try to explain.

I've an USB modem (look at the tags of the thread) and the last week I was able to open every kind of page in internet, to download  mail, to update my OS and so on.
But now, I can't do it. My modem is connected, "Every thing is Ok" it says, but I can't open any page, I can't download my mail and I can't use Gaim.

I've the last version of ubuntu (I've downloaded kde and a lot of packages).

My modem requires eciadsl drivers and I've installed them succesfully, in fact till saturday it was all ok.
So, after some attempts, i decidet to format my pc. I've done it, i've installed ubuntu and eciadsl-drivers but I can't connect: I've the same problem. The fact is that the modem runs, in fact if I use Windows XP there are no problems.

DNS are correct and all configuration of the connection is correct, I think (I have not changed it and some days ago it was all ok).

The problem, shortly, is that I try to open a page (with the modem running and synchronized, as confrimed by the command eciadsl-doctor) but it is as if I hadn't pressed: nothing happens! No page can be opened...

What can I do? 



I write some answers to the command "eciadsl-start" and "eciadsl-doctor" 
 ```

[EciAdsl 1/5] Setting up USB support...
 

 Preliminary USB device filesystem is OK
 

 [EciAdsl 2/5] Uploading firmware...
 

 GlobeSpan GS7070 USB ADSL WAN Modem compatible modem found (in 2390ms)
[B] eciadsl-firmware: success
 firmware loaded successfully[/B]
 

 [EciAdsl 3/5] Synchronization...
 
[B]
 OK eciadsl-synch: success  
 Synchronization successful[/B]
 

 [EciAdsl 4/5] Connecting to provider...
 

 Couldn't set tty to PPP discipline: Interrupted system call
 Terminating on signal 2
 Waiting for 1 child processes...
   script /usr/bin/eciadsl-pppoeci -vpi 8 -vci 35 -vendor 0x0915 -product 0x00ca -mode VCM_RFC2364, pid 5965
 Child process /usr/bin/eciadsl-pppoeci -vpi 8 -vci 35 -vendor 0x0915 -product 0x00ca -mode VCM_RFC2364 (pid 5965) terminated with signal 2
 ERROR: failed to connect
 mastrofini@mastrofini-desktop:~$ sudo eciadsl-doctor
 You are using linux kernel version 2.6.15-27-amd64-generic
 Support for USB is OK
 Preliminary USB device filesystem is OK
 dabusb module is not loaded: OK
 UHCI support is not needed
 OHCI support is OK
 /dev/ppp is OK
 HDLC support is OK
 HDLC support is OK (no bug)
 You are using pppd version 2.4.4b1 (untested)
 No existing PPP connection... trying to make one (please wait)
 using channel 1
 Using interface ppp0
 Connect: ppp0 <--> /dev/pts/2
 sent [LCP ConfReq id=0x1 <magic 0x976dbeba>]
 rcvd [LCP ConfReq id=0x58 <magic 0x34105941> <mru 1500> <auth pap>]
 sent [LCP ConfAck id=0x58 <magic 0x34105941> <mru 1500> <auth pap>]
 rcvd [LCP ConfAck id=0x1 <magic 0x976dbeba>]
 sent [PAP AuthReq id=0x1 user="stefania57@flat" password=<hidden>]
 rcvd [PAP AuthAck id=0x1 ""]
 PAP authentication succeeded
 sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
 rcvd [IPCP ConfReq id=0xaf <addr 151.6.148.65>]
 sent [IPCP ConfAck id=0xaf <addr 151.6.148.65>]
 rcvd [IPCP ConfNak id=0x1 <addr 151.37.150.217> <ms-dns1 193.70.152.15> <ms-dns3 193.70.152.25>]
 sent [IPCP ConfReq id=0x2 <addr 151.37.150.217> <ms-dns1 193.70.152.15> <ms-dns3 193.70.152.25>]
 rcvd [IPCP ConfAck id=0x2 <addr 151.37.150.217> <ms-dns1 193.70.152.15> <ms-dns3 193.70.152.25>]
 not replacing existing default route via 192.168.0.1
 local  IP address 151.37.150.217
 remote IP address 151.6.148.65
 primary   DNS address 193.70.152.15
 secondary DNS address 193.70.152.25
 PPP connection is OK
 No default route over ppp0... trying to add
 Default route over ppp0 is OK
 You have default route(s) not over ppp0... trying to delete
 Deleting default route over eth0
** Everything is OK**
 

 mastrofini@mastrofini-desktop:~$ sudo eciadsl-stop
 EciAdsl: shutting down...
 Please wait... disconnecting
 modem disconnected
 stopped.
 mastrofini@mastrofini-desktop:~$ sudo eciadsl-start
 

 [EciAdsl 1/5] Setting up USB support...
 

 Preliminary USB device filesystem is OK
 

 [EciAdsl 2/5] Uploading firmware...
 

 Warning: firmware seems to be already loaded
 Check that your modem is OFF before running eciadsl-start (if modem is
 powered on, then unplug/replug it)
 

 [EciAdsl 3/5] Synchronization...
 
[B]
 OK eciadsl-synch: success  
 Synchronization successful[/B]
 

 [EciAdsl 4/5] Connecting to provider...
 

 using channel 2
 Using interface ppp0
 Connect: ppp0 <--> /dev/pts/2
 sent [LCP ConfReq id=0x1 <magic 0xa41e8e59>]
 sent [LCP ConfReq id=0x1 <magic 0xa41e8e59>]
 sent [LCP ConfReq id=0x1 <magic 0xa41e8e59>]
 rcvd [LCP ConfReq id=0x59 <magic 0xf1be731> <mru 1500> <auth pap>]
 sent [LCP ConfAck id=0x59 <magic 0xf1be731> <mru 1500> <auth pap>]
 rcvd [LCP ConfAck id=0x1 <magic 0xa41e8e59>]
 sent [PAP AuthReq id=0x1 user="stefania57@flat" password=<hidden>]
 rcvd [PAP AuthAck id=0x1 ""]
 PAP authentication succeeded
 sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
 rcvd [IPCP ConfReq id=0xb0 <addr 151.6.148.65>]
 sent [IPCP ConfAck id=0xb0 <addr 151.6.148.65>]
 rcvd [IPCP ConfNak id=0x1 <addr 151.38.222.213> <ms-dns1 193.70.152.15> <ms-dns3 193.70.152.25>]
 sent [IPCP ConfReq id=0x2 <addr 151.38.222.213> <ms-dns1 193.70.152.15> <ms-dns3 193.70.152.25>]
 rcvd [IPCP ConfAck id=0x2 <addr 151.38.222.213> <ms-dns1 193.70.152.15> <ms-dns3 193.70.152.25>]
 local  IP address 151.38.222.213
 remote IP address 151.6.148.65
 primary   DNS address 193.70.152.15
 secondary DNS address 193.70.152.25
** Connection successful**
 

 [EciAdsl 5/5] Setting up route table...
 

 Waiting for ppp0...
 mastrofini@mastrofini-desktop:~$ sudo eciadsl-doctor

```

---

### Post by _Manuel_ on 2006-10-28
Lol, nobodoy can help me?

---

