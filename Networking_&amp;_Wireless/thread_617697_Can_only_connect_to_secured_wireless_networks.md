---
title: "Can only connect to secured wireless networks"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by ender8282 on 2007-11-19
OK everyone else seems to have the opposite problem from me.  I have 2 secured wireless networks that I connect to on a regular basis (one at home and one at work). I have a short script that I use to connect.  (eventually I am going to write my own network utility but haven't had time yet).  The scripts looks like:
 ```

sudo iwconfig eth1 mode managed
sudo ifconfig eth1 down
sudo iwconfig eth1 essid SOME_ESSID key SOME_KEY
sudo ifconfig eth1 up
sudo dhcpcd eth1

```
After running the script I get the message 
```

dhcpcd.exe: interface eth1 has been configured with new IP=192.168.1.100

```
Everything works and I can browse the internet and write this post.  
Now my problem:
When I try to connect to an unsecured network I don't get result. 
I use a similar script to try to connect to an unsecured network.
```

sudo iwconfig eth1 mode managed
sudo ifconfig eth1 down
sudo iwconfig eth1 essid SOME_OTHER_ESSID
sudo ifconfig eth1 up
sudo dhcpcd -d -t 10 eth1

```
I lowered the time out to 10 seconds because I was impatient but it fails with the default 60 second time out as well.  The debug message reads:
```

Nov 19 13:43:46 jhubbard-laptop dhcpcd[6711]: broadcasting DHCP_DISCOVER        
Nov 19 13:43:53 jhubbard-laptop dhcpcd[6711]: timed out waiting for a valid DHCP server response 

``` 

So my question is why am I failing to connect to unsecured wireless networks.  I would like to do everything from the command line (so eventually I can write my own wireless management utility).  If there is more information you need feel free to ask.  Thanks in advance.

---

### Post by reckless2k2 on 2007-11-19
does the unsecured net show up with iwlist? 

can you see it in the GUI? 

can you connect via the GUI? 

does the unsecured net have dhcp running to issue addresses?

---

### Post by ender8282 on 2007-11-20
```

jhubbard@jhubbard-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:B6:79:C6
                    ESSID:"HIPPOWIRELESS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:B5:67:F0:22
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

The Netgear network is one of the networks that I have tried to connect to.  I have seen a much stronger signal (in the 50s) when I am at the other end of my house, and I can connect to it with this machine when I boot to windows.  

I can see it with my gui tool (Wireless Assistant) but I cannot connect to it with the GUI tool.  It tries to connect and then says 'connection failed' and asks if I want to review network settings.  I take a look and a bunch of grayed out fields and a check in the DHCP box.

---

### Post by reckless2k2 on 2007-11-20
i guess you have eliminated some of the questions but not the last. if this is your router, i'd suggest to disable any possible encryption and broadcast the SSID (looks like it is already) and then try to connect right next to it. i would say it might be an encryption or MAC filtering issue. it doesn't seem to be hardware on your end.

---

### Post by ender8282 on 2007-11-20
Sorry I missed the last question.  I don't know much about the Netgear network that I am trying to connect to.  It is a neighbor's (I don't know whose) network.  I do know that I can successfully connect to THAT network with THIS  laptop when I boot under windows.  This suggests that the problem is not with the network accepting my connection request but with the way that I request a connection.  Under windows the network does function as a dhcp server and assigns me an IP address.  
So in short I don't have control over the network and I don't know whether or not the network uses any kind of security but I don't believe it does (based on my ability to connect under windows).  
Hope this answers your questions.

---

### Post by reckless2k2 on 2007-11-20
i'm sorry i can't be of more help myself. i know i've had various issues connecting depending on vendor or wifi card being used or even what driver being used. good luck.

---

### Post by ender8282 on 2007-11-22
Thanks for trying to help. Reckless2k2  
I would love to better understand how linux handles wireless networks as well as how wireless networks work in general.  
Is my first attempt at connection with the wireless access point when I request an IP address from it or is there information exchanged before that?  
Is there any way to see more information (a higher debug level) about what messages I am sending to the access point/DHCP server?  
With a regular server (google.com) I can ping it and see if I get a response.  (ping [www.google.com](www.google.com)) Is there any way to 'ping' a wireless access point?  
is a  ```
iwlist eth1 scan
``` like a ping or is my wireless controller just listening for who is out there?  
My network does not broadcast ESSID.  I see it in a scan only when I am connected to it.  Why is this.  
Again thanks in advance for any advice/assistance.  I have no problems reading man pages so if I missed this information is in some man page just point me to that page.

---

### Post by kevdog on 2007-11-22
Ok, I dont know anything about dhcpcd
sudo dhcpcd -d -t 10 eth1

I usually use a line like this:
sudo dhclient eth1

To drop the lease its
sudo dhclient -r eth1

If you put this line in place does it make a difference (I fear it will not!).

---

### Post by ender8282 on 2007-12-03
Thanks for the help. Sorry that it took me so long to respond but I was out of town for a while.   When I use the dhclient command 
```

sudo dhclient eth1

```
I get the response
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:cf:8f:80:98
Sending on   LPF/eth1/00:16:cf:8f:80:98
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So this doesn't really fix my problem but it does give me more information about what is wrong.  
After this command failed I rebooted to XP and was able to connect to the network.  So it is not a problem with the server it is a problem with how I am connecting.  Based on the fact that I am not receiving an ip offer I would assume that I am not properly connecting to the server.
Is the problem with one of the other commands?
```

sudo ifconfig eth1 down
sudo iwconfig eth1 mode Managed essid 'NETGEAR'
sudo ifconfig eth1 up

```
Is there any way that I can get more information from ifconfig and/or iwconfig?  
According to the man page for iwconfig there is a 'commit' option.  Can someone confirm that commit is not needed when ifconfig down/up are used.  
Thanks again.

---

