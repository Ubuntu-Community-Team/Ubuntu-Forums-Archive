---
title: "Poweredge 2950 slow network speed, 12.04"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by garyi on 2014-04-30
Hello. I am at my wits end!

I have installed ubuntu and all is well apart from network issues left right and centre.

I can ping the server no issues speeds the same as anything else on my network

But anything concerning network is slow on that server. For instance I have ran a broadband speed test on that server which reports 17Mb/s from my imac on the network 150Mb/s

Lan speeds are terrible, I am getting network speeds of less than 4MB/s I am doing a copy from an old server to it 300 gigs is down for 4 days to copy.
The same files copied to my mac, less than 2 hours.

This is the details of the card nic in use:

network               
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet [14E4:164C]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:1a:a0:1a:20:4e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.3 duplex=full firmware=bc 2.9.1 ip=192.168.0.97 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:105 memory:f8000000-f9fffff


It seems like it should all be as quick as everything else on my network.

I have searched the googles of which of course there is 7.5 billion results, I tried a couple but no improvement at all.

The lan copy is over samba but my problem is the entire nic is slow even though it says its fast.


The server is second hand, I wondered if perhaps the ethernet was somehow set up at bios or something to be something different but am not sure on the front. 

I would really appreciate some advice on this one, I really want ubuntu to work as its fine for what I need but its primary purpose is a file server which is going to be am issue at these speeds.

---

### Post by garyi on 2014-04-30
One other thing copying from the ubuntu, i.e. mounting it under samab on my mac I am able to achieve speeds of 17MB/s (The same speed as the broadband speed test on the server) which is better but my network throughput easily hits 607-MB/s no problem

---

### Post by garyi on 2014-04-30
here is another output.

	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

---

### Post by tgalati4 on 2014-04-30
Try changing cables and ports on your router.  Put dedicated mounts in /etc/fstab to improve transfer speeds.

---

### Post by garyi on 2014-04-30
Its not my switch or cables. It either the nic or ubuntu.

I'll try and find out what dedicated mounts is, cheers.

---

### Post by garyi on 2014-04-30
Hi, mounts seems to be to do with mounting drives? I don't see what thats got to with for instance internet speed being 10 times slower on the server compared to the rest of my network? Would you be able to expand on what you mean?

---

### Post by SeijiSensei on 2014-04-30
Broadcom adapters can be tricky under Linux because they are not open-source.  

If the server has a GUI environment, you can try this.  (Ubuntu Server comes with only a text-mode interface by default, though there are ways to add a GUI.)

Open the Package Manager and find the "Configure Software Sources" item.  In the dialog box that follows, make sure the "proprietary drivers" item is check.  Then update the sources; usually this will happen automatically, but if it doesn't, there will be a command to force an update.

Now exit the Package Manager, and run the "Additional Drivers" application in the "System" menu.  See if it detects a driver for your card and install it.  Any better?

I usually specify [Intel adapters]("http://www.newegg.com/Intel-Network-Interface-Cards/BrandSubCat/ID-1157-27") when buying servers.  They work flawlessly with Linux since Intel has released open-source drivers for their network adapters.  If you can't get satisfaction with the Broadcom, I'd invest the $30 or so and buy an Intel.

---

### Post by garyi on 2014-04-30
Thank you for your help. I installed another network card, though it could be the same chip with the same issue, i.e. a start of a copy can start out at a fair clip say 45MB/s then is degrades rapidly until down to a bare whisper.

I will check out your suggestion now see if it helps.

---

### Post by garyi on 2014-04-30
I do not have a package manager but do have an update manager where proprietary drivers were already checked, I then did the additional drivers it and came back with nothing.

I suppose if its a driver from the manufacturer issue then this won't be any better under red hat or what ever?

I'll get a intel card, but am just worried it won't be any better.

---

### Post by garyi on 2014-04-30
Looking about the web I can see linux drivers for the particular chip set but the install instructions are to say the least intimidating.

---

### Post by garyi on 2014-04-30
SO it turns out my new card is different chip:

[COLOR=#000000][FONT=verdana]0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

[/FONT][/COLOR]And its doing exactly the same thing. I tried updating to 12.10 the other day but it warned that the graphics were not supported and sure enough once done I had no display.

Sigh. I guess its going to have to be windows server.

---

### Post by tgalati4 on 2014-04-30
Dedicated mounts:  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by garyi on 2014-04-30
Hi thanks for the link, but thats not the issue. As the internet speed is a massive problem as well it seems to be an issue of the drivers for both of the NICs I have tried. According to the ubuntu site the only distribution certified for a dell 2950 is 10.04 so perhaps I will have to try this and get used to working in terminal all the time lol. 

I have now tried the server on two known good network points and with a variety of cables. Issues persist.

---

### Post by garyi on 2014-04-30
OK, I installed win 2008 and sure enough network speeds bang on, internet showing 150Mb/s on broadband speed checker so the issue is the driver in ubuntu, what a real shame.

---

### Post by garyi on 2014-05-04
Back in ubunutu as I got an intel based ethernet card.

The problem is the same. What ever this issue is its an ubuntu issue. 

General internet speed appears to be resolved I think
uncommented these lines from smb.conf
[COLOR=#000000]
[/COLOR][COLOR=#000000]SO_RCVBUF=8192 SO_SNDBUF=8192[/COLOR]
[COLOR=#000000]socket options = TCP_NODELAY[/COLOR]

Which gave a speed boost so now a copy starts out at 55MB/s but as you watch that copy progress as the bar fills up the network speed drops, 55, 54, 53, 52 looking at it now ten minutes in its down to 29. If the transfer is big enough this will continue until the speed is down to 3/MBs and many days to complete the transfer.

Surely this should give some hints to the problem?

I really want to use ubuntu but having tried 12 and 10 this issue is the same.

Does anyone else use a poweredge 2950?

---

### Post by SeijiSensei on 2014-05-04
Is the server running Windows so you are limited to SMB?  If it's running a Unix variant, you should be using NFS or maybe sshfs.  Rsync is another good choice.  I don't use SMB for any purpose other than serving files to Windows machines.  There are much better options for Unix-to-Unix file transfers.

The Samba developers warn against changing SO_* in the man page for smb.conf:
"Linux in particular has an auto-tuning mechanism for buffer sizes that will be disabled if you specify a socket buffer size. This can potentially cripple your TCP/IP stack."

---

### Post by slasc on 2014-10-16
> **garyi said:**
> Back in ubunutu as I got an intel based ethernet card.

The problem is the same. What ever this issue is its an ubuntu issue. 

General internet speed appears to be resolved I think
uncommented these lines from smb.conf
[COLOR=#000000]
[/COLOR][COLOR=#000000]SO_RCVBUF=8192 SO_SNDBUF=8192[/COLOR]
[COLOR=#000000]socket options = TCP_NODELAY[/COLOR]

Which gave a speed boost so now a copy starts out at 55MB/s but as you watch that copy progress as the bar fills up the network speed drops, 55, 54, 53, 52 looking at it now ten minutes in its down to 29. If the transfer is big enough this will continue until the speed is down to 3/MBs and many days to complete the transfer.

Surely this should give some hints to the problem?

I really want to use ubuntu but having tried 12 and 10 this issue is the same.

Does anyone else use a poweredge 2950?

Did you get this fixed?  I have a Poweredge 2950 as well, and I've been having weird issues with it the last few days.  They seem to be networking related.  Whether via IMAP, SSH,VNC, or Samba, I am getting extremely slow network speeds.  When accessing it directly, I can see the processor use is roughly at .02% and the network use even seems very low.  It's just not responding to requests over the network in a timely fashion or with good speeds.  Trying to check for updates using 'sudo apt-get update' or 'sudo apt-get upgrade' is extremely slow (hours instead of seconds like it used to be).  I recently upgraded to 12.04.5 because I saw that my HWE was no longer supported (seriously, isn't the whole concept of LTS supposed to avoid these issues?).  I'm very frustrated, and I'm hoping you might have some insight.

---

