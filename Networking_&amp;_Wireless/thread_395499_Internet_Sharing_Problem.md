---
title: "Internet Sharing Problem"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by thorosius on 2007-03-28
I've searched the forum but most of posts i found involve wireless connections, routers or switches and i am not a networking expert so I am confused. Anyway I've tried some of them but no success. Please Help! 

Here is my situation: I want to access the internet with ubuntu on my laptop through WinXP Desktop which is connected to the internet.


[CENTER]Internet
/\
||
||
<DesktopPC Ethernet IP:192.168.1.1 Prefered DNS Server:192.168.1.1>
OS:WinXP updated upto December 2006
Internet connection sharing enabled
This PC successfully connects to the internet.
||
Cross cable
||
\/
<Laptop EthernetIP:192.168.1.2 Prefered DNS Server:192.168.1.1 Gateway:192.168.1.1>
OS: Ubuntu Edgy[/CENTER]


Still I can't reach any websites, although I am able to ping both machines.

---

### Post by tatster on 2007-03-28
Hi,

Just a thought and it may be wrong but you might want to check that the ICS is turned on correctly as my understanding was that when ICS was turned on that it changed the PCs IP to 192.168.0.1  and then it ran a mini DHCP server which handed out 192.168.0.x addresses to clients.

Please can you paste the results from an ipconfig /all on the windows box.


Tat.

---

### Post by thorosius on 2007-03-28
I think its correctly turned on. Command output is given below.


C:\Documents and Settings\Fahd>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : s-3887580aa2b74
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : 3Com EtherLink XL 10/100 PCI For Complete PC Management NIC (3C905C-TX)
        Physical Address. . . . . . . . . : 00-01-02-9A-EB-B8

---

### Post by tatster on 2007-03-28
Hi Fahd,

Please can you redo that command with the crossover and your Ubuntu machine connected.
Unfortunately you don't get to see IP settings when the NIC is disconnected.  :-)

Tat.

---

### Post by thorosius on 2007-03-29
Windows IP Configuration

        Host Name . . . . . . . . . . . . : s-3887580aa2b74
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com EtherLink XL 10/100 PCI For Complete PC Management NIC (3C905C-TX)
        Physical Address. . . . . . . . . : 00-01-02-9A-EB-B8
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 192.168.1.1

---

### Post by thorosius on 2007-03-29
There is something called "Network Proxy" in preferences doesn't this need to be configured?

---

### Post by tatster on 2007-03-29
Hi,

I'm not 100% sure but it might be worth doing a bit of research about ICS on the Windows side of things because I was pretty sure that when you turn ICS on it set's the PC's IP to 192.168.0.1

Tat.

---

### Post by thorosius on 2007-03-29
OK I'll confirm that.

---

### Post by thorosius on 2007-03-29
IP does not change I'v run the command while internet was connected and Connection was shared.
 
C:\Documents and Settings\Fahd>ipconfig /all
Windows IP Configuration
        Host Name . . . . . . . . . . . . : s-3887580aa2b74
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com EtherLink XL 10/100 PCI For Complete PC Management NIC (3C905C-TX)
        Physical Address. . . . . . . . . : 00-01-02-9A-EB-B8
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 192.168.1.1
PPP adapter WoL:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 202.61.62.70
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 202.61.62.70
        DNS Servers . . . . . . . . . . . : 202.61.62.2
                                            202.61.56.66
        NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by koenn on 2007-03-29
> **thorosius said:**
> 
Still I can't reach any websites, although I am able to ping both machines.
What kind of error do you get when trying to access websites ? 
I suspect those will be time-outs or "can't find server" errors. 
Try setting  202.61.62.2 as DNS server on the Ubuntu Laptop (in stead of 192.168.1.1 )

---

### Post by thorosius on 2007-03-30
Yes those are the errors and i'v tried setting the DNS server ti 202.61.62.2 but no success. shouldn't firefox be configured in any way?

---

### Post by koenn on 2007-03-30
> **thorosius said:**
> Yes those are the errors and i'v tried setting the DNS server ti 202.61.62.2 but no success. shouldn't firefox be configured in any way?
First let's see if your laptop has internet access through the Windows ICS. can it ping google or ubuntuforums ? 
```
ping -c 5 64.233.183.103
ping -c 5 82.211.81.186

```

---

### Post by Austin_KW on 2007-03-30
Do you have a windows firewall running, anything in the firewall logs. 
I also thought that windows used dhcp to assign private addresses to the sharer, did you allocate static addresses? DHCP would also take care of the wrong DNS server address

---

### Post by thorosius on 2007-03-30
koenn >> I'v tried to ping google, ping waits for about 5-6 seconds then says "not reachable"
 
Austin_KW >> I'll look at the logs I have ZoneAlarm. Yes I have allocated static addresses to both cards.

---

### Post by koenn on 2007-03-30
> **thorosius said:**
> koenn >> I'v tried to ping google, ping waits for about 5-6 seconds then says "not reachable".
hm, let's see if we can narrow it down.

Assuming the windows machine can access the internet, and that it's WAN interface still has 202.61.62.70, 
can you ping, from the laptop,  the following and post the result

```

ping -c 4 127.0.0.1
ping -c 4 192.168.1.2
ping -c 4 192.168.1.1
ping -c 4 202.61.62.70

```

You may want to try this both with and without ZoneAlarm running, to see if it interferes.

---

### Post by thorosius on 2007-03-31
I read on the internet about setting the host IP to 192.168.0.1. So I'v set Windows machine's IP to 192.168.0.1 and Laptop to 192.168.0.2. If this is alright I'll keep it this way. ZoneAlarm was actvie during all this process.
Command outputs are given below:
 
[SIZE=2]fahd@fahd-laptop:~$ ping -c 4 127.0.0.1[/SIZE]
[SIZE=2]PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.[/SIZE]
[SIZE=2]64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.044 ms[/SIZE]
[SIZE=2]64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.035 ms[/SIZE]
[SIZE=2]64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.035 ms[/SIZE]
[SIZE=2]64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.036 ms[/SIZE]
[SIZE=2]--- 127.0.0.1 ping statistics ---[/SIZE]
[SIZE=2]4 packets transmitted, 4 received, 0% packet loss, time 2997ms[/SIZE]
[SIZE=2]rtt min/avg/max/mdev = 0.035/0.037/0.044/0.007 ms[/SIZE]
 
 
[SIZE=2]fahd@fahd-laptop:~$ ping -c 4 192.168.0.2[/SIZE]
[SIZE=2]PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.[/SIZE]
[SIZE=2]64 bytes from 192.168.0.2: icmp_seq=1 ttl=64 time=0.047 ms[/SIZE]
[SIZE=2]64 bytes from 192.168.0.2: icmp_seq=2 ttl=64 time=0.037 ms[/SIZE]
[SIZE=2]64 bytes from 192.168.0.2: icmp_seq=3 ttl=64 time=0.032 ms[/SIZE]
[SIZE=2]64 bytes from 192.168.0.2: icmp_seq=4 ttl=64 time=0.048 ms[/SIZE]
[SIZE=2]--- 192.168.0.2 ping statistics ---[/SIZE]
[SIZE=2]4 packets transmitted, 4 received, 0% packet loss, time 2997ms[/SIZE]
[SIZE=2]rtt min/avg/max/mdev = 0.032/0.041/0.048/0.006 ms[/SIZE]
 
 
[SIZE=2][SIZE=2]fahd@fahd-laptop:~$ ping -c 4 192.168.0.1[/SIZE]
[SIZE=2]PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.[/SIZE]
[SIZE=2]64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=0.322 ms[/SIZE]
[SIZE=2]64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=0.259 ms[/SIZE]
[SIZE=2]64 bytes from 192.168.0.1: icmp_seq=3 ttl=128 time=0.257 ms[/SIZE]
[SIZE=2]64 bytes from 192.168.0.1: icmp_seq=4 ttl=128 time=0.256 ms[/SIZE]
[SIZE=2]--- 192.168.0.1 ping statistics ---[/SIZE]
[SIZE=2]4 packets transmitted, 4 received, 0% packet loss, time 2998ms[/SIZE]
[SIZE=2]rtt min/avg/max/mdev = 0.256/0.273/0.322/0.032 ms[/SIZE]
[/SIZE]
When I reconnect after disconnecting from my ISP I get random new Gateway Address so this time it was 202.61,62,101WOW it was pinged successfully ???
[SIZE=2]fahd@fahd-laptop:~$ ping -c 4 202.61.62.101[/SIZE]
[SIZE=2]PING 202.61.62.101 (202.61.62.101) 56(84) bytes of data.[/SIZE]
[SIZE=2]64 bytes from 202.61.62.101: icmp_seq=1 ttl=128 time=0.677 ms[/SIZE]
[SIZE=2]64 bytes from 202.61.62.101: icmp_seq=2 ttl=128 time=0.259 ms[/SIZE]
[SIZE=2]64 bytes from 202.61.62.101: icmp_seq=3 ttl=128 time=0.247 ms[/SIZE]
[SIZE=2]64 bytes from 202.61.62.101: icmp_seq=4 ttl=128 time=0.250 ms[/SIZE]
[SIZE=2]--- 202.61.62.101 ping statistics ---[/SIZE]
[SIZE=2]4 packets transmitted, 4 received, 0% packet loss, time 2998ms[/SIZE]
[SIZE=2]rtt min/avg/max/mdev = 0.247/0.358/0.677/0.184 ms[/SIZE]

---

### Post by thorosius on 2007-03-31
I think ISP blocks pings to hosts other than their own. I think the replay is from the DNS server of the ISP.
 
C:\Documents and Settings\Fahd>ping 64.233.183.103
Pinging 64.233.183.103 with 32 bytes of data:
Request timed out.
Reply from 202.61.62.3: Destination net unreachable.
Request timed out.
Reply from 202.61.62.3: Destination net unreachable.
Ping statistics for 64.233.183.103:
    Packets: Sent = 4, Received = 2, Lost = 2 (50% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

---

### Post by Austin_KW on 2007-03-31
So except for the blocked pings, is it working?

---

### Post by koenn on 2007-03-31
> **thorosius said:**
> I read on the internet about setting the host IP to 192.168.0.1. So I'v set Windows machine's IP to 192.168.0.1 and Laptop to 192.168.0.2. If this is alright I'll keep it this way

no problem

> 
When I reconnect after disconnecting from my ISP I get random new Gateway Address so this time it was 202.61,62,101WOW it was pinged successfully ???
This means your laptop at least has access to the WAN interface of the windows machine, on another network. So it should have internet access as well.
So, is everything working now ? 
if not : since pings are blocked, you could try if the laptop has internet access by typing ip addresses in your browser's address box. (eg [http://64.233.183.103](http://64.233.183.103)   and [http://82.211.81.186](http://82.211.81.186) )

---

### Post by thorosius on 2007-04-01
koenn >> I'v tried the above address in the firefox after about a minute and then says:
 
The connection has timed out.
The server at <address> is taking too long to respond.
 
I have a question, is there no need for specifying a proxy in "Network Setting" configuration in Firefox?
 
One other thing, as I had mentioned above that pings were being blocked the results I posted in that thread were from WindowsXP (Pings were even blocked from WinXP machine). So I'v changed my ISP. Now I can atleast ping google and ubuntuforums from the XP machine.
 
Austin_KW >> No its not working I cannot access any Website from Firefox and I cannot ping any of them (Even after changing the ISP)

---

### Post by thorosius on 2007-04-01
I'v tried a little experiment. There is a free proxy server "AnalogX proxy" I used this on the WindowsXP machine it opens up a port for http by placing this port in the firefox network configurations I can open websites now in Ubuntu. But I still dont have internet in the terminal.

---

### Post by koenn on 2007-04-01
The ICS on the Windows machine is not working.
Your ubuntu laptop looks OK and has network access to the Windows PC, and the Windows PC has internet access, so the part missing is the windows PC doing routing+NAT (= ICS)

When you use AnalogX proxy, you only need network between the laptop and the windows pc - the pc does the web access on behalf of the laptop, that's the essence of 'proxy'

Do you recall what steps you took to activate ICS on the windows PC ?

---

### Post by thorosius on 2007-04-02
If I recall correctly I tried these two procedures:
 
1. I had a manual internet connection already present. Properties>Advanced>Allow other network users to connect through this computer's Internet connection.
 
When it didn't work I used this method.
2. With "Network Wizard" Choosing an option "This Computer Connects directly to the internet. The other computers on my network connect to the internet through this computer". Wizard also changed the static IP of the WinXP machine that I set to 192.168.0.1 automatically.

---

### Post by koenn on 2007-04-02
sounds reasonable. 
not really sure waht to do next, but I still think it's the windows box that is giving trouble. 
Could you post the routing table of that windows PC : at a command prompt, do
```
 route PRINT
```

Then, let's see how far the Ubuntu laptop gets when he's trying to get on the internet  :
```
traceroute 82.211.81.186
```

The only thing bugging me is that that PC has the same address for its own IP address and its default gateway. Feels wrong, even for a ppp connection. 
```
IP Address. . . . . . . . . . . . : 202.61.62.70
Subnet Mask . . . . . . . . . . . : 255.255.255.255
Default Gateway . . . . . . . . . : 202.61.62.70
```

Any ideas about that ?

---

### Post by Austin_KW on 2007-04-02
and the windows PC output of (complete output not truncated)
```
ipconfig/all
```

and on the ubuntu PC
```
ifconfig -a
cat /etc/network/interfaces
```
I want to confirm the the ubuntu PC  is using DHCP to get it's address, this may be the trigger for windoze to start to configure its NAT tables.

---

### Post by thorosius on 2007-04-02
koenn >> I agree seems that the WinXP machine is the problem.
 
Output for the route PRINT Command. Text is not formated correctly:
 
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.
C:\Documents and Settings\Fahd>route PRINT
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 01 02 9a eb b8 ...... 3Com EtherLink XL 10/100 PCI For Complete PC Man
agement NIC (3C905C-TX) - Packet Scheduler Miniport
0x20004 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination Netmask Gateway Interface Metric
0.0.0.0 0.0.0.0 61.5.149.174 192.168.0.1 21
0.0.0.0 0.0.0.0 61.5.149.221 61.5.149.221 1
61.5.148.10 255.255.255.255 61.5.149.221 61.5.149.221 1
61.5.149.221 255.255.255.255 127.0.0.1 127.0.0.1 50
61.255.255.255 255.255.255.255 61.5.149.221 61.5.149.221 50
127.0.0.0 255.0.0.0 127.0.0.1 127.0.0.1 1
192.168.0.0 255.255.255.0 192.168.0.1 192.168.0.1 20
192.168.0.1 255.255.255.255 127.0.0.1 127.0.0.1 20
192.168.0.255 255.255.255.255 192.168.0.1 192.168.0.1 20
224.0.0.0 240.0.0.0 192.168.0.1 192.168.0.1 20
224.0.0.0 240.0.0.0 61.5.149.221 61.5.149.221 1
255.255.255.255 255.255.255.255 61.5.149.221 61.5.149.221 1
255.255.255.255 255.255.255.255 192.168.0.1 192.168.0.1 1
Default Gateway: 61.5.149.221
===========================================================================
Persistent Routes:
None
 
[SIZE=2]Output for traceroute 82.211.81.186:[/SIZE]
 
[SIZE=2][SIZE=2]fahd@fahd-laptop:~$ traceroute 82.211.81.186[/SIZE]
[SIZE=2]traceroute to 82.211.81.186 (82.211.81.186), 30 hops max, 40 byte packets[/SIZE]
[SIZE=2]1 s-3887580aa2b74.mshome.net (192.168.0.1) 0.305 ms 0.186 ms 0.157 ms[/SIZE]
[SIZE=2]2 * * *[/SIZE]
[SIZE=2]3 * * *[/SIZE]
[SIZE=2]4 * * *[/SIZE]
[SIZE=2]5 * * *[/SIZE]
[SIZE=2]6 * * *[/SIZE]
[SIZE=2]7 * * *[/SIZE]
[SIZE=2]8 * * *[/SIZE]
[SIZE=2]9 * * *[/SIZE]
[SIZE=2]10 * * *[/SIZE]
[SIZE=2]11 * * *[/SIZE]
 
[SIZE=2]seems like Laptop can't reach any further than the WinXP machine.[/SIZE]
[SIZE=2]And I have absolutely no idea why the Gateway and IP address are same.[/SIZE]
 
[SIZE=2]Austin_KW >> Output generated by ipconfig /all:[/SIZE]
 
[SIZE=2][SIZE=2]C:\Documents and Settings\Fahd>ipconfig /all[/SIZE]
[SIZE=2]Windows IP Configuration[/SIZE]
[SIZE=2]Host Name . . . . . . . . . . . . : s-3887580aa2b74[/SIZE]
[SIZE=2]Primary Dns Suffix . . . . . . . :[/SIZE]
[SIZE=2]Node Type . . . . . . . . . . . . : Unknown[/SIZE]
[SIZE=2]IP Routing Enabled. . . . . . . . : Yes[/SIZE]
[SIZE=2]WINS Proxy Enabled. . . . . . . . : No[/SIZE]
[SIZE=2]Ethernet adapter Local Area Connection:[/SIZE]
[SIZE=2]Connection-specific DNS Suffix . :[/SIZE]
[SIZE=2]Description . . . . . . . . . . . : 3Com EtherLink XL 10/100 PCI For Complete PC Management NIC (3C905C-TX)[/SIZE]
[SIZE=2]Physical Address. . . . . . . . . : 00-01-02-9A-EB-B8[/SIZE]
[SIZE=2]Dhcp Enabled. . . . . . . . . . . : No[/SIZE]
[SIZE=2]IP Address. . . . . . . . . . . . : 192.168.0.1[/SIZE]
[SIZE=2]Subnet Mask . . . . . . . . . . . : 255.255.255.0[/SIZE]
[SIZE=2]Default Gateway . . . . . . . . . : 61.5.149.174[/SIZE]
[SIZE=2]DNS Servers . . . . . . . . . . . : 192.168.0.1[/SIZE]
[SIZE=2]PPP adapter CNet:[/SIZE]
[SIZE=2]Connection-specific DNS Suffix . :[/SIZE]
[SIZE=2]Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface[/SIZE]
[SIZE=2]Physical Address. . . . . . . . . : 00-53-45-00-00-00[/SIZE]
[SIZE=2]Dhcp Enabled. . . . . . . . . . . : No[/SIZE]
[SIZE=2]IP Address. . . . . . . . . . . . : 61.5.149.221[/SIZE]
[SIZE=2]Subnet Mask . . . . . . . . . . . : 255.255.255.255[/SIZE]
[SIZE=2]Default Gateway . . . . . . . . . : 61.5.149.221[/SIZE]
[SIZE=2]DNS Servers . . . . . . . . . . . : 202.163.96.3[/SIZE]
[SIZE=2]202.163.96.4[/SIZE]
[SIZE=2]NetBIOS over Tcpip. . . . . . . . : Disabled[/SIZE]
 
[SIZE=2]The sencond command didn't work. I think it has a syntax problem anyway I didn't know the command so couldn't fix it. Can you please look it at again?[/SIZE]
[/SIZE][/SIZE]

---

### Post by Austin_KW on 2007-04-02
>  DNS Servers . . . . . . . . . . . : 192.168.0.1[\quote]
Where did this come from? Are you running a dns server on the windows PC? I am sure I have read somewhere that an ICS pc cannot be a server (dns,dhcp...)


[quote]Default Gateway . . . . . . . . . : 61.5.149.174
I don't see where this came from and it appears to be a routing loop
> 0.0.0.0 0.0.0.0 61.5.149.174 192.168.0.1 21 maybe I am misinterpreting
The second set of commands were to be run on the linux pc, I just wanted to verify that the liux PC was getting a correct address/gateway/nameserver via dhcp

---

### Post by thorosius on 2007-04-03
Austin_KW >> I'll try without the DNS address. but I used this for two connecting my two machines (Laptop & Desktop). Please confirm: Should I remove it?
 
The Default Gateway is wrong because I entered this address for the previous connection I made to the ISP and I was trying this method out. Please confirm: Is Gateway specification unneccessary? 
 
I have no experiance with routing. Please suggest a solution for this routing problem so I can try it.

---

### Post by koenn on 2007-04-03
This doesn't make sense : ```

NetworkDestination 	Netmask 	Gateway 	Interface 	Metric
0.0.0.0 		0.0.0.0 	61.5.149.174 	192.168.0.1 	21
0.0.0.0 		0.0.0.0 	61.5.149.221 	61.5.149.221 	1

```
It gives you 2 default routes (while there should be only one), and the first one is nonsense, it says to send traffic out via router 61.5.149.174 through interface 192.168.0.1. Plus the address 61.5.149.174 is nowhere to be found on the netwok.

Obviously this route was created by Windows because you put
```
IP Address. . . . . . . . . . . . : 192.168.0.1
Subnet Mask . . . . . . . . . . . : 255.255.255.0
**Default Gateway . . . . . . . . . : 61.5.149.174**
```
in the network config of tha LAN interface. This wasn't there before, it's a good thing Austin_KW asked for the output of ipconfig /ALL again. 
You can't just put numbers there. You have less than 1/ 4,000,000,000 chance to guess the correct address :) 
I think you should leave the default gw for this interface blank.
Reboot, check 'route PRINT' again to see if that line has gone, then do that traceroute again. The rest of the routing table looks OK so we'll see what we have so far.

We may have to work on the dns servers as well, but that can wait, they shouldn't interfere with network config as long as you test with addresses, not host names. 
Unless the fact in itself that you have a dns server running on the windows box interferes with the NAT / ICS. Win XP does not include a DNS server so probably there is no DNS at 192.168.0.1

---

### Post by thorosius on 2007-04-03
koenn >> I didnot put that address on random. As I had mentioned before everytime I reconnect to my ISP. So this was the Default Gateway for that session but I forgot to remove it when I connected to the ISP again. I'v removed it now. Here is the table:
 
```
 
C:\Documents and Settings\Fahd>route PRINT
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 01 02 9a eb b8 ...... 3Com EtherLink XL 10/100 PCI For Complete PC Man
agement NIC (3C905C-TX) - Packet Scheduler Miniport
0x40004 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     61.5.149.170    61.5.149.170       1
      61.5.148.10  255.255.255.255     61.5.149.170    61.5.149.170       1
     61.5.149.170  255.255.255.255        127.0.0.1       127.0.0.1       50
   61.255.255.255  255.255.255.255     61.5.149.170    61.5.149.170       50
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
        224.0.0.0        240.0.0.0     61.5.149.170    61.5.149.170       1
  255.255.255.255  255.255.255.255     61.5.149.170    61.5.149.170       1
  255.255.255.255  255.255.255.255     61.5.149.170               2       1
Default Gateway:      61.5.149.170
===========================================================================
Persistent Routes:
  None

```
 
But again traceroute didnot reach the internet:
```
fahd@fahd-laptop:~$ sudo traceroute 82.211.81.186
traceroute to 82.211.81.186 (82.211.81.186), 30 hops max, 40 byte packets
 1  s-3887580aa2b74.mshome.net (192.168.0.1)  0.405 ms  0.251 ms  0.215 ms
 2  * * *
 3  * * *
 4  * *

```
I would also like to mention that I still am able to ping the ppp's default gateway. This time it was:
```
Default Gateway . . . . . . . . . : 61.5.149.221
```
 
How can I confirm that there is no DNS present on WinXP?

---

### Post by Austin_KW on 2007-04-03
> How can I confirm that there is no DNS present on WinXP?

to query any dns from a linux pc 'dig @ipAddress name' eg dig @192.168.0.1 google.com

> I would also like to mention that I still am able to ping the ppp's default gateway. This time it was:
I think this is a point-point tunnel, encapsulated data sent to the  local ip address address just pops out at the remote end. So you are probably just pinging the local end (windows PC).

Something is wrong here, this should not be this difficult; from what I remember windows ICS is  zeroconfig, you turn it on with the wizard and enable dhcp at the client end.
You should not manually configure any ip address/mask, or gateway or dns on the interface. ICS will automatically configure the static ip address on the ethernet adapter. 
Remove all configuration from the ethernet network adapter and rerun the ICS wizard. Then do not change the configuration. Then enable dhcp on the client PC

---

### Post by koenn on 2007-04-03
I agree with Austin_KW - this usually "Just Works" and I can't find anything strange
(other than not knowing what address is at the other side of the ppp link and thus the default gateway set as the machines own WAN interface)

restarting from scratch might be a good idea here.

---

### Post by thorosius on 2007-04-03
I removed connection sharing and static IPs from the internet and ethernet configuration and restarted the network wizard. Wizard has not set any DNS server IP for LAN:
 
```
 
C:\Documents and Settings\Fahd>ipconfig /all
Windows IP Configuration
        Host Name . . . . . . . . . . . . : DESKTOP
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No
Ethernet adapter Local Area Connection:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com EtherLink XL 10/100 PCI For Complete PC Management NIC (3C905C-TX)
        Physical Address. . . . . . . . . : 00-01-02-9A-EB-B8
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
PPP adapter CNet:
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 61.5.149.61
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 61.5.149.61
        DNS Servers . . . . . . . . . . . : 202.163.96.3
                                            202.163.96.4
        NetBIOS over Tcpip. . . . . . . . : Disabled

```
 
Still can't "traceroute" futher than WinXP. Although I am able to "ping" both PCs.
 
Now how do I reset settings for Ubuntu? Its already on DHCP. And one other thing, how can I reset Iptables there might be a problem with it.
 
Should the Wizard be run when Internet Connection is active or when its not?

---

### Post by applemacmad on 2007-04-03
I have the exact same problem here.
I have a powerbook connected to the internet wirelessly, with a ethernet cable going into the back of my Ubuntu box. Internet sharing is set up on the Mac, yet I get nothing on the ubuntu box.
I also have XP and Macintosh installed on the computer abd they work fine with exactly the same settings.

I've tried everything suggested in this thread with no luck.
I might try downloading Feisty, to see if I have any luck with that.... :confused:

---

### Post by koenn on 2007-04-04
> **thorosius said:**
>  
Now how do I reset settings for Ubuntu? Its already on DHCP. And one other thing, how can I reset Iptables there might be a problem with it.
 
If the ubuntu is already on dhcp it should have an Ip address like 192.168.0.n, and 192.168.0.1 for default gateway. If so, there's nothing to (re-)set. otherwise, just run dhclient. 

Iptables ? You're running iptables on the ubuntu ? 
why do you think there might be a problem with it ? 
you can remove iptables rules with
```
sudo iptables --flush
``` but that still leaves to default policies intact, i think. 
Post the output of  ```
 sudo iptables --list
```



> Should the Wizard be run when Internet Connection is active or when its not?What wizzard is that and where do you want to run it ?

---

### Post by thorosius on 2007-04-04
Network Setup Wizard in WindowsXP.

---

### Post by koenn on 2007-04-04
I don't get it. You're XP is set up : the network is configured, the ICS is setup - why do  you think you need to run that wizzard ?

---

### Post by Robynsveil on 2007-04-05
> **Austin_KW said:**
> Do you have a windows firewall running, anything in the firewall logs. 
I also thought that windows used dhcp to assign private addresses to the sharer, did you allocate static addresses? DHCP would also take care of the wrong DNS server address
I've got Windows 2000 Pro as my ICS box at this point. It does a mini-dhcp - just enough, no NAT or anything fancy, you need Window$$$ $$$erver for *that* - and it is not configurable at all, issues out dynamic IP addresses when the workstations boot up. Tried static IP addresses, but could not connect the machines that had static addresses, as the WIn2K simply wouldn't recognize them. A bit pov, that. :mad:

---

### Post by thorosius on 2007-04-09
I apologise for my absence my network cable has broken I'll repair it in one or two days. 
 
koenn >> When I reset all the settings I ran the network setup wizard when my internet connection was disconnected. So I wanted to confirm if this was alright (Running wizard when no internet connection is present).
 
I'll post the command output soon.

---

### Post by thorosius on 2007-04-12
I again apologise for the delay.
 
So here is the news ... 
 
A problem occured with my laptop's Ubuntu installation and I can't install it again. So I am now using laptop to connect to the internet and the desktop PC's Ubuntu installation to share the connection. The only difference now is that the IP configuration is reversed between the two machines. I know its becoming confusing but I hope you understand it. And I think it is easy if we mention Ubuntu machine and WinXP machine instead of Laptop and Desktop .... :) Still if you have any confusion ask me about it. I can ping both machines. 
 
koenn >> I thought something might be wrong with iptables cause its a firewall and it may be blocking the connection. I was trying to learn how to configure it. The flush, dhclient and list command outputs are given below.
 
Anyway here is the output for the commands:
 
```
 
fahd@fahd-desktop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5962
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/00:01:02:9a:eb:b8
Sending on LPF/eth0/00:01:02:9a:eb:b8
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 
 
fahd@fahd-desktop:~$ sudo iptables --flush
fahd@fahd-desktop:~$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target prot opt source destination 
Chain FORWARD (policy ACCEPT)
target prot opt source destination 
Chain OUTPUT (policy ACCEPT)
target prot opt source destination 

```

---

### Post by koenn on 2007-04-12
you're not getting an IP address from dhcp. If ICS is supposed to offer a dhcp service, at least that is not working. 
(or you could try again AFTER you flush the iptables - in case the dhcp communication was blocked)

---

### Post by thorosius on 2007-04-13
Now its working.
 
```
 
fahd@fahd-desktop:~$ sudo dhclient
Password:
There is already a pid file /var/run/dhclient.pid with pid 5390
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/eth0/00:01:02:9a:eb:b8
Sending on LPF/eth0/00:01:02:9a:eb:b8
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.203 -- renewal in 272 seconds.

```

---

### Post by thorosius on 2007-04-14
I can feel something is missing but I cant put my finger on  it.
 
Ameteure Question: DHCP can automatically set a computer's IP but is it able to setup the computer to use the internet connection on another machine in the network? At the university, were I studied, has thousands of computer and if for example I would try to connect my laptop to ethernet of the university and use internet I would have to setup a proxy in internet explorer. Why do you think in this case proxy setup is not important?

---

### Post by koenn on 2007-04-14
> I can feel something is missing but I cant put my finger on it.
Yeah, that would be easier. You'd just have to lift your finger and see what's under it  :)

> DHCP can automatically set a computer's IP but is it able to setup the computer to use the internet connection on another machine in the network? No. Dhcp provides network settings : ip address, router address, dns server address, etc. 

> At the university, were I studied, has thousands of computer and if for example I would try to connect my laptop to ethernet of the university and use internet I would have to setup a proxy in internet explorer. Why do you think in this case proxy setup is not important?
[http://ubuntuforums.org/showpost.php?p=2387283&postcount=22](http://ubuntuforums.org/showpost.php?p=2387283&postcount=22)
these proxies are usefull to 
- cache content (saves bandwith, can help to speed up browsing)
- implement security : in stead of the whole university accessing the internet directly, only the proxy does. It's easier to secure 1 proxy than 1000 pc's all over the place. 
- allow or deny access (for certain users, to certain websites, etc)

You could use a proxy as a workaround for your ICS problem as you did with the AnalogX, though, but it will only work for protocols that can be proxied (most often http).

---

### Post by thorosius on 2007-04-14
So is it possible that pings to google or ubuntu forums can be done successfully if I use a proxy?

---

### Post by koenn on 2007-04-14
I don't think so. ping uses ICMP protocol and you can not proxy that, AFAIK. 

You can ping the proxy server, but the proxy server will not relay that ping to, say, google.com. To ping google.com, you need a direct connection to the internet.

---

### Post by thorosius on 2007-04-15
I dont need to browse the internet I already have windows for that. There should be a solution for my problem please help!

---

### Post by thorosius on 2007-04-17
I suppose I dont have it written in my fate to use internet in ubuntu!
 
Please help!

---

### Post by thorosius on 2007-04-21
Any other suggestions, anyone ????

---

### Post by thorosius on 2007-04-21
I solved the problem... well I didn't solve it [steve.horsley]("http://ubuntuforums.org/member.php?u=26326") did. I will post the solution here too but first I would like to thank all the people that have helped me in this thread, especially keonn. I'll paste exactly what steve.horsley suggested.
 
>  Can you ping the XP machine? If so, you are probably missing two things - an IP route, and the addresses of hte DNS servers.
 
The IP route can be added with this command:
**sudo route add default gw 192.168..0.1**
 
The IP addresses of the DNS servers you will have to look at the XP box IP configuration and read the DNS servers addresses from there. Add these to the file /etc/resolv.conf, one address per line like this:
**nameserver 1.2.3.4**
**nameserver 6.6.6.6**


---

### Post by koenn on 2007-04-21
The DNS make sense, but that was a minor problem once the network is set up right. It's w eird that you'd have to specify a route :
> **koenn said:**
> If the ubuntu is already on dhcp it should have an Ip address like 192.168.0.n, **and 192.168.0.1 for default gateway**. If so, there's nothing to (re-)set. otherwise, just run dhclient. 

I suppose we should have explicitely checked that .

Glad you got it working, though.

---

### Post by thorosius on 2007-04-23
Thank You !

---

