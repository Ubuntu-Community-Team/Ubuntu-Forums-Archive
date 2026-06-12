---
title: "PPPoE+Aztech dsl600e, connection drops regularly"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by mikewhatever on 2007-08-24
Presently, I use pppoe for internet connection with Aztech ADSL2 dsl600E modem/router connected to the ethernet port. The username and password authentication works and I get connected, the problem is that the connection drops every 15-20 minutes. I can then disconnect and reconnect for another similar period of time. I've tried different variations of commenting out and uncommenting lines to no avail. I have not the slightest idea how to solve or even diagnose it. pppoeconfig detects the modem and here is the dsl-provider file it generated:
cat /etc/ppp/peers/dsl-provider

> # Minimalistic default options file for DSL/PPPoE connections

noipdefault

defaultroute

replacedefaultroute

hide-password

#lcp-echo-interval 60

#lcp-echo-failure 4

noauth

persist

#mtu 1492

#persist

#maxfail 0

#holdoff 20

plugin rp-pppoe.so eth0

usepeerdns

user "xxxxxxxxxxx"


Here's some more stuff that looks useful.
In Windows, the ipconfig output looks as follows:

> Ethernet adapter local area connection:

	Connection-specific DNS suffix:
	IP address   10.0.0.1
	Subnet mask  255.255.255.0
	Def. Gateway  10.0.0.138

PPP adapter adsl:

	Connection-specific DNS suffix:
	IP address  132.64.xxx.xxx
	Subnet mask 255.255.255.255
	Def. Gateway  132.64.xxx.xxx same as IP

Two dns servers are assigned: 128.139.xxx.xxx,  128.139.xx.xx

In Ubuntu, here is the output of ifconfig while connected:

>  #eth0      Link encap:Ethernet  HWaddr 00:16:D4:43:80:1B  

          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0

          inet6 addr: fe80::216:d4ff:fe43:801b/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:555 errors:0 dropped:0 overruns:0 frame:0

          TX packets:499 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:482489 (471.1 KiB)  TX bytes:90801 (88.6 KiB)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:168 (168.0 b)  TX bytes:168 (168.0 b)



ppp0      Link encap:Point-to-Point Protocol  

          inet addr:132.64.xxx.xxx  P-t-P:132.64.xxx.xxx  Mask:255.255.255.255

          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1

          RX packets:510 errors:0 dropped:0 overruns:0 frame:0

          TX packets:437 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:3 

          RX bytes:466751 (455.8 KiB)  TX bytes:76291 (74.5 KiB)


Searching for solutions, I found a very similar issue [http://ubuntuforums.org/showthread.php?t=106847&highlight=aztech](http://ubuntuforums.org/showthread.php?t=106847&highlight=aztech)

Following the advice given by Raja, I've added the mentioned dns addresses to DNS tab. The following was already there – 10.0.0.138. That made no difference. The connection dropped as before, and the addresses I've added to DNS tab got deleted. In fact, every time I manually start pppoe, the aforementioned addresses appear in the DNS tab automatically, and every time the connection drops, they disappear and 10.0.0.138 is back there.

Hope someone has good suggestions.

Edit: Here is what I found in /var/log/messages, when starting pppoe
> Aug 25 13:56:39 xxx pppd[7411]: Plugin rp-pppoe.so loaded.
Aug 25 13:56:39 xxx pppd[7413]: pppd 2.4.4 started by root, uid 0
Aug 25 13:56:39 xxx pppd[7413]: PPP session is 54627
Aug 25 13:56:39 xxx pppd[7413]: Using interface ppp0
Aug 25 13:56:39 xxx pppd[7413]: Connect: ppp0 <--> eth0
Aug 25 13:56:41 xxx pppd[7413]: PAP authentication succeeded
Aug 25 13:56:41 xxx pppd[7413]: peer from calling number xxxxxxxxxxxx authorized
Aug 25 13:56:41 xxx pppd[7413]: replacing old default route to eth0 [10.0.0.138]
Aug 25 13:56:41 xxx pppd[7413]: local  IP address 132.64.xx.xx
Aug 25 13:56:41 xxx pppd[7413]: remote IP address 132.64.xx.xx
Aug 25 13:56:41 xxx pppd[7413]: primary   DNS address 128.139.xx.xx
Aug 25 13:56:41 xxx pppd[7413]: secondary DNS address 128.139.xx.xx

and on manually disconnecting
> Aug 25 13:55:11 xxx pppd[6325]: Terminating on signal 15
Aug 25 13:55:11 xxx pppd[6325]: Connect time 28.5 minutes.
Aug 25 13:55:11 xxx pppd[6325]: Sent 377265 bytes, received 5935726 bytes.
Aug 25 13:55:11 xxx pppd[6325]: restoring old default route to eth0 [10.0.0.138]
Aug 25 13:55:11 xxx pppd[6325]: Connection terminated.
Aug 25 13:55:12 xxx pppd[6325]: Exit.

---

### Post by mikewhatever on 2007-08-26
I found a netconf file for pppoe on the Windows partition. Here is the content
> [info]

display_name=PPPOE modem

image=samsung.jpg

description=xxxxx

manufacture=NetGame Cables





[dial up connection]

;

Connection_Name=adsl

Connection_IP=

DialerDescription=SpeedTouch

NoNIC=0

PPPOE=1

;

Server type=PPP

Enter net=0

Enable compression=1

Demand encrypted password=0

Use NetBEUI=0

Use IPX/SPX=0

Use TCP/IP=1

;

Get IP from server=1

Get DNS from server=1

ISP_DNS_Server_IP=0.0.0.0

ISP_DNS2_Server_IP=0.0.0.0

ISP_WINS_Server_IP=0.0.0.0

ISP_WINS2_Server_IP=0.0.0.0

Use IP title compression=1

Use remote default gateway=1





//ipmtu default is 0    - automatic

	           576  - samll

		   1000 - medium

		   1500 - large		

mtu=1431



//NT RAS Encryption settings

//  0 - allow any

//  1 - require encryption

//  2 - require microsoft encryption



ForceEncryptPassword=0

ForceEncryptData=0







[win2k_security]

;data_encryption Value Meaning 

;Require encryption                                       0

;Require strong encryption 				  1	

;No encryption 						  2

;Require encryption 					  3

;Require maximum-strength encryption. 		  	  4

;Do encryption if possible. No encryption is okay.     	  5



advanced=1

require_data_enc=1

//

data_encryption=5

//logon security

use_EAP=0

PAP=1

SPAP=0

CHAP=0

MS_CHAP=0

MS_CHAP_95=0

MS_CHAP_V2=0

MS_CHAP_AUTO=0

show_progress=1

preview_user_psw=1



[TCP]

Wins=0

Gateway=

IP=10.200.1.1

Mask=255.0.0.0

DNS Enabled=0

localhost=

domain=

DNS List=

Suffix List=



[Browser]

HomePage=www.bezeq.co.il

InstallProgram=cd:\data\browsers\win95\ie5setup.exe



[misc]

Fwnetins params=-t -d -r -w -l -a*PNP8386



[setup]

LaunchAuto=0



[Driver]

MaxSessions_9x=1

MaxSessions_NT=1

; Seconds

EchoInterval=10

MaxMissedEchos=3

ConnectSpeed=10000000












---

### Post by mikewhatever on 2007-08-28
Found a guide, [http://www.mulix.org/adsl-howto.txt](http://www.mulix.org/adsl-howto.txt). They seem to suggest using stuff called pptp, which is supposed to be similar to MS VPN. No idea what either of those are. Just for the record, so far, no matter what I try, the connection either disconnects or does not work at all. This is just a guess work, since I am no pppoe expert, and have no intention of becoming one. Any help, suggestion or advice would be much appreciated.

---

### Post by mikewhatever on 2007-09-02
Well, thanks to everyone that looked at this thread. I've got a di-524 wireless router which has no trouble maintaining the connection through pppoe and was very easy to set up. Out of curiosity, I'd still like to know how to solve or diagnose that problem.
Thanks.

---

