---
title: "Setting up RDP/SSH/FTP"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by Pap3r on 2008-04-14
Hey all,
Recently I've been attempting to set-up my computer for remote access. It is an Ubuntu 7.10 machine running Firestarter (I have a few side questions about Firestarter, too, but I'll ask them in another post on this thread soon).

I started off simply, I went to my router's ip (192.168.1.1) and changed the rules for my computer to allow RDP, VNC, FTP, and SSH connection types. I assume by "Adding" the rules, I was allowing connections of this type. I enabled RDP on Ubuntu and went to another computer in my house to try it out. It didn't connect. I changed my firewall to allow my other home IP to connect and tried again. But the RDP didn't connect again. I've been unable to connect with RDP to my Windows comp, or from my Windows comp to my Ubuntu comp so far. Neither with a computer outside my network, for instance my school.

My next step in the configuring process was to install the Daemons/Servers to allow FTP and SSH connections to be established/

```
sudo apt-get install sshd && sudo apt-get install ftpd
```

worked well enough, and I configured both of the new daemons. I went to my windows machine and attempted my first ssh. Success! PuTTY connected right to my Ubuntu machine and I was able to screw around for a bit. I went to a friends and attempted to connect using my external IP, but only received connection refused errors, or network unreachable.  FTP From my Windows comp to my Ubuntu box did NOT work.  I also installed muddleftpd, and testes that out.  Nothing.

Point being, internal IP connections work, besides the RDP and FTP. External connections on the other hand, through IP or DynDNS, are not connecting. I'm in school at the moment, but when I get home I will be able to check FireStarter to find out if all my connections were simply blocked. In that case I assume I would have to either allow a single IP which belongs to a school computer and only connect through it, or disable my firewall when I feel it would be necessary for me to connect to my machine remotely (every other day in school), which is obviously a security threat.

I'm really new at these remote connections, so I may just be missing some simple things. How come I can't connect to my machine remotely? Everything should be configured correctly, and the servers set up. Any ideas?

EDIT

I had a strange success but a moment ago, connecting to my computer through telnet. I typed
```


Microsoft Telnet> o XXXXXXXX
Connecting To XXXXXXXX
BusyBox on (none) login: admin
Password:


BusyBox v0.61.pre (2007.03.09-22:59+0000) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

#

```
I could navigate a small amount, do a few things. I was absolutely astounded telnet worked. It wasn't even my login name and password, just Admin/Password.

Here are the Firestarter questions.  Many times I will see the Red lightningbolt type thing, and I'll click it to see what was up.  Most of the time I'll see some thing trying to make a connection, with the service as VNC.  I'm very familiar with windows processes and firewalls etc, but seeing services in Ubuntu trying to access me throws me off guard, I'm never sure what to think.  Anyway, two days ago I got a red arrow and checked it out.  It was written in red lettering, and the service was HTTPS, from an IP I forget.  What is that (not the service, I know what HTTPS is)?  I've also gotten some random IP's with FTP set as their service.  These are not MY FTP IP's as stated above

---

### Post by SpaceTeddy on 2008-04-15
This is lots of things at once... 
i'll try to file through them, so bear with me if i might ask questions that you have already answered.

first off, how is your network connected to your internet ? is your ubuntu server directly connected to the internet, or is there a router inbetween that every computer on the network connects to ? can you possibly draw me a picture of it ?

second - what happens if you turn firestarter off. can you connect the ftp and rdp then ? (this means setting your INPUT&OUTPUT chain to ACCEPT). In other words, do you have a configuration problem with the servers of is this a firewall related problem

third - When you telneted into the machine, from where did you come ? where you in your internal network, or did you do this from the internet ? 

Ok... also, i would like you to paste a few output here. run these on your ubuntu and simply paste the output

```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
sudo netstat -lnp --inet
sudo lsmod |grep ip_
ifconfig
```

the first two will print out your firewall configuration, the third will show which servers you have running on your system, the fourth will show if you have an addintional firewall modules loaded (for ftp connecton tracking). The last one gives out the configuration of your network interfaces.

hope we can figure this :)

---

### Post by Pap3r on 2008-04-15
I'm not at home right now, so I can't give you the output from those commands.  However, I can answer some things, I'll get to the rest later.  Just an FYI, I appreciate the explanation of the commands, what they do.  I see many people siply giving out answers, and people never learn exactly why they typed that code :)

Anyway, I have my Ubuntu box connected to a router, which is connected to the internet.  I was under the impression, as stated before, that I have set the rules on my router to allow connections of these types.

If I'm not mistaken, FireStarter is turned out at the moment, and I was just able to FTP to my computer.  Here's the output: 
```
C:\>ftp
ftp> open pap3r.dynalias.com
Connected to pap3r.dynalias.com.
220 muddleftpd (1.3.13) server ready. Enter Username.
User (pap3r.dynalias.com:(none)): joe
331 Welcome 'joe', enter password to login.
Password:
230-Welcome, archive user joe@spsd-gateway.spsd.org !
230-
230-The local time is: Tue Apr 15 10:07:56 2008
230-
230-This is an experimental FTP server.  If have any unusual problems,
230-please report them via e-mail to <root@muddleftpd>.
230-
230-
230 User 'joe' login successful.
ftp> dir
200 PORT command successful. Data port is 169.244.100.48 port 1559.
150 Starting ASCII transfer for file listing.
total 4
-rw-r--r--   1 root     root          166 Jun 15  2007 welcome.msg
226 Transfer done. 77 bytes transferred.
ftp: 77 bytes received in 0.02Seconds 4.81Kbytes/sec.
ftp>

```
However, I can log in as any name and password combination I want.  And ls and dir don't show any folders.  I've just installed muddleftpd, because PROftpd said it was running, but I couldn't connect.  

I'm at school when I telnet to it, so it is accepting those connections.  But wtf is BusyBox?  Is that the telnet name?  What's weird, is that it acts just like I am processing commands form home.  I can enter those commands through telnet and get results.  This is the output of the commands.

iptables -L -vnx:
```
# iptables -L -vnx
Chain INPUT (policy ACCEPT 3034 packets, 255039 bytes)
    pkts      bytes target     prot opt in     out     source               dest
ination
    7411   500667 QUEUE      udp  --  br0    *       0.0.0.0/0            0.0.0.
0/0           udp dpt:53
      40     4740 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:80
      10      480 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           state NEW tcp dpt:23
      75     6108 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.
0/0
    6322   647924 ACCEPT     all  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           state RELATED,ESTABLISHED
    3736  1581792 DROP       all  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0

Chain FORWARD (policy ACCEPT 6260952 packets, 2952262805 bytes)
    pkts      bytes target     prot opt in     out     source               dest
ination
       0        0 REJECT     tcp  --  br0    *       0.0.0.0/0            0.0.0.
0/0           state INVALID,NEW,RELATED,UNTRACKED tcp dpt:23 flags:!0x02/0x02 re
ject-with tcp-reset
     529    65448 QUEUE      udp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           udp spt:53
     534    34206 QUEUE      udp  --  *      ppp0    0.0.0.0/0            0.0.0.
0/0           udp dpt:53
       0        0 ACCEPT     udp  --  br0    *       192.168.1.65         0.0.0.
0/0           udp spt:3389
      24      960 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:3389
       0        0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        udp dpt:3389
      24     1164 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:3389
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:4899
       1       40 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:4899
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spts:3999:4000
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpts:3999:4000
       0        0 ACCEPT     udp  --  br0    *       192.168.1.65         0.0.0.
0/0           udp spts:3996:3998
       0        0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        udp dpts:3996:3998
      21      936 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:5900
     135     6376 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:5900
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:5800
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:5800
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:5500
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:5500
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:799
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:799
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:5100
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:5100
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:194
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:194
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:6667
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:6667
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:23
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:23
      98     5206 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:20
      60     2480 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:20
     179    14905 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:21
     269    12887 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:21
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:443
       1       48 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:443
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:80
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:80
       0        0 ACCEPT     47   --  br0    *       192.168.1.65         0.0.0.
0/0
       0        0 ACCEPT     47   --  ppp0   *       0.0.0.0/0            192.16
8.1.65
       0        0 ACCEPT     tcp  --  br0    *       192.168.1.65         0.0.0.
0/0           tcp spt:1723
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        tcp dpt:1723
       0        0 ACCEPT     udp  --  br0    *       192.168.1.65         0.0.0.
0/0           udp spt:4500
       0        0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        udp dpt:4500
       0        0 ACCEPT     esp  --  br0    *       192.168.1.65         0.0.0.
0/0
       0        0 ACCEPT     esp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65
       0        0 ACCEPT     udp  --  br0    *       192.168.1.65         0.0.0.
0/0           udp spt:500
       0        0 ACCEPT     udp  --  ppp0   *       0.0.0.0/0            192.16
8.1.65        udp dpt:500
   44584  1966916 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.
0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU
 2804263 248554119 sLog       all  --  !ppp0  ppp0    0.0.0.0/0            0.0.0
.0/0           sLog max_num 50 timeout 300

Chain OUTPUT (policy ACCEPT 7165 packets, 970928 bytes)
    pkts      bytes target     prot opt in     out     source               dest
ination
    7410   773146 QUEUE      udp  --  *      br0     0.0.0.0/0            0.0.0.
0/0           udp spt:53
       0        0 DROP       udp  --  *      ppp0    0.0.0.0/0            0.0.0.
0/0           udp spt:520
      95     4764 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.
0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU
      14      952 DROP       icmp --  *      ppp0    0.0.0.0/0            0.0.0.
0/0           icmp type 3
       0        0 DROP       icmp --  *      ppp0    0.0.0.0/0            0.0.0.
0/0           state INVALID
#

```
iptables -L -vnx --table nat
```
# iptables -L -vnx --table nat
Chain PREROUTING (policy ACCEPT 35535 packets, 3100274 bytes)
    pkts      bytes target     prot opt in     out     source               dest
ination
       8      480 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:4567 to:192.168.1.1:80
      10      480 REDIRECT   tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:23 redir ports 23
       0        0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           state NEW tcp dpt:80
       0        0 REDIRECT   tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:80 redir ports 80
       0        0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           udp dpt:3389 to:192.168.1.65:3389
      24     1164 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:3389 to:192.168.1.65:3389
       1       40 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:4899 to:192.168.1.65:4899
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpts:3999:4000 to:192.168.1.65:3999-4000
       0        0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           udp dpts:3996:3998 to:192.168.1.65:3996-3998
      48     2332 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:5900 to:192.168.1.65:5900
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:5800 to:192.168.1.65:5800
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:5500 to:192.168.1.65:5500
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:799 to:192.168.1.65:799
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:5100 to:192.168.1.65:5100
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:194 to:192.168.1.65:194
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:6667 to:192.168.1.65:6667
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:23 to:192.168.1.65:23
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:20 to:192.168.1.65:20
      20     1012 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:21 to:192.168.1.65:21
       1       48 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:443 to:192.168.1.65:443
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:80 to:192.168.1.65:80
       0        0 DNAT       47   --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           to:192.168.1.65
       0        0 DNAT       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:1723 to:192.168.1.65:1723
       0        0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           udp dpt:4500 to:192.168.1.65:4500
       0        0 DNAT       esp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           to:192.168.1.65
       0        0 DNAT       udp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           udp dpt:500 to:192.168.1.65:500
       0        0 DROP       tcp  --  ppp0   *       0.0.0.0/0            0.0.0.
0/0           tcp dpt:80

Chain POSTROUTING (policy ACCEPT 112 packets, 5649 bytes)
    pkts      bytes target     prot opt in     out     source               dest
ination
   30624  1406845 MASQUERADE  all  --  *      ppp0    0.0.0.0/0            0.0.0
.0/0

Chain OUTPUT (policy ACCEPT 1147 packets, 73062 bytes)
    pkts      bytes target     prot opt in     out     source               dest
ination
#

```
netstat -lnp --inet  Did not work

lsmod |grep ip_  No output

ifconfig
```
# ifconfig
br0       Link encap:Ethernet  HWaddr 00:18:01:9D:42:D7
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:6317801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6311755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3081251139 (2938.5 Mb)  TX bytes:3065775316 (2923.7 Mb)

br1       Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

br2       Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:18:01:9D:42:D7
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:2815836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3618739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:307809282 (293.5 Mb)  TX bytes:2736887601 (2610.0 Mb)
          Base address:0x2800

imq0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
-00
          UP RUNNING NOARP  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1  ASYMMTU:0
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:56527 (55.2 kb)  TX bytes:56527 (55.2 kb)

nas0      Link encap:Ethernet  HWaddr 00:18:01:9D:42:D8
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:3489641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2990735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:2783725331 (2654.7 Mb)  TX bytes:351152613 (334.8 Mb)

ppp0      Link encap:Point-Point Protocol
          inet addr:70.16.108.60  P-t-P:10.21.1.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1  ASYMMTU:15
00
          RX packets:3468632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2811807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:2706151490 (2580.7 Mb)  TX bytes:249238230 (237.6 Mb)

usb0      Link encap:Ethernet  HWaddr 00:18:01:9D:42:D9
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:01:9D:42:DB
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  ASYMMTU:1500
          RX packets:12343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:820748 (801.5 kb)  TX bytes:36394226 (34.7 Mb)

#
```

These are all done through telnet, so I assume they are accurate.  I will check later when I get home.

---

### Post by SpaceTeddy on 2008-04-15
mhm... somehow i don't think you got into your  linux box... i have the suspicion that you accidentially telnet'ed into your little router box at home. Which means (assuming i am right), ANYONE from ANYWHERE can do ANYTHING to your router, including reading your username and password from your ISP. You can check that theory by going home and then running the commands again locally on your linux box.... if they differ lots, you were on a different machine. Also, busybox is a very small kernel usually running on these routers... Furthermore, it strikes me VERY odd that your computer would have three bridge devices installed, but netstat is not installed... i'd really put my money on the router :(

in case i was not clear, this is a HUGE security risk !

i'll wait for further input from you before we continue...

---

### Post by Pap3r on 2008-04-15
That makes the most sense, because my router password and user name are the ones I have to use.

These are my results from my Linux Box (physically on it now).

sudo iptables -L -vnx
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02
    1023   102231 ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0
       0        0 ACCEPT     tcp  --  *      *       71.243.0.12          0.0.0.0/0           tcp flags:!0x17/0x02
     207    25254 ACCEPT     udp  --  *      *       71.243.0.12          0.0.0.0/0
    8697   352251 ACCEPT     0    --  lo     *       0.0.0.0/0            0.0.0.0/0
      31    17856 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
       0        0 DROP       0    --  eth0   *       0.0.0.0/0            255.255.255.255
     150    34535 DROP       0    --  *      *       0.0.0.0/0            192.168.1.255
       0        0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0
       0        0 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8
       0        0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0
       0        0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0
       3      120 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID
       0        0 LSI        0    -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5
  247193 125212123 INBOUND    0    --  eth0   *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input'

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5
       0        0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward'

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     tcp  --  *      *       192.168.1.65         192.168.1.1         tcp dpt:53
    1021    71426 ACCEPT     udp  --  *      *       192.168.1.65         192.168.1.1         udp dpt:53
       0        0 ACCEPT     tcp  --  *      *       192.168.1.65         71.243.0.12         tcp dpt:53
     207    13248 ACCEPT     udp  --  *      *       192.168.1.65         71.243.0.12         udp dpt:53
    8697   352251 ACCEPT     0    --  *      lo      0.0.0.0/0            0.0.0.0/0
       0        0 DROP       0    --  *      *       224.0.0.0/8          0.0.0.0/0
      18     1116 DROP       0    --  *      *       0.0.0.0/0            224.0.0.0/8
       0        0 DROP       0    --  *      *       255.255.255.255      0.0.0.0/0
       0        0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0
       9      360 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID
  226738 82117145 OUTBOUND   0    --  *      eth0    0.0.0.0/0            0.0.0.0/0
       0        0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output'

Chain INBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination
  157012 101653928 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
   90151 23556683 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
       0        0 ACCEPT     0    --  *      *       192.168.1.64         0.0.0.0/0
       0        0 ACCEPT     0    --  *      *       70.15.54.154         0.0.0.0/0
       7      336 ACCEPT     0    --  *      *       169.244.100.48       0.0.0.0/0
       3      144 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:3389
       0        0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:3389
       0        0 ACCEPT     tcp  --  *      *       169.244.100.48       0.0.0.0/0           tcp dpt:21
       0        0 ACCEPT     udp  --  *      *       169.244.100.48       0.0.0.0/0           udp dpt:21
      20     1032 LSI        0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination

Chain LSI (2 references)
    pkts      bytes target     prot opt in     out     source               destination
      20     1032 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
      20     1032 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
      20     1032 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8
       0        0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound '
       0        0 DROP       0    --  *      *       0.0.0.0/0            0.0.0.0/0

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 LOG_FILTER  0    --  *      *       0.0.0.0/0            0.0.0.0/0
       0        0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound '
       0        0 REJECT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination
       3      435 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0
  142308 75405743 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
   82267  6614607 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
    2160    96360 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0
joe@joe-desktop:~$  
```
sudo iptables -L -vnx --table nat
```
Chain PREROUTING (policy ACCEPT 261 packets, 48116 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 4071 packets, 194148 bytes)
    pkts      bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 4106 packets, 197065 bytes)
    pkts      bytes target     prot opt in     out     source               destination
joe@joe-desktop:~$  
```
sudo netstat -lnp --inet
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     14942/python
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     13624/muddleftpd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5361/cupsd
tcp        0      0 0.0.0.0:15000           0.0.0.0:*               LISTEN     5551/wesnothd
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          5699/avahi-daemon:
udp        0      0 0.0.0.0:32816           0.0.0.0:*                          13664/C:\Program Fi
udp        0      0 0.0.0.0:32820           0.0.0.0:*                          13664/C:\Program Fi
udp        0      0 0.0.0.0:32826           0.0.0.0:*                          13664/C:\Program Fi
udp        0      0 0.0.0.0:68              0.0.0.0:*                          5839/dhclient
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          5699/avahi-daemon:

joe@joe-desktop:~$  sudo sshd
sshd re-exec requires execution with an absolute path

joe@joe-desktop:~$ sudo ftpd
muddleftpd error in file procnum.c line 186: Muddleftpd already running!
CANNOT RESUME. Goodbye

```
sudo lsmod |grep ip_
```

ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:17:31:8B:27:14
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe8b:2714/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:478610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:441920773 (421.4 MB)  TX bytes:99021704 (94.4 MB)
          Interrupt:3 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:17:31:8B:2D:1A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:369919 (361.2 KB)  TX bytes:369919 (361.2 KB)

```

I really appreciate your help-- thanks a ton.

EDIT--
I'm using a dynamic DNS from dyndns.com  When I telnet, I use my dyndns.

---

### Post by SpaceTeddy on 2008-04-15
oh god... i just looked at the iptables rules created by firestarter... makes me want to cry... but, i will come to that later... 

first, the output of netstat
> tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     14942/python
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     13624/muddleftpd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5361/cupsd
tcp        0      0 0.0.0.0:15000           0.0.0.0:*               LISTEN     5551/wesnothd

these are the services currently actively broadcasting into the world... i don't see any ssh server, as well as i don't see any vnc or rdp port open... even if you installed those services, they are not running. At least for ssh server i know, you have to install the openssh-server
```
sudo apt-get install openssh-server
```
that should configure it and start it all by itself and at boottime. check after the install with netstat again if it really is running. As for VNC or RDP - i have no idea how those work. I only use and live in consoles...

ifconfig is next... you only have one network card configured. Which means, your computer is NOT being used a router. this also means that you will need to do port forwarding on your router to your box to make sure you can reach it via your dyndns name... the same thing is told by iptables -L -vnx --table nat. there are no maquerading rules or anything that rewrites... so i guess you are using this as a stand-alone machine behing the router... 

no... *shudder*... iptables -L -vnx. I know these rules were created by firestarter... i will need some time to understand them... 

ok, i don't undestand them... really... i have no clue what they do (or at least some of them). You if something does not work although the server is running (check via netstat) then it is either a firestarter or a port forwarding problem... what i cannot tell at the moment... sorry. My concentration is pretty bad at the moment anyway... been answering and explaining too much :)

hope this helps at least a little bit...

PS:maybe i have not stressed this point enough... but your router is vulnerable from the internet. Make sure that you have a proper username and password set, and close the telnet port. telnet is an old protocol, which is unencrypted. Anyone can listen in to what you are typing there. and believe me, listening in is easy if you want to do it. So... close it !!! make sure your router does not have any unneccessary open ports !!!

---

### Post by Pap3r on 2008-04-15
Alright, first thing first, I already have openssh-server...  It doesn't run though.  I'm not aware why, it's installed, but it doesn't show up on the netstat (super useful command, thanks for explaining it to me).

Secondly, I will get right on the Router security, I'm doing it as I type this.

Thirdly, no worries about the RDP/VNC thing, I'm almost certain I only need vncviewer to VNC to my other computers, which I have, I also just configured the password etc.

Lastly, when I FTP to my comp, I'm able to now, I have no directories, just the a welcome message.  Do I need to add the paths to files into muddleftp?  I just connected again to make sure via smartftp.  It connects to the '/' folder, but nothing else is listed.

---

### Post by Pap3r on 2008-04-15
Here's something.  I've found that I do indeed have many openssh programs installed.  I have openssl, openssh-server, openssh-client, sshd etc. etc.

I can start/stop/restart the ssh servers using ```
sudo /etc/init.d/ssh start
```
I get ```
pap3r|joe-desktop~| sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd                                                                                                         [ OK ]
```From that, but a netstat command shows the same as before- no ssh daemon.

---

### Post by SpaceTeddy on 2008-04-16
check your logs in /var/log/syslog und /var/log/messages if there are any errors why your sshd server does not come up... 
also, i've just  figured out i am a moron... the flag --inet will not show any ipv6 sockets, which the openssh-server will bind to in it's default configuration... 

use ```
sudo netstat -lnx
``` to see the full list... if there is a line looking like this, it started and simply did not show... 
>  netstat -lnp
tcp6       0      0 :::22                   :::*                    LISTEN     2854/sshd   


sorry for the confusion :(

---

### Post by Pap3r on 2008-04-16
Okay, so I got ```
pap3r|joe-desktop~| netstat -lnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:57639           0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:48397           0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:58356           0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:15000           0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     -
tcp6       0      0 :::5900                 :::*                    LISTEN     6444/vino-server
**tcp6       0      0 :::22                   :::*                    LISTEN     -**
udp        0      0 0.0.0.0:32768           0.0.0.0:*                          -
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          -
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          -
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          -
udp        0      0 0.0.0.0:32772           0.0.0.0:*                          -
udp        0      0 192.168.1.65:137        0.0.0.0:*                          -
udp        0      0 0.0.0.0:137             0.0.0.0:*                          -
udp        0      0 192.168.1.65:138        0.0.0.0:*                          -
udp        0      0 0.0.0.0:138             0.0.0.0:*                          -
udp        0      0 0.0.0.0:68              0.0.0.0:*                          -
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          -
udp        0      0 0.0.0.0:876             0.0.0.0:*                          -
udp        0      0 0.0.0.0:111             0.0.0.0:*                          -
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     28341    6595/mapping-daemon /tmp/mapping-joe
unix  2      [ ACC ]     STREAM     LISTENING     18786    -                   /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     26828    6382/gnome-keyring- /tmp/keyring-zLf0i1/socket
unix  2      [ ACC ]     STREAM     LISTENING     26935    -                   /tmp/ssh-qFvNjb6385/agent.6385
unix  2      [ ACC ]     STREAM     LISTENING     26965    6424/gconfd-2       /tmp/orbit-joe/linc-1918-0-73dd9ee7a972b
unix  2      [ ACC ]     STREAM     LISTENING     26978    6385/x-session-mana /tmp/orbit-joe/linc-18f1-0-4d8a3e7eb884d
unix  2      [ ACC ]     STREAM     LISTENING     27258    6385/x-session-mana /tmp/.ICE-unix/6385
unix  2      [ ACC ]     STREAM     LISTENING     27299    6430/gnome-settings /tmp/orbit-joe/linc-191e-0-106cb63e84814
unix  2      [ ACC ]     STREAM     LISTENING     27398    6437/bonobo-activat /tmp/orbit-joe/linc-1925-0-770af286cc64c
unix  2      [ ACC ]     STREAM     LISTENING     27508    6444/vino-server    /tmp/orbit-joe/linc-192c-0-6954aa0f34762
unix  2      [ ACC ]     STREAM     LISTENING     27527    6495/gnome-screensa /tmp/orbit-joe/linc-192f-0-77975de638780
unix  2      [ ACC ]     STREAM     LISTENING     27668    6491/gnome-volume-m /tmp/orbit-joe/linc-1935-0-7ba392a29a40c
unix  2      [ ACC ]     STREAM     LISTENING     27685    6449/gnome-panel    /tmp/orbit-joe/linc-1931-0-7ba392a2a1303
unix  2      [ ACC ]     STREAM     LISTENING     27692    6452/nautilus       /tmp/orbit-joe/linc-1934-0-7ba392a2a2a1c
unix  2      [ ACC ]     STREAM     LISTENING     18454    -                   /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     27795    6516/gnome-vfs-daem /tmp/orbit-joe/linc-1974-0-31abf97f157c1
unix  2      [ ACC ]     STREAM     LISTENING     28015    6564/bluetooth-appl /tmp/orbit-joe/linc-19a4-0-2cd32e89fbe7
unix  2      [ ACC ]     STREAM     LISTENING     28067    6570/gksu           /tmp/orbit-joe/linc-19aa-0-69874674cc38e
unix  2      [ ACC ]     STREAM     LISTENING     28149    6590/gnome-power-ma /tmp/orbit-joe/linc-19ac-0-3513fc672faa9
unix  2      [ ACC ]     STREAM     LISTENING     28192    6579/nm-applet      /tmp/orbit-joe/linc-19b3-0-3513fc673bf48
unix  2      [ ACC ]     STREAM     LISTENING     28134    6563/vino-session   /tmp/orbit-joe/linc-19a3-0-72419142cb85
unix  2      [ ACC ]     STREAM     LISTENING     28140    6566/update-notifie /tmp/orbit-joe/linc-19a6-0-72419142e006
unix  2      [ ACC ]     STREAM     LISTENING     28208    6562/compiz.real    /tmp/orbit-joe/linc-19a2-0-19cac3a649337
unix  2      [ ACC ]     STREAM     LISTENING     28385    6597/cpufreq-applet /tmp/orbit-joe/linc-19c5-0-50e1b02f3bb62
unix  2      [ ACC ]     STREAM     LISTENING     28480    6613/multiload-appl /tmp/orbit-joe/linc-19d5-0-ea05f7a1087e
unix  2      [ ACC ]     STREAM     LISTENING     28505    6615/sensors-applet /tmp/orbit-joe/linc-19d7-0-ea05f7a2e9ca
unix  2      [ ACC ]     STREAM     LISTENING     28548    6609/gweather-apple /tmp/orbit-joe/linc-19d1-0-ea05f7a5edaa
unix  2      [ ACC ]     STREAM     LISTENING     28574    6611/charpick_apple /tmp/orbit-joe/linc-19d3-0-ea05f7a769b3
unix  2      [ ACC ]     STREAM     LISTENING     28696    6571/evolution-alar /tmp/orbit-joe/linc-19ab-0-3c9fd2fbe1475
unix  2      [ ACC ]     STREAM     LISTENING     29166    6645/trashapplet    /tmp/orbit-joe/linc-19f5-0-6472dce463be9
unix  2      [ ACC ]     STREAM     LISTENING     28931    6631/tsclient-apple /tmp/orbit-joe/linc-19e7-0-5841775c53552
unix  2      [ ACC ]     STREAM     LISTENING     29003    6637/evolution-data /tmp/orbit-joe/linc-19ed-0-35fcd29c23748
unix  2      [ ACC ]     STREAM     LISTENING     29288    6658/evolution-exch /tmp/orbit-joe/linc-1a02-0-4f9f34d67dcee
unix  2      [ ACC ]     STREAM     LISTENING     31131    -                   /tmp/orbit-root/linc-1a18-0-76692ff3b5aa7
unix  2      [ ACC ]     STREAM     LISTENING     31139    -                   /tmp/orbit-root/linc-19bc-0-2d51a960b8d43
unix  2      [ ACC ]     STREAM     LISTENING     18741    -                   /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     16352    -                   @/var/run/hald/dbus-UfbJk0s9aq
unix  2      [ ACC ]     STREAM     LISTENING     2865769  9467/kdeinit Runnin /tmp/ksocket-joe/kdeinit__0
unix  2      [ ACC ]     STREAM     LISTENING     16355    -                   @/var/run/hald/dbus-VFQwAddE5V
unix  2      [ ACC ]     STREAM     LISTENING     2865771  9467/kdeinit Runnin /tmp/ksocket-joe/kdeinit-:0
unix  2      [ ACC ]     STREAM     LISTENING     42749    6961/firefox-bin    /tmp/orbit-joe/linc-1b31-0-5fef78b2f67a
unix  2      [ ACC ]     STREAM     LISTENING     2865778  9470/dcopserver [kd /tmp/.ICE-unix/dcop9470-1208374985
unix  2      [ ACC ]     STREAM     LISTENING     2865800  9473/klauncher [kde /tmp/ksocket-joe/klauncher28Pdmb.slave-socket
unix  2      [ ACC ]     STREAM     LISTENING     2879496  9583/artsd          /tmp/ksocket-joe/joe-desktop-256f-480657c9
unix  2      [ ACC ]     STREAM     LISTENING     16335    -                   @/tmp/dbus-LTBG98103t
unix  2      [ ACC ]     STREAM     LISTENING     18657    -                   @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     18521    -                   /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     1400163  -                   /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16276    -                   /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     16020    -                   /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     27273    6428/dbus-daemon    @/tmp/dbus-5JA9wLGc2G
unix  2      [ ACC ]     STREAM     LISTENING     18523    -                   @/var/run/dbus-9z8C2m4TiE
pap3r|joe-desktop~|                                                                                      
```
It shows, but not as sshd.

EDIT

Question about muddleftp.  When I connect, it connects me to my machine, I'm positive.  However, the folder I connect to (/home/ftp) only contains one file: welcome.msg  I can't navigate anywhere, so I assume that for this ftp server, only files I may need remotely would be stored in that folder?  I.e., I may need an essay for school, so I put it in the /home/ftp folder, then recv it?  Or is there a way to make it connect to my computer as a whole, which is what ssh does (this is why I want it to work so badly :( )

---

### Post by SpaceTeddy on 2008-04-16
> **Pap3r said:**
> Okay, so I got ```
**tcp6       0      0 :::22                   :::*                    LISTEN     -**
```
It shows, but not as sshd. 
oh yes, it does. But netstat is not able to figure out the process attached to a port if it is not run by root. if you put a sudo infront of your command, you will see the port is attached to your sshd process :)
> **Pap3r said:**
>  Question about muddleftp.  When I connect, it connects me to my machine, I'm positive.  However, the folder I connect to (/home/ftp) only contains one file: welcome.msg  I can't navigate anywhere, so I assume that for this ftp server, only files I may need remotely would be stored in that folder?  I.e., I may need an essay for school, so I put it in the /home/ftp folder, then recv it?  Or is there a way to make it connect to my computer as a whole, which is what ssh does (this is why I want it to work so badly :( )

Honest - if you can avoid normal ftp - avoid it. the protocoll might have been good at some point in the past (and still is when it comes to overhead) but in general, ftp is a PAIN.
The openssh server you run can handle sftp sessions aswell. You can authenticate with your normal username and password, and you can browse the full directory tree as you want. So if you can, use sftp (winscp is a nice client for it)

But back to your problem.
I would like to run some internal tests first. on your computer, open a console and try run 
```
ssh localhost
```
this should ask you for a password, and then connect you to your own machine. Of course you cannot see that, as the console will not change. All you should get is another welcome message.

if that worked, try to connect to your machine from another computer. if that other machine is a linux, use
```
ssh username@ip
``` where you repace username by your login name, and the ip by the ip of your computer. 
Again, you should be prompted for a username and password, and should be able to log in again. Make sure both Connections work !

If, for some odd reason, the connections do not work, run these commands on your ubuntu box and try again. They basicially disable your firewall. Don't worry, after a reboot, everything will be back to normal :)

```
sudo iptables -F INPUT
sudo iptables -F OUTPUT
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

the first two delete ALL rules for pakets going from and to your computer - the second pair makes sure that any and every paket is processed and none is droped.

tell me how the testing is going :)

oh, one more thing regarding sFTP (via ssh) instead of ftp - sFTP is encrypted and secure - and supports host verification. FTP does none of these :(

---

### Post by Pap3r on 2008-04-16
Yes, I noticed the normal FTP not verifying my login name.

Anyway, yeah, I am able to ssh to localhost, as well as ssh via a computer in my network through PuTTY.```
sudo netstat -lnp
``` Does indeed show the ssh server, which is nice.

I'm having a friend of mine test the SSH from his computer down the street, so I'll get back to you on external ip ssh connections.

---

### Post by Pap3r on 2008-04-17
Update

So my friends computer dumb, it couldn't connect to anything, not FTP, not VNC etc.  It was a problem on his side.  Anyway, I'm in school right now, and I can FTP and VNC to my computer from the school computer.  I am however, unable to connect via SSH... still.  I am positive that the SSHD server is running, I can VNC then check through the konsole, but I can't connect remotely.

---

### Post by SpaceTeddy on 2008-04-17
this sounds like a port forwarding problem to me. check your router (little box) if port 22 is being forwarded to your machine correctly.

---

### Post by Pap3r on 2008-04-17
It wasn't in my Rules table, so I made two new rules;

Name: SSH
Protocol: TCP
Port Start: 22
Port End: 22
Portmap: 22

Name: SSH2
Protocol: UDP
Port Start: 22
Port End: 22
Portmap: 22

---

