---
title: "Ethernet Speed Test"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by karlw on 2008-10-05
I have a question about the connection speed that I get over my home network.  A little bit of background.  I have a a very simple setup:

1 - Ubuntu Hardy desktop
1 - Macbook

These are connected with a Netgear router, which is a wired connection.  My issue is that when I transfer a large file between the two PCs, the speed of the transfer never goes over 10 MB/s.  The best speed I have seen is 9.3 Mb/s.  It seems that this system is limited by something on the network.  Now, as this is not a Mac/Netgear/Ubuntu form, I will restrict my questions to the Ubuntu side of things.  But I can say, that I have confirmed that the Mac and the router are operating in 100 Mb/s mode.  Also, running the following command:
```
sudo ethtool eth0
```
returns the following info:
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000000 (0)
	Link detected: yes

```

which also confirm the connection speed.

Now, this shows that the link speed is at 100 Mb/s, but i seem to be hitting a wall at 10 Mb/s.  I am using Samba to create a network share.  Is there another configuration setting that I am missing?  Maybe something in Samba?  I'm at a loss at even what to google anymore.

Also, I can confirm that when I move a large file around on my Ubuntu PC, locally from one HD to another, I see transfer speeds of about 14 Mb/s.

Thanks in advance!

---

### Post by jmbargar on 2008-10-05
When you send a file from your computer 1 to your computer 2 inside your local network, the first computer upload the file and the second one download it.

The wired cards usually have two asymmetric speeds, one of them is for uploading and the other one if for downloading. If your have two 10/100 networks cards installed in your machines, the download speed will be 100 Mb/s but the upload speed will be only 10 Mb/s.

In the situation that you describe, one computer always have to upload the file, this computer impose the speed limit, that's why the top speed is 10 Mb/s.

---

### Post by cariboo on 2008-10-05
You can try iperf to check network speed. Iperf is available in the repositories. You will have to search for a Mac version. 

This is the output I get from ethtool:

```
sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
```

I set up iperf on my server to run in server mode:

```
iperf -s
```

This is the result:

```
iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
```

I then ran on my home computer:

```
iperf -c sever -d
```

This runs iperf in dual mode checking upload and download speeds. THe result is this:

```
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.100 port 46813 connected with 192.168.1.200 port 5001
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.200 port 36445
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.1 sec    111 MBytes  92.6 Mbits/sec
[  4]  0.0-10.2 sec    103 MBytes  85.2 Mbits/sec
```

Just as a note there is a Linksys wrt54gs router and a 100Mb switch between the two computers.

Jim

---

### Post by miegiel on 2008-10-05
@ jmbargar
> **jmbargar said:**
> The wired cards usually have two asymmetric speeds, one of them is for uploading and the other one if for downloading. If your have two 10/100 networks cards installed in your machines, the download speed will be 100 Mb/s but the upload speed will be only 10 Mb/s.

To my knowledge this is not true. Unless you mess around with your network card's setup, (utp wired) network cards are full-duplex and symmetrical.


@ karlw
Make sure you're not confusing Mbits and Mbytes. For you network 1byte = 8bit. So a 100Mbit network connection will never let you transfer at a speed greater than 12.5 Mbyte/s. However protocol overhead can account for another 10% speed loss, depending on the used network protocol. In general 10Mbyte/s is a good speed on a 100Mbit/s network.

ps. Your file browser will probably give you a speed in (M,k) bytes.

---

### Post by jmbargar on 2008-10-06
I apologize for my confusion. I was convinced that it was as I said but, Miegiel, I give you a reason. Anyway, I was reading about it and the speed (10/100) could depend on the cable used for connecting the devices.

---

### Post by karlw on 2008-10-12
I would like to thank everyone for their response.  I was able to run iperf on my mac (using [darwin ports]("http://darwinports.com/")).  Using the steps from cariboo, I received the following result:

```

Client connecting to 192.168.1.2, TCP port 5001
TCP window size:   129 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.3 port 57437 connected with 192.168.1.2 port 5001
[  5] local 192.168.1.3 port 5001 connected with 192.168.1.2 port 42621
[  3]  0.0-10.0 sec  28.4 MBytes  23.8 Mbits/sec
[  5]  0.0-10.1 sec    112 MBytes  93.0 Mbits/sec
```
This is a great tool, thanks for pointing this out.  I have some bottle neck, my upload and download are not equal - I would expect the upload and download to be the same.  This could be my network card, I'll be troubleshooting this.  Any suggestion would be helpful.

miegiel's comment about Mbits/sec and MBytes/sec is what I needed.  My network monitor on my Mac shows data transfer in MBytes/sec, not MBits/sec.  I thought my home network was running at 100 MBytes/sec.  My original question was due to my assumptions, thanks for clearing this up!

---

