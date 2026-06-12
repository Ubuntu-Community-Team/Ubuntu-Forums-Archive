---
title: "pppoeconf issues &amp; understanding"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by ShirishAg75 on 2006-07-21
Hi all,
      I configured an ADSL modem/router Huawei MT880 with pppoeconf. I'm able to surf the web using the command

```
pon dsl-provider
Plugin rp-pppoe.so loaded
``` 
 Then after surfing when I give

```
poff
/usr/bin/poff: /bin/kill failed. None stopped 
``` 
I gave the command again 

```
poff
/usr/bin/poff: /bin/kill failed. None stopped 
``` 
 the same thing happens.

     Then again I gave 

```
pon dsl-provider
 Plugin rp-pppoe.so loaded 
``` 

  Then sometimes it gives an error or something 
saying another interface is up already or something 
like tht.


 Then after reading the man I gave

```
poff -a
``` 
   I get some other error but the connection is off.

  Then giving the command while the connection is on

```
ifconfig ppp0
link ecap : Point-to-point protocol
inet address : 59.95.14.24

P-T-P : 59.95.0.1
Mask : 255.255.255.255

UP POINT POINT RUNNING NO ARP MULTICAST
MTU: 1492 METRIC :1
Rx Packets : 18 errors :0
dropped :0 overruns :0
frame :0

Tx packets :5 errors:0
dropped :0 overruns :0
carrier :0 collisons :0
txqueueclean:3

Rx bytes :932 (932.0b)
Tx bytes : 134 (134.0b) 
``` 
Now question time, 
1.    what is this Plugin rp-pppoe.so which is loaded? Is it a library or what & where is it reside(location with the whole path) ?

2. of the two addresses given, one of them would be the dynamic IP which is given by the ISP. Now of the 2 which is dynamic & what is other IP from inet & P-T-P ?

3. The Rx packets & Tx packets would be packets received & send right? If so, what does tx queueclean stand for?

4. Lastly, the poff has many options starting with [-r] [-d] [-c] [-a] [-h] [up-name] , what are these options & what do they mean?


 All of the things are hand-written notes as they appeared on the screen so if some of the things should appear on the same line but appears but on the next line as I've written then it might be what I've written & not on the screen. So the content look might be different but the content itself is 100% accurate.

---

### Post by ShirishAg75 on 2006-07-22
just bumping this up, come on guys somebody plz.

---

### Post by mips on 2006-07-22
Who is your ISP ? 

Get the VPI/VCI information and configure the MT880 for routed mode and NOT bridged mode. Other information you will need is your FULL username and password.

After you have done this simply setup  ubuntu for DHCP and thats that. You do NOT have to run pppoe on your ubuntu machine. this is the easiest way of doing it.

How was windows setup ?

---

### Post by narasim_7 on 2006-07-22
I have already posted a reply in a thread reporting that my dsl via ethernet aka pppoe doesnt work.Shirishag ...i live in chennai and i am using dataone.This dsl via router stuff can be configured but its troublesome to get the control that can be got using a dial up ...so its no use.Dsl via dialing is working well in Windows Xp ,Fedora Core 5 .So possibly ..theres is some snag i would suggest u to take a look at that thread and see whether such a problem exists for you

---

### Post by ShirishAg75 on 2006-07-22
A clarification, this is not me but my friend's laptop, he's connected to a network which apparently has apache configured somewhere. He's just permitted to surf & access his wemails. I don't know much about pppoeconf hence the query, as far as his windows setup is concerned,
he just pulls an ethernet RJ-45 cable+socket from the desktop which is on the network the other end of which goes in the Huawei MT-880 router. This is what I could get from the desktop networked machine.

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : administrator

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection

        Physical Address. . . . . . . . . : 00-11-11-66-A5-C7

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 192.168.1.20

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC

        Physical Address. . . . . . . . . : 00-08-A1-19-F9-8F

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        Autoconfiguration IP Address. . . : 169.254.135.49

        Subnet Mask . . . . . . . . . . . : 255.255.0.0

        Default Gateway . . . . . . . . . : 
``` 

AFA I can see this machine seems to have 2 network cards, is this the server or what? I think one of the cards is for accessing the net while the other is for accessing the internal network, am I right? If I'm right then is it possible to tell or guess which is which?

I know u need the laptop ipconfig file will get tht on Monday to give me guidance but just if this helps. As it is I don't know much about networking but it does seem fascinating enough. 

Also I've heard of some called network scanning tools which can give some kind of map of how many machines are there on the network & how they're configured or something to tht effect. Does anyone have links to these. Apparently it's a small network & they'ven't secured it as of yet so would like to see how the network is laid out also. This is in the next though. The first thing is understanding what I did & what I need to do it right. 
                            Thnx for your time

A further edit @narasim_7 the connectivity works, tht's not the issue, my issue is to understand it so in case if & when problems happen then I would atleast have an idea where to look for the answers __

---

### Post by mips on 2006-07-22
To see which is whih simply start the laptop up in windows and then disconnect one lan cable and check which controller goes down.

I suspect the Intel LAN is the Internet one but could be wrong. Simply configure ubuntu with exactly the same settings as windows, i see dhcp is not used and you would have to specify a gateway which could be 192.168.1.1 but double check this as i'm just taking a stab at it.

Another thing you will have to configure is the DNS servers of the ISP.

---

### Post by ShirishAg75 on 2006-07-22
I think u skim-read my post. The last ipconfig was from the desktop machine. Lemme have all the details on Monday evening & then take off from there. Till that time if anybody can point out some good resources where I can read about pppoeconf that would be nice. Thnx in advance.

---

### Post by mips on 2006-07-22
Well in that case just change the ip address to 192.168.1.21  The rest of the stuff I said still applies.

You need to clarify what the other card is for. he might be doing internet connection sharing on the desktop and the notebook connects to the desktop for all we know. Get a bit more details.

Also FORGET about ppoeconfig. The better thing to do is to let the router do that + all the authentication.

---

### Post by ShirishAg75 on 2006-07-24
Hi all,
       o.k. here are the details from my friend's laptop:-


> Windows IP Configuration

        Host Name . . . . . . . . . . . . : administrator
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-16-36-30-61-C0
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.25
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :  

  The above is when he was connected with the router cable

> Windows IP Configuration
        Host Name . . . . . . . . . . . . : administrator
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:
        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-16-36-30-61-C0

                 The above is when he was disconnected.

> eth0      Link encap:Ethernet  HWaddr 00:16:36:30:61:C0  
          inet6 addr: fe80::216:36ff:fe30:61c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2593166 (2.4 MiB)  TX bytes:135695 (132.5 KiB)
          Interrupt:201 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:78:28:D9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.95.7.115  P-t-P:59.95.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1715382 (1.6 MiB)  TX bytes:56656 (55.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

This is when he was connected with ubuntu.  AFAI can tell it seems eth0 is connected as there is transmission & receive bytes there.Nothing else I've on me at the moment. Can anyone help me have a better connect as it disconnects after every 5 minutes or so. Of course he'll have to do all the updates.

---

### Post by mips on 2006-07-24
I can see two issues here, first one is the realtek chipset, just do a search here for realtek. Second one is that you are using ppoe on the linux box, DONT. Let the router handle the pppoe and authentication.

---

### Post by ShirishAg75 on 2006-07-24
hi mips, 
          Firstly, I'll do the search although I'm not sure what I'm looking for in the realtek chipset. Even I've the same chipset RTL8139+ card in my desktop machine. Please clarify.
           AFA the router is concerned, he's not the only one who gets to handle the network connection. There are 2 other machines who use the Net & they've windows. The policy in the company is tht they need to do authentication on their machine (username & pwd) & only then they can move forward. There is also the possibility tht the company is also using the in-built log. I don't have physical access to the router & also don't want to mess with the router settings. I don't know enough. Instead of using pppoeconf what would u recommend ?

---

### Post by mips on 2006-07-25
Ok, in that case you will have to use pppoe on the pc.

Can you ping 59.95.14.24 & 59.95.0.1 ?

I don't have any experience with pppoe, could I suggest you look in the howto section for some guides.

---

