---
title: "internet conection failure with sis ethernet controller"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by spinctz on 2008-03-12
ubuntu  detects it but we i'm trying to connect to the internet i don't have any conection ... here is what the dmesg exec after i plug in the cable :

[ 4889.256000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4904.264000] wlan0: no IPv6 routers present


please help

---

### Post by SpaceTeddy on 2008-03-12
can you please provide the output of the following commands to further debug your problem 

```
ifconfig
iwconfig
cat /etc/network/interfaces
ip link show
route -n

```

thanks

---

### Post by spinctz on 2008-03-12
[PHP]spinctz@spinctz-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1672 (1.6 KB)  TX bytes:1672 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:A0:D1:CA:B9:AF  
          inet addr:192.168.1.168  Bcast:192.168.1.255  
Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:feca:b9af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24126 (23.5 KB)  TX bytes:30579 (29.8 KB)
          Interrupt:22 Memory:d4407000-d4407080 
[/PHP]


[PHP]spinctz@spinctz-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 
Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/PHP]

[PHP]spinctz@spinctz-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback[/PHP]

[PHP]spinctz@spinctz-laptop:~$ ip link show
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlan0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 
1000
    link/ether 00:a0:d1:ca:b9:af brd ff:ff:ff:ff:ff:ff
3: wlan1: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:c0:a8:fe:81:38 brd ff:ff:ff:ff:ff:ff[/PHP]

[PHP]spinctz@spinctz-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use 
Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 
wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 
wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 
wlan0
[/PHP]

10x for reply

---

### Post by SpaceTeddy on 2008-03-12
accoring to what you have supplied as output, your network seems to be working flawlessly. Your interface is configured correctly, the gateway is set. Your network card should work.
What confuses me tho is that the card wlan0 claims to have no wireless extension - which does not make sense. 

maybe you could describe your problem again, since i am unsure at the moment where exactly the problem lies - the network seems to be configured correctly !

---

### Post by spinctz on 2008-03-12
i forgot to mention that i m conecting throw a wired router and i can ping the router ... but when i m trying to ping an external address i don't get any response ... i read something about ipv6 ... maybe is because of the dhcp ... don't think is well configured ...
i have a wireless card which works assigned with wlan1 and the wired card (i don't know why) is assigned with wlan0

---

### Post by SpaceTeddy on 2008-03-12
mhm - a ping to [www.google.com](www.google.com) will result in nothing - how about pinging the ip ? does that give you answers ?
```
ping -c 4 209.85.129.99
```

if it does, this seems to be a dns problem. if not... well... then i would assume that something in your router blocks you... (btw. what is the ip of your router ?)

---

### Post by spinctz on 2008-03-12
yes the ping to the ip works ... now what do i have to do ? 
the ip of the router is 192.168.1.1

---

### Post by SpaceTeddy on 2008-03-12
ok, since the ping works, but addressing the name does not, i think this is a dns problem. to confirm that, plase post the content of this command
```
cat /etc/resolv.conf
```
which will list your current dns server. also, try to ping those servers and see if they reply. I good guess is that your router is in there - possibly the only dns server. 
if that is the case, and other computers (obviously) can access the internet, then it is either   ubuntu not pulling the servers right, or something blocking the connection.
Do you have any firewall software installed (i never used any, but names i have come across are firestarter - for example)

---

### Post by spinctz on 2008-03-12
```
spinctz@spinctz-laptop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!



nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.1.1

```

no response from any of them

---

### Post by SpaceTeddy on 2008-03-12
what do you mean by "no response" from any of them. one of them is your router, and you said you can ping that one. so can you ping those servers ? (i get responses from here)

if you can ping them, but cannot do queries, then i would like you to take a look at your ip-filter table... you can do that with
> sudo iptables -L -vnx

---

### Post by spinctz on 2008-03-12
ok... sorry for the post before ... the lan network wasn't ready when i pinged the ips ,,, so that is why i didn't get any response ... so they all work ... 

```
spinctz@spinctz-laptop:~$ sudo iptables -L -vnx
[sudo] password for spinctz:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```

---

### Post by SpaceTeddy on 2008-03-13
this is starting to get weird. The ping works, so that means the servers themselves are reachable. This also means that your ip and gateway are correct and your internet connection is working. 

the nameservers respond to the queries from here, so i know they work too. The path there must be working (the pings would not work otherwise).

there is nothing in your filter configuration that would prohibit your computer to send or recieve pakets.

i am starting to run out of ideas what the problem could be :(

just to be on safe side, can you please do a traceroute for the dns servers ?
i.e. run these commands ?
```
traceroute 208.67.222.222
traceroute 208.67.220.220
traceroute 192.168.1.1
```

---

### Post by spinctz on 2008-03-13
```
spinctz@spinctz-laptop:~$ traceroute 192.168.1.1
traceroute to 192.168.1.1 (192.168.1.1), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * *
Ctrl+C
```

```
spinctz@spinctz-laptop:~$ traceroute 208.67.222.222
traceroute to 208.67.222.222 (208.67.222.222), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.870 ms  0.945 ms  1.147 ms
 2  10.164.0.1 (10.164.0.1)  8.867 ms  12.360 ms  16.578 ms
 3  89.137.0.209 (89.137.0.209)  17.234 ms  16.707 ms  17.176 ms
Ctrl+C
```

```
spinctz@spinctz-laptop:~$ traceroute 208.67.220.220
traceroute to 208.67.220.220 (208.67.220.220), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  0.845 ms  0.916 ms  1.092 ms
 2  10.164.0.1 (10.164.0.1)  14.102 ms  18.292 ms  24.139 ms
 3  89.137.0.209 (89.137.0.209)  24.560 ms  24.777 ms  24.991 ms
Ctrl+C
```

hope this means something ...

---

### Post by SpaceTeddy on 2008-03-13
this means that your internet setup is correct and you are acctially going out into the internet. it also means that your router blocks icmp pakets (but that is of absolutly no concern).

the bad side is that i am entirely at loss now as to why you do not get anything but icmp though... so lets run some more tests, shall we ?

first off, i would like you to test if you can pass anything BUT icmp to the internet. this can be tested as followed:
> telnet 209.85.129.99 80
this will give you a prompt with nothing in it - press any key and the enter twice, You should be getting back the html for the google page - if in doubt, paste the content here. If this works, then port 80 is passed to the internet. and you do get answers. next we try the same thing on the ssl port:
> telnet 209.85.129.99 443
here you do not get anything back, but you should still get the first three lines you got in the other response - i.e. it says "connected".

of this also works, your only problem is dns resolution. next, try to query nameservers direclty by using
> nslookup [www.google.de](www.google.de) 209.85.129.99
this should NOT work (as suggested before) but nonetheless, i thought we might try it anyway... 

that was all my ideas... really....

---

### Post by spinctz on 2008-03-13
```
spinctz@spinctz-laptop:~$ telnet 209.85.129.99 80
  

  


   
Trying 209.85.129.99...
Connected to 209.85.129.99.
Escape character is '^]'.
Connection closed by foreign host.
```

```

spinctz@spinctz-laptop:~$ telnet 209.85.129.99 443
Trying 209.85.129.99...
Connected to 209.85.129.99.
Escape character is '^]'.
Connection closed by foreign host.

```

```

spinctz@spinctz-laptop:~$ nslookup www.google.de 209.85.129.99
;; connection timed out; no servers could be reached
```

could you consider the problem appears because i installed the driver with ndiswrapper and my wired card is recognized as a wireless one ... my router is for wired connections ...no wireless ... but i can connect with my wireless card to a local network ...

---

### Post by SpaceTeddy on 2008-03-13
well, the connection acctually got though - you got an established tcp connection to google on port 80 and port 443 ! which means the problem is purely dns (or udp)

but i have no further idea what would block the udp pakets - althought my guess is that your router (for some reason) is blocking the pakets.

i have to give up here... no idea what the cause could be... sorry :(

---

### Post by spinctz on 2008-03-13
and if the router is blocking the packets ... what do i have to do ? port forwarding or something ? i can access the router from a win xp running pc ...

---

### Post by SpaceTeddy on 2008-03-13
port forwarding is not the answer... that is only for allowing connections from the internet to pass through your router. that is not what you want to do.
can you please check if you have a programm called tcpdump install ? can be checked via
> which tcpdump
maybe that can generate some more information... but i am really streching my ideas thin now...

---

