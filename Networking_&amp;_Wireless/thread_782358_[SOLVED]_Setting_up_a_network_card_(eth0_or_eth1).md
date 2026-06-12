---
title: "[SOLVED] Setting up a network card (eth0 or eth1)"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Stephen_A on 2008-05-04
I'm trying to get Ubuntu 8.04 online and to do this I need to know the private IP address of my modem, which is an NEC NTA-3110 ADSL.

The problem is that my network card is detecting a private IP address automatically (169.x.x.x) and this is not quite in the range that I would expect. Normally it is in the 192.168.x.x range. The reason it is doing this is because the router is not offering any private IP addresses.

Someone advised me to ask here for assistance in setting up my network card. If anyone could help here, I'd appreciate it. Thanks.

---

### Post by superprash2003 on 2008-05-05
you could try setting your network card manually as 192.168.1.10 and insert gateway as 192.168.1.1 or set network card manually as 192.168.0.10 and gateway as 192.168.0.1 ..cause usually by default modem ip's are either 192.168.1.1 or 192.168.0.1 ..to configure ip manually. go to system->administration->network ..choose your network card(eth0 mostly).. and then click on properties and then select static ip.. and enter ip

---

### Post by Stephen_A on 2008-05-05
That's exactly the kind of stuff I was hoping someone would post. Many thanks indeed.

---

### Post by Stephen_A on 2008-05-06
Hi Superhash, 
I hope you don't mind me imposing on you again. I tried both of your suggestions but it still can't get online. I use the Roaring Pengiun PPPoe connection software; that worked fine the last time I used it on Ubuntu. 

On 'Network Settings' I still haven't entered anything on the other tabs, namely, General, DNS and Hosts. Should I put anything under these settings?

Thanks in advance.

---

### Post by Iowan on 2008-05-06
```
ping 192.168.0.0 -b
``` *should* get a response from all machines on that network.

---

### Post by Stephen_A on 2008-05-06
This might be brining us close to a solution. I put in that code and got 'Network is unreachable.'

---

### Post by ComputerRick on 2008-05-06
> **Stephen_A said:**
> I use the Roaring Pengiun PPPoe connection software; that worked fine the last time I used it on Ubuntu. 

On 'Network Settings' I still haven't entered anything on the other tabs, namely, General, DNS and Hosts. Should I put anything under these settings?

I don't think you should be using the PPPoE software if you have a home network.  If you're other computers are getting DHCP, you most likely have a problem because of it.

Try setting the network settings, when you type ifconfig, it should show your ip configuration.

---

### Post by Stephen_A on 2008-05-06
No, we don't have a home network. Simply, two Windows boxes and a Dell with Ubuntu on it are plugged into the same modem. Before, everything ran fine using the PPPoE software. 

Here is the result of ifconfig -a

```

ifconfig -a:

eth0 Link encap:Ethernet HWaddr 00:0d:56:e9:f0:c3
inet6 addr: fe80::20d:56ff:fee9:f0c3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:122 errors:0 dropped:0 overruns:0 frame:0
TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:16933 (16.5 KB) TX bytes:10281 (10.0 KB)
Interrupt:7

eth0:avahi Link encap:Ethernet HWaddr 00:0d:56:e9:f0:c3
inet addr:169.254.11.4 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:7

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:50976 (49.7 KB) TX bytes:50976 (49.7 KB)
```

---

### Post by ComputerRick on 2008-05-07
> **Stephen_A said:**
> No, we don't have a home network. Simply, two Windows boxes and a Dell with Ubuntu on it are plugged into the same modem. Before, everything ran fine using the PPPoE software.

eth0:avahi Link encap:Ethernet HWaddr 00:0d:56:e9:f0:c3
inet addr:169.254.11.4 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1


Ok, I am trying to help you get running, but I need some more info.  There is very little regarding your NEC device available.  Also, We can't worry about what did work, because it doesn't now.  On your other computer that's plugged into the router (it's a loose assumption), can you post the IPCONFIG and do you have it configured as PPPoE?  If not, the Ubuntu shouldn't be either.
[COLOR="Blue"]You may want to try assigning the eth0 an ip that is one higher than the highest XP box, with the same DNS and Gateway addresses to see if you then have Internet.[/COLOR]

I do remember seeing this somewhere, just on a hunch, what network card are you using?

PS.  Two Windows boxes and an Ubuntu box all using the same Internet is a network.

---

### Post by Stephen_A on 2008-05-07
I've noted your definition of a 'network.' Thanks. Here is the ipconfig output from the XP box: 

C:\>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : IBM-75E205662A9
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2200BG Network Connection
        Physical Address. . . . . . . . . : 00-16-6F-36-84-3F

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
        Physical Address. . . . . . . . . : 00-16-41-12-BE-7F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.163.2
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter NETVIGATOR BROADBAND:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 218.103.224.29
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 218.103.224.29
        DNS Servers . . . . . . . . . . . : 218.102.32.208
                                            205.252.144.126
        NetBIOS over Tcpip. . . . . . . . : Disabled

Do I have it configured as PPPoE? Start>Connect to>Show All connections shows that the Netvigator account is configured to PPPoE. 
In the XP box, the network card is a Broadcom NetXtreme Gigabit Ethernet. 
I'll try what you suggest about putting the Ubuntu machine one higher than the XP. 
I hope all this is of some help. Thanks for your help so far.

---

### Post by ComputerRick on 2008-05-08
> **Stephen_A said:**
> Windows IP Configuration
Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
        Physical Address. . . . . . . . . : 00-16-41-12-BE-7F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        **Autoconfiguration IP Address. . . : 169.254.163.2**
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter NETVIGATOR BROADBAND:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 218.103.224.29
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 218.103.224.29
        DNS Servers . . . . . . . . . . . : 218.102.32.208
                                            205.252.144.126
        NetBIOS over Tcpip. . . . . . . . : Disabled


**[COLOR="Red"]Your original post:[/COLOR]**
> **Stephen_A said:**
> I'm trying to get Ubuntu 8.04 online and to do this I need to know the private IP address of my modem, which is an NEC NTA-3110 ADSL.

The problem is that my network card is detecting a private IP address automatically (169.x.x.x) and this is not quite in the range that I would expect. Normally it is in the 192.168.x.x range. The reason it is doing this is because the router is not offering any private IP addresses.

Well, I am going to be limited in what I can do for you, because I don't understand your network or the device and how it works with 4 ports yet requires PPPoE from the workstation unless it's in some form of bridging.

I quoted your original post because you were concerned about knowing your device's ip address.  It doesn't appear to have one.  Your Windows computer has the same address on the eth port as what you were concerned about in your first post, a 169.x.x.x address.  Only the PPP adapter has a functional address.  It appears that your dsl device does NOT have an address, and it's certainly not handing out dhcp.

You do need to leave your Ubuntu eth set to dhcp, it won't matter if you set it.  But you must use the Roaring Penguin software, based on your ipconfig from the XP box.  

Where are you?  Who is your DSL with?  Who is your ISP?  It would run better and easier (imho) if you could change the modem config to have an address with a private subnet behind.  No more PPPoE and you have a network that easier to plug into.  Then it will work more like you 'expected' in your first post, getting a 192.x.x.x range address.

** [COLOR="red"][SIZE="3"]I CANNOT ADVISE YOU TO CHANGE IT OR HOW[/SIZE][/COLOR], I am only offering suggestions for you to discuss with your ISP. I am not aware of their capabilities or configurations. [COLOR="Blue"]*Can you set your modem to PPPoE and get a dhcp ip, and will your modem support NAT to allow a private subnet on the internal side?? *[/COLOR]**

Can both Win boxes be online at the same time?

---

### Post by Stephen_A on 2008-05-12
Hi Everyone, 
Many thanks indeed for your help. The solution was to get a proper router, in this case a D-Link DIR-110 and hook up all the computers to it. The WAN port goes into the modem and everything runs perfectly. This is what I'd recommend to anyone else having the same trouble.

---

### Post by zebraman on 2008-09-06
i use this code but can't save it '/' is not accessable fully. i'm in ubuntu 8.

---

### Post by Stephen_A on 2008-09-06
As I said above, you can circumvent the problem by ensuring you have a properly configured router. After I did that, I found all you need to do is plug in a box, run Firefox and bingo, it's online. 
If you are setting up network I suggest you post a detailed description of your problem in the appropriate part of these forums, namely Networking or even in the beginners' thread.

---

