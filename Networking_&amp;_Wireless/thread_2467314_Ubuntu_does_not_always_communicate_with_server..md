---
title: "Ubuntu does not always communicate with server."
date: 2021-09-23
forum: Networking &amp; Wireless
---

### Post by Mititelu_Radu on 2021-09-23
Situation:
- servers:  1 linux server (samba file share) and 1 windows server in the server room
- lclients: Ubuntu workstation + few windows workstation in a different room 
- LAN infrastructure is the exact same between any client - server route. 
- windows clients can access all servers at any time
- linux client can access only windows server MOST of the time
 
Problem 
- Most of the time Ubuntu server is unreachable from Ubuntu client. Samba share does not work, ssh does not work, even ping packet are 100% lost.

Clarification
- communication between Linux client and server will go down and come up on its own with no action being taken 
- during down time Linux server is still accessible for windows clients, and Linux client can access everything except the Linux server 

Simply put ONLY Ubuntu serer - Ubuntu Client connection turns off and on without anyone doing anything on client or server. Every other connection between servers, clients and even outside services (the internet) work 100% of the time. 

Does anyone have any ideas on what may cause this, because I am not only lost, I have no idea what to even look for online. thank you.

---

### Post by TheFu on 2021-09-23
What release and flavor?
What is the hardware involved?
Is the Ubuntu Server configured with a static IP on-the-system?  If not, why not?
Does booting from a *Try Ubuntu *flash drive show the same issues? Use 20.04 LTS, please.
What are the exact configuration of the network, the LAN, the server networking and DNS?

This could easily be cable issue or switch or bad NIC issue. We cannot tell based on what's been said.

If you cannot ping the router, there isn't much to be done.

Typically, I'd look at these commands to figure out network issues. Since this is a server and you are obviously an IT pro, I won't go to the effort of making the exact commands from my bash troubleshooting script. You can figure out the variables to be set, yes?  Here's the function for getting network information.

```
function Networking(){
   Logging "Network Overview" 
   Logging " $INXI -izNnxz" 
   $INXI -c0 -izNnxz |$TEE -a $LOG

   Logging " lspci details" 
   $LSPCI -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' |$TEE -a $LOG

   Logging " lsusb details" 
   $SUDO $LSUSB -v  |$EGREP 'Ether|Network' |$TEE -a $LOG

   Logging " lshw network " 
   $SUDO $LSHW -sanitize -C network |$TEE -a $LOG

   Logging " ip addr " 
   $IP addr |$TEE -a $LOG

   Logging " ip route " 
   $IP route | column -t |$TEE -a $LOG

   Logging " resolv.conf file for DNS" 
   $CAT /etc/resolv.conf |$TEE -a $LOG
   if [ -L /etc/resolv.conf ] ; then
      Logging "WARNING: /etc/resolv.conf is a symbolic link; Name resolution file can change."
   fi

   Logging " ping gateway"   The read line is extremely picky about spacing.
   #GW=$($IP route | column -t |$EGREP "^default" | $AWK '{print $3}')
   GW=$(read -r x x i x< <($IP r g 1);echo "$i")
   $PING -c 1 $GW |$TEE -a $LOG

   Logging " For wifi issues, please run the wifi-info script from: https://github.com/UbuntuForums/"
}
```

---

### Post by Doug S on 2021-09-23
How do your various computers get their IP addresses? Via DHCP or static? Could there be any IP address conflict? Could there be a routing issue?

I would start by using tcpdump (or wireshark, if you prefer) and monitor ping packets from a linux client. Run tcpdump on both. Example:

Server, watching for ping packets:
```
doug@s15:~$ sudo tcpdump -tttt -n -i br0 icmp
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on br0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
2021-09-23 07:23:54.170153 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 1, length 64
2021-09-23 07:23:54.170205 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 1, length 64
2021-09-23 07:23:55.220635 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 2, length 64
2021-09-23 07:23:55.220678 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 2, length 64
2021-09-23 07:23:56.244656 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 3, length 64
2021-09-23 07:23:56.244701 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 3, length 64
2021-09-23 07:23:57.268616 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 4, length 64
2021-09-23 07:23:57.268659 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 4, length 64
2021-09-23 07:23:58.292622 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 5, length 64
2021-09-23 07:23:58.292666 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 5, length 64
2021-09-23 07:23:59.316627 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 6, length 64
2021-09-23 07:23:59.316671 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 6, length 64
2021-09-23 07:24:00.340636 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 7, length 64
2021-09-23 07:24:00.340680 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 7, length 64
^C
14 packets captured
14 packets received by filter
0 packets dropped by kernel
```

And a linux client also watching for ping packets:
```
doug@s19:~$ sudo tcpdump -tttt -n -i br0 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br0, link-type EN10MB (Ethernet), capture size 262144 bytes
2021-09-23 07:23:54.043924 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 1, length 64
2021-09-23 07:23:54.044126 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 1, length 64
2021-09-23 07:23:55.094410 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 2, length 64
2021-09-23 07:23:55.094629 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 2, length 64
2021-09-23 07:23:56.118429 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 3, length 64
2021-09-23 07:23:56.118657 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 3, length 64
2021-09-23 07:23:57.142391 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 4, length 64
2021-09-23 07:23:57.142643 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 4, length 64
2021-09-23 07:23:58.166394 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 5, length 64
2021-09-23 07:23:58.166620 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 5, length 64
2021-09-23 07:23:59.190400 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 6, length 64
2021-09-23 07:23:59.190639 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 6, length 64
2021-09-23 07:24:00.214412 IP 192.168.111.136 > 192.168.111.1: ICMP echo request, id 2, seq 7, length 64
2021-09-23 07:24:00.214641 IP 192.168.111.1 > 192.168.111.136: ICMP echo reply, id 2, seq 7, length 64
^C
14 packets captured
14 packets received by filter
0 packets dropped by kernel
```


And on that linux client I did this:

```
doug@s19:~/idle/teo/named/t03$ ping 192.168.111.1
PING 192.168.111.1 (192.168.111.1) 56(84) bytes of data.
64 bytes from 192.168.111.1: icmp_seq=1 ttl=64 time=0.206 ms
64 bytes from 192.168.111.1: icmp_seq=2 ttl=64 time=0.223 ms
64 bytes from 192.168.111.1: icmp_seq=3 ttl=64 time=0.231 ms
64 bytes from 192.168.111.1: icmp_seq=4 ttl=64 time=0.256 ms
64 bytes from 192.168.111.1: icmp_seq=5 ttl=64 time=0.229 ms
64 bytes from 192.168.111.1: icmp_seq=6 ttl=64 time=0.242 ms
64 bytes from 192.168.111.1: icmp_seq=7 ttl=64 time=0.233 ms
^C
--- 192.168.111.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6170ms
rtt min/avg/max/mdev = 0.206/0.231/0.256/0.014 ms
```

So, I would observe the packets leaving the client and getting to the host. Then I could observe the replies leaving the host and getting to the client.

EDIT: I see TheFu replied with excellent input while I was writing this.

---

### Post by Mititelu_Radu on 2021-09-24
Client is Ubuntu LTS 20.04.3, Server is Ubuntu LTS 20.04.04, both with all the updates installed, all the ip are static. 
Configuration is the clasic star with 1 up-link per switch, switches have management enabled, with no special port setup, just loop detection. 
DNS are the one provided by our IPS who manage the VPN between our remote locations and are also static. 
Gateway ping works and it is stable, so no signs of ip conflict. 
NIC is just fine since every other resources from the LAN and Internet is available to both server and client at all times. The only thing that does not work is the link between Ubuntu server and Ubuntu client. 
I will try with a live flash and use those commands to see if I can figure out why only those 2 machines refuse to communicate and only with each other. Thank you .

---

### Post by TheFu on 2021-09-24
If you can ping the router from both systems, it isn't general networking that's in the way.
Check for routing tables that aren't bi-directional and check the firewalls on each computer and filters that routers/switches might have between the two systems.

To get the best help, it is good to run commands AND show the output here.  In short, prove the claims above.  I often have found that things I believed to be true had been modified, either by a coworker or by me, which prevented things from working.

About 1 in 1000 times, I'd have an issue that came back to some subsystem.  Once a bridge setup for virtual machines refused to ping public IPs, but about 10 other VMs using the same bridge from the same physical VM host all worked.  I moved the VM to a different VM host (just moved the storage and VM definition) and it has been working perfect ever since that point.  I never figured out the issue. No other VMs on the 1st physical machine have shown that same issue. Around here, networking sorta just works. Our network only has a few subnets, 5 switches and 3 routers, so it doesn't get very complex.

---

### Post by TheFu on 2021-09-24
If you can ping the router from both systems, it isn't general networking that's in the way.
Check for routing tables that aren't bi-directional and check the firewalls on each computer and filters that routers/switches might have between the two systems.  ufw, iptables and ipset entries are where I'd start on Linux. If you use firewalld, check that as well.

To get the best help, it is good to run commands AND show the output here.  In short, prove the claims above.  I often have found that things I believed to be true had been modified, either by a coworker or by me, which prevented things from working.

About 1 in 1000 times, I'd have an issue that came back to some subsystem.  Once a bridge setup for virtual machines refused to ping public IPs, but about 10 other VMs using the same bridge from the same physical VM host all worked.  I moved the VM to a different VM host (just moved the storage and VM definition). Initially the problem followed the VM and all sorts of troubleshooting never found the root cause.  It magically started working perfect and has since that time ... about 3 yrs ago.  No other VMs on the 1st physical machine showed the same issue. Around here, networking sorta just works. Our network only has a few subnets, 5 switches and 3 routers, so it doesn't get very complex.

---

### Post by Mititelu_Radu on 2021-09-27
take a look at this MF
> radu@IT:~$ sudo tcpdump -tttt -n -i eno1 icmptcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eno1, link-type EN10MB (Ethernet), capture size 262144 bytes
2021-09-27 09:09:28.742648 IP 172.16.112.83 > 172.16.112.202: ICMP echo request, id 2, seq 190, length 64
2021-09-27 09:09:29.766762 IP 172.16.112.83 > 172.16.112.202: ICMP echo request, id 2, seq 191, length 64
2021-09-27 09:09:30.790768 IP 172.16.112.83 > 172.16.112.202: ICMP echo request, id 2, seq 192, length 64
2021-09-27 09:09:31.814706 IP 172.16.112.83 > 172.16.112.202: ICMP echo request, id 2, seq 193, length 64
^C
4 packets captured
5 packets received by filter
0 packets dropped by kernel
radu@IT:~$ sudo tcpdump -tttt -n -i eno1 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eno1, link-type EN10MB (Ethernet), capture size 262144 bytes
2021-09-27 09:10:29.414754 IP 172.16.112.83 > 172.16.112.1: ICMP echo request, id 3, seq 7, length 64
2021-09-27 09:10:29.414990 IP 172.16.112.1 > 172.16.112.83: ICMP echo reply, id 3, seq 7, length 64
2021-09-27 09:10:30.438782 IP 172.16.112.83 > 172.16.112.1: ICMP echo request, id 3, seq 8, length 64
2021-09-27 09:10:30.438977 IP 172.16.112.1 > 172.16.112.83: ICMP echo reply, id 3, seq 8, length 64
2021-09-27 09:10:31.462741 IP 172.16.112.83 > 172.16.112.1: ICMP echo request, id 3, seq 9, length 64
2021-09-27 09:10:31.462979 IP 172.16.112.1 > 172.16.112.83: ICMP echo reply, id 3, seq 9, length 64
^C
6 packets captured
6 packets received by filter
0 packets dropped by kernel
radu@IT:~$ sudo tcpdump -tttt -n -i eno1 icmp
[sudo] password for radu: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eno1, link-type EN10MB (Ethernet), capture size 262144 bytes
2021-09-27 11:52:49.649439 IP 172.16.112.202 > 172.16.112.83: ICMP echo request, id 4, seq 1, length 64
2021-09-27 11:52:49.649515 IP 172.16.112.83 > 172.16.112.202: ICMP echo reply, id 4, seq 1, length 64
2021-09-27 11:52:50.675168 IP 172.16.112.202 > 172.16.112.83: ICMP echo request, id 4, seq 2, length 64
2021-09-27 11:52:50.675244 IP 172.16.112.83 > 172.16.112.202: ICMP echo reply, id 4, seq 2, length 64
2021-09-27 11:52:51.699090 IP 172.16.112.202 > 172.16.112.83: ICMP echo request, id 4, seq 3, length 64



*83 is the client and *202 is the server. 
Do you know what happen between first and last command? I ping the client from server. Since Friday I was testing this and as soon as I send a ping packets from server to client, the client itself can connect to the server (ping, ssh, samba file share... everything works), for a random period of time, usually a few hours. I guess now I need to find a way to automatically run "ping  *.*.*.83 -c5" on server every hour. I could never imagine such an idiotic solution.

ps.
and crontab  - > 40 * * * * ping ***.***.***.83 -r7 did the job. Connection was down, min 40 came, client received the 7 ping  packets on the client and everything is back up. Again, completely retarded solution I know, but I really don't know what else to do.

---

### Post by TheFu on 2021-09-27
You probably don't need so many pings.
Some stateful firewalls, usually enterprise versions, will close connections that are open for a long time just to force reclaiming of resources.  Ran into this at work a long time ago.  We had thousands of client systems opening CORBA connections to some servers. All servers were in different network zones, based on the access needed.  Anyway, as part of a router upgrade, the "network guys" decided they would put a 24 hr limit for connections and force disconnect access.  We'd been running for a few years without any issues, until the Tuesday after the change happened. People generally turned off their machines over the weekend, but not nightly. On Tuesday morning, their connections would all be shutdown ... er ... 24 hours after they had made the connection on Monday morning.  It didn't happen to all users, since some logged off the system nightly.

You know how it is never really the network at fault?  This is 1 time where it was.

The change to the software to have it reconnect automatically 5 times in 5 minutes, with each additional attempt showing a stronger warning cost the project way too much and tool about a year to get.  We had to go pretty high up to get a waiver to have the router not disconnect connections every 24 hours.  A ping wouldn't have helped us. The routers were monitoring each connection - source, destination, port, protocol.

At another job, when WAN connections were over ISDN, the little company where I worked had 2 offices.  We setup a direct ISDN connection between the networks that could be made by either side, on-demand. There was a 5 minute time-out period and the long-distance phone call would be dropped.  One of the admins at the remote location decided that the 1sec delay for the connection to be made was too long and he setup a single ping every minute, 24/7/365.  The next month the corporate phone bill doubled.  The VP of operations was looking at the bill and noticed there was a very long phone call ... basically a month long between the satellite office and us ... $10K/month.  For a small company, that was a big deal.  I mentioned it to the admin on the other side that someone seemed to be working all night long and did they ever go home, since the office-to-office connection never dropped.  He sheepishly admitted to the ping and we worked out a deal where I'd get a VPN setup over the internet connections between our offices and he would limit the ping to be during business hours until that happened.  This was long before openvpn existed - so it was a commercial VPN product for a few $K.  Getting that cost approved was easy.  1-time cost (really for 3 yrs at a time) vs $10K/month for even 1 yr was a bargain.

Network costs are much different these days.  I use a ping script to keep track of uptime for the business network connection. 1 ping, every 2 minutes.  For last week, 
```
$ internet-up-summary.sh /var/log/internet-up.log.1.gz 
  Using /var/log/internet-up.log.1.gz ... 
  Using /tmp/internet-up.log.1
 ... 
 Period 20210919-062611  - 20210927-062411
  Total Time: 11520 (min) 192.00 (hrs)
  Percent Up Time: 99.93 % 
  Percent Down Time: 0.07 % 
  Total Down Time: 8 min or 0.13 hrs
 Currently: UP
  Removing /tmp/internet-up.log.1
```
I know exactly what the 8 minutes of down time was.  I was patching the WAN router.
2 weeks ago:
```
$ internet-up-summary.sh /var/log/internet-up.log.2.gz 
  Using /var/log/internet-up.log.2.gz ... 
  Using /tmp/internet-up.log.2
 ... 
 Period 20210913-062611  - 20210919-062411
  Total Time: 8640 (min) 144.00 (hrs)
  Percent Up Time: 100.00 % 
  Percent Down Time: 0.00 % 
  Total Down Time: 0 min or 0.00 hrs
 Currently: UP
  Removing /tmp/internet-up.log.2
```
I have 26 weekly logs, half a year, which has been useful to prove issues with the ISP.

---

