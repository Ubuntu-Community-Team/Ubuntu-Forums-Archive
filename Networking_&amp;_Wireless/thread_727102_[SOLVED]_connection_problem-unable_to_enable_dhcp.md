---
title: "[SOLVED] connection problem-unable to enable dhcp"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by robby_dobby on 2008-03-17
Hi,

I'm running ubuntu on an old box, PIII 700MHz 256MB RAM 80 GB HDD. [:)]. I am connected via an ADSL Router which has a provision for DHCP. My problem is, right now I am connected through the static IP address provided for temporary use by my ISP with a further warning to switch over to DHCP at the earliest possible since they usually allot IP addresses via the DHCP mode. Before you guys blast me about reading the previous posts,  let me tell you that I have tried setting up DHCP from the terminal by accessing interfaces config file and changing the relevant lines. Then I tried running the dhcpcd daemon along with resolvconf to automatically allot DNS. I have also restarted the network from the terminal by giving 'sudo /etc/init.d/networking restart' command.

What have I left out?? My ethernet card and all is perfectly recognised by ubuntu. 


I have included all I have done below with their outputs for convenience: 

altering /etc/network/interfaces
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp 


here's the fault : I try to run dhcpd daemon and it just times out. (I use resolvconf, so I didn't need to alter dhcpcd much except set an option -s {sum IP address} if DHCP fails to properly obtain IP address)
> 
$ sudo dhcpcd -d eth0
Info, eth0: dhcpcd 3.0.17 starting
Info, eth0: hardware address = 00:40:f4:c1:ef:b2
Info, eth0: deleting IP address X.X.X.X/24
Info, eth0: broadcasting for a lease of X.X.X.X
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Debug, eth0: waiting on select for 20 seconds
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Debug, eth0: waiting on select for 15 seconds
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Debug, eth0: waiting on select for 14 seconds
Debug, eth0: waiting on select for 12 seconds
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Debug, eth0: waiting on select for 10 seconds
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Debug, eth0: sending DHCP_REQUEST with xid 0x241e98a8
Error, eth0: timed out
Info, eth0: exiting


and, finally I give ifconfig (FYI)
> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:C1:EF:B2  
          inet6 addr: fe80::240:f4ff:fec1:efb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6324587 (6.0 MB)  TX bytes:1441570 (1.3 MB)
          Interrupt:5 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


it shows some received and transmitted bytes since I was running it under static IP addressing before trying to switch to DHCP.

Any pointers to rectify this?? :) :)

---

### Post by Eiríkr on 2008-03-17
Assuming you're running Gutsy, do you have Network Manager installed?  It sounds like you might; NM will often override whatever manual changes have been made to the interfaces file.  Try opening NM, then click Wired Connection, hit the Properties button, and make sure the Configuration dropdown is set to "Automatic configuration (DHCP)".  I suspect you currently have it on "Static IP address".

HTH,

Eiríkr

---

### Post by robby_dobby on 2008-03-17
Hi,

Thanks for your reply. I'm running Ubuntu Gutsy with NM. No, it doesn't override anything. All changes made in the terminal are directly reflected here. The problem still persists.

---

### Post by Eiríkr on 2008-03-17
Does NM respect manual changes even after a reboot?  I dimly recall hours of frustration trying to find out why rebooting overwrote my interfaces file...

---

### Post by robby_dobby on 2008-03-17
Hi,

 Yes, it does. In fact, I use static IP addressing for accessing the net and I am able to do that every time I boot up the box. No problems there too. Actually, I was thinking along the lines of DNS allocation(that was before I installed resolvconf and it worked fine too. I mean, the DNS normally used for connecting up to my ISP are all there). So, what gives???

---

### Post by robby_dobby on 2008-03-17
ok. I ll give this another try with dhcp3 client.

---

### Post by robby_dobby on 2008-03-17
Am I doing anything wrong here??? Please indicate if I am wrong. :) :)

---

### Post by robby_dobby on 2008-03-18
ok... some more news. It's been a long day at work, so couldn't look into this immediately then. Well, as mentioned before, I ran the dhclient to obtain IP address with the result as follows.

> 
$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:f4:c1:ef:b2
Sending on   LPF/eth0/00:40:f4:c1:ef:b2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Then, I run ifconfig only to find an IP address allotted by the avahi daemon and no connectivity. This is what was displayed.

> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:C1:EF:B2  
          inet6 addr: fe80::240:f4ff:fec1:efb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12828600 (12.2 MB)  TX bytes:1176799 (1.1 MB)
          Interrupt:5 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:F4:C1:EF:B2  
          inet addr:169.254.11.162  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4680 (4.5 KB)  TX bytes:4680 (4.5 KB)




Any help here???

---

### Post by Eiríkr on 2008-03-18
I'd have a look at the router.  The complete lack of any DHCP offers suggests that it's not your DHCP client setup that's the problem, but rather either a complete lack of connection to the DHCP server (the router), or a problem with the DHCP server itself (like not being enabled, or being misconfigured).  

Cheers,

Eiríkr

---

### Post by robby_dobby on 2008-03-18
Thanks for your reply.

I admit I am unable to follow the concept of DHCP server. I mean, the configuration for the DHCP server and DHCP client should be done on the same machine(my box here) with the router at the ISP's end??? :confused: And, when I was using XP (that was some time ago :) ), all I had to do was click on the radio buttons that said Automatically assign IP address and DNS from TCP/IP properties. ??? :confused:

---

### Post by Eiríkr on 2008-03-18
The bit in Windows about "Automatically assign IP address and DNS from TCP/IP properties" is somewhat mislabeled in Windows (no surprise there :-|), as the IP address and DNS settings are assigned by the DHCP server -- usually a router if you have one, or possibly the ISP if you're connecting to them directly and you don't have a router.  

> I admit I am unable to follow the concept of DHCP server. I mean, the configuration for the DHCP server and DHCP client should be done on the same machine(my box here) with the router at the ISP's end???  

The DHCP server is a special program that assigns DHCP addresses to client programs that request them.  The DHCP server and client programs are pretty much **never** on the same machine (except perhaps in fringe-case experimental setups or similar).  You noted in your initial post:
> I am connected via an ADSL Router which has a provision for DHCP...

Assuming the DSL modem is **also** acting as a router, it would then likely have a DHCP server program included in its firmware.  Many modems and routers allow you to connect to them by typing their IP addresses into your browser; my DSL modem is at 192.168.0.1, and I have my router (since my particular modem does **not** include router functionality) manually assigned to 192.168.10.1, so I can access one or the other simply enough via my browser.  Try typing [font=courier]http://192.168.0.1[/font] into your browser and see if this connects you to your DSL modem (this address is a common default).  

If you cannot access your DSL modem and cannot find any documentation from your ISP that describes how to do so, contact your ISP again and explain that you cannot find out how to get an address via DHCP.  Explain that you've attempted to get an address, but "received no DHCP offers".  This last point is important, as it should make it clear that your DHCP client program did indeed attempt to get an IP address.  Ask them if there is a specific IP address for accessing the modem, and if there are any instructions for setting up the DHCP server on the modem.  

HTH,

Eiríkr

---

### Post by robby_dobby on 2008-03-18
Ah, that cleared the air! :) I'm sorry I messed up on the description which should have read ADSL modem connecting to the router at the ISP's end. I stand corrected. :( 
In fact, I connect to the net in a way similar to what you had described. Now, I'm able to connect to the router by typing in the IP address. And, a little search around revealed that they had actually disabled the DHCP server. I will talk to the ISP's technical support and clear this up. Many thanks!! :) :)

---

### Post by Eiríkr on 2008-03-18
Wow, that's great!  I'm surprised they disabled the DHCP server but gave you no instructions for how to re-enable it; I hope the phone call goes well.  :D  

Cheers,

Eiríkr

PS -- If this pretty much resolves your issue, please also remember to mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)  Thanks!

---

### Post by robby_dobby on 2008-03-18
For now, I had set a temporary work around by setting two options to eth0 in the interfaces config file as follows: 

> 

auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0 inet static
{and, so n so about static ip details }
 


So, this works for now. Still need to enable DHCP if my earlier talks with the ISPs are any indication. 

Cheers,

Robby

---

