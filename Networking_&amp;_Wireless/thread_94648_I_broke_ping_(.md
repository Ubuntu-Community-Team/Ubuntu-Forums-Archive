---
title: "I broke ping :("
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by ace2005 on 2005-11-24
See what i mean


> PING google.com (72.14.207.99) 56(84) bytes of data.

--- google.com ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 5998ms

ace@Linux:~$ ping tiscali.co.uk
PING tiscali.co.uk (212.74.101.10) 56(84) bytes of data.

--- tiscali.co.uk ping statistics ---
45 packets transmitted, 0 received, 100% packet loss, time 44042ms

ace@Linux:~$ ping google.co.uk
PING google.co.uk (216.239.39.104) 56(84) bytes of data.

--- google.co.uk ping statistics ---
62 packets transmitted, 0 received, 100% packet loss, time 61127ms

ace@Linux:~$ ping ask.com
PING ask.com (65.214.39.56) 56(84) bytes of data.

--- ask.com ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

ace@Linux:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 5998ms

ace@Linux:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.

--- 127.0.0.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6009ms

ace@Linux:~$

Help Anyone???

The internet works fine, in fact i'm using it not to write this

---

### Post by jdong on 2005-11-24
Did you recently modify any firewall settings? Do any major upgrades? Does **ping localhost** work?

---

### Post by ace2005 on 2005-11-24
Well i first tried to get internet connection shareing via firestarter:

I can't get Firestarter and DHCP to do internet connection shareing for my second computer which is connected via a crossover cable, i've tried installing dhcp but that gives the error described below, tried dhcp3-server and that gives the same error, i set the config in firestarter and it says an unknown error ocurs. Konsole gave this:

> ace@Linux:~$ sudo firestarter
Firewall started
Failed to start DHCP server 	

With fedora core all i did was give it the ip 192.168.0.1 to the network adapter when i first installed Fedora Core and then in firestarter set the IPs to hand out to from 192.168.0.100 to 192.168.0.105. That was it.

So then i tried a guide from the forum:

[http://ubuntuforums.org/showthread.php?t=91370&highlight=reconfigure+internet](http://ubuntuforums.org/showthread.php?t=91370&highlight=reconfigure+internet)

My local network is on eth0 and my internet connection is on ppp0 (eagle usb)

and as for ping localhost:

> ace@Linux:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.

--- localhost ping statistics ---
192 packets transmitted, 0 received, 100% packet loss, time 191177ms

ace@Linux:~$

Help :(

---

### Post by jdong on 2005-11-24
Your meddling with Firestarter probably caused pings to be blocked. If **dmesg** is filled with messages then that's the culprit.

double-check your firestarter work to make sure you didn't set things too paranoid.

---

### Post by ace2005 on 2005-11-24
Well what does this mean?

> [4297417.336000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=0 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=1
[4297418.344000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=1 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=2
[4297419.337000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=2 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=3
[4297420.361000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=3 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=4
[4297421.369000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=4 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=5
[4297422.361000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=5 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=6
[4297423.369000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=6 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=7
[4297424.361000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=7 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=8
[4297425.369000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=8 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=9
[4297426.121000] Inbound IN=ppp0 OUT= MAC= SRC=80.42.194.81 DST=80.42.204.156 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=17700 DF PROTO=TCP SPT=4923 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0
[4297426.361000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=9 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=10
[4297427.369000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=10 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=11
[4297428.361000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=11 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=12
[4297429.369000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=12 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=13
[4297429.385000] Inbound IN=ppp0 OUT= MAC= SRC=80.42.194.81 DST=80.42.204.156 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=18040 DF PROTO=TCP SPT=4923 DPT=139 WINDOW=65535 RES=0x00 SYN URGP=0
[4297430.361000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=13 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=14
[4297431.370000] Inbound IN=ppp0 OUT= MAC= SRC=72.14.207.99 DST=80.42.204.156 LEN=84 TOS=0x00 PREC=0x40 TTL=243 ID=14 DF PROTO=ICMP TYPE=0 CODE=0 ID=23082 SEQ=15


So what do i do to fix it and get internet connection shareing to work?

---

### Post by jdong on 2005-11-24
that means pings are being blocked.

---

### Post by ace2005 on 2005-11-24
Ok

So do i just remove firestarter to get things to work or do i have to edit something and how come internet connection shareing isn't working?

"sudo firestarter" takes for ever to start

---

### Post by ace2005 on 2005-11-24
Ok now i think all the network settings are messed up, what command can i use to reconfigure the network?

See what i mean:

When i first turn on my computer and run ifconfig i get this:

> ace@Linux:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:60:4C:3A:54:39
          inet6 addr: fe80::260:4cff:fe3a:5439/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:65535  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14506 (14.1 KiB)  TX bytes:7947 (7.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:80.42.206.73  P-t-P:212.74.111.225  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:14267 (13.9 KiB)  TX bytes:5880 (5.7 KiB)


So i run ifconfig eth0 192.168.0.1

> ace@Linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe33:a63a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:238 (238.0 b)
          Interrupt:19 Base address:0xd400

eth1      Link encap:Ethernet  HWaddr 00:60:4C:3A:54:39
          inet6 addr: fe80::260:4cff:fe3a:5439/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:65535  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:366403 (357.8 KiB)  TX bytes:24193 (23.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:80.42.206.73  P-t-P:212.74.111.225  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:365492 (356.9 KiB)  TX bytes:17674 (17.2 KiB)

ace@Linux:~$


And this is /etc/network/interfaces

> ### etherconf DEBCONF AREA. DO NOT EDIT THIS AREA OR INSERT TEXT BEFORE IT.
auto lo eth0

iface lo inet loopback

iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast 


### END OF DEBCONF AREA.  PLACE YOUR EDITS BELOW; THEY WILL BE PRESERVED.


iface eth1 inet 


i used eatherconf which took over the config from KDE so now its really screwed up. No matter how many times i configure it, the configuraion never sticks

> ace@Linux:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
212.74.111.225  0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         212.74.111.225  0.0.0.0         UG        0 0          0 ppp0

And if i try to ping 192.168.0.2 i get

> 
ace@Linux:~$ sudo ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.2 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3998ms

ace@Linux:~$      

So how do i reconfigure this network and get it working?

I need some help

---

### Post by mips on 2005-11-25
Under Firestarter preferences their is a ICMP Filter option. Is it enabled or disabled ?

---

### Post by ace2005 on 2005-11-25
Yea i knew about that setting, yet strangely ignored it, and it was the cause thanks, well i never knew that ICMP was about pings. How do i make it allow everything for eth0 and only protect me from ppp0?

I screwed arround with the settings a bit more and things seem to be working ok and internet connection shareing is ok and everything is working fine, i just hope it stays that way when i restart.

---

### Post by ace2005 on 2005-11-25
YAY!!

everything wroks now, thanks for the help, in the end i used "sudo dpkg-reconfigure etherconf" to reconfigure the network and i used firestarter to enable get the internet connection sharing to work, turns out that i don't need to tick "Enable DHCP for local network" to get ICS to work

Thanks again :)

---

### Post by jdong on 2005-11-25
Very cool. Have fun :)

---

### Post by mips on 2005-11-25
[QUOTE=ace2005]YAY!!

everything wroks now, thanks for the help, in the end i used "sudo dpkg-reconfigure etherconf" to reconfigure the network and i used firestarter to enable get the internet connection sharing to work, turns out that i don't need to tick "Enable DHCP for local network" to get ICS to work

Thanks again :)[/QUOTE]

No DHCP is not a requirement as long as you statically configure the PC(s) that want to grant access to.

Ping uses Internet Control Messaging Protocol to get its job done. [http://www.erg.abdn.ac.uk/users/gorry/course/inet-pages/icmp.html](http://www.erg.abdn.ac.uk/users/gorry/course/inet-pages/icmp.html)

---

### Post by ace2005 on 2005-11-25
I tried it with static and with "Enable DHCP for local network"  turned off and nothing worked, made the XP computer get an IP from this one and it worked and this setting is still off.

---

