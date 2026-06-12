---
title: "Can't open any ports"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by ricky_buntu on 2015-08-17
hello I'm hoping someone can help me. I've tried a bunch of solutions but nothing has worked. I recently upgraded Ubuntu from 12.04 to 14.04 and since then I've been unable to open any of my ports. The port I'm trying to open is 49995.
I've tried: 
[LIST]
[*]Allowing the ports in UFW 
[*]Adding the ports to iptables 
[*]Adding the ports to NAT tables 
[*]Flushing the iptables and starting from scratch 
[*]Turning off my UFW 
[/LIST]

sudo netstat -tulpn gives me

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1127/smbd       
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1885/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      14224/cupsd     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1127/smbd       
tcp6       0      0 10.1.1.10:49995         :::*                    LISTEN      16635/java      
tcp6       0      0 :::139                  :::*                    LISTEN      1127/smbd       
tcp6       0      0 127.0.0.1:45100         :::*                    LISTEN      16635/java      
tcp6       0      0 ::1:631                 :::*                    LISTEN      14224/cupsd     
tcp6       0      0 :::445                  :::*                    LISTEN      1127/smbd       
tcp6       0      0 127.0.0.1:6880          :::*                    LISTEN      16635/java      
tcp6       0      0 127.0.0.1:32874         :::*                    LISTEN      16635/java      
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1885/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1869/dhclient   
udp        0      0 192.168.0.255:137       0.0.0.0:*                           2026/nmbd       
udp        0      0 192.168.0.20:137        0.0.0.0:*                           2026/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           2026/nmbd       
udp        0      0 192.168.0.255:138       0.0.0.0:*                           2026/nmbd       
udp        0      0 192.168.0.20:138        0.0.0.0:*                           2026/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           2026/nmbd       
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1625/cups-browsed
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3027/chromium-brows
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1476/avahi-daemon: 
udp        0      0 0.0.0.0:43288           0.0.0.0:*                           1476/avahi-daemon: 
udp        0      0 0.0.0.0:35446           0.0.0.0:*                           1869/dhclient   
udp6       0      0 :::56662                :::*                                1476/avahi-daemon: 
udp6       0      0 10.1.1.10:36945         :::*                                16635/java      
udp6       0      0 :::16680                :::*                                16635/java      
udp6       0      0 :::16680                :::*                                16635/java      
udp6       0      0 192.168.0.20:33235      :::*                                16635/java      
udp6       0      0 10.1.1.10:33235         :::*                                16635/java      
udp6       0      0 10.1.1.10:49995         :::*                                16635/java      
udp6       0      0 :::5353                 :::*                                1476/avahi-daemon: 
udp6       0      0 :::21908                :::*                                1869/dhclient   
udp6       0      0 192.168.0.20:46872      :::*                                16635/java      
udp6       0      0 10.1.1.10:46872         :::*                                16635/java      
udp6       0      0 :::1900                 :::*                                16635/java      
udp6       0      0 :::1900                 :::*                                16635/java      

```

sudo iptables -t nat -L -nv gives me
```

Chain PREROUTING (policy ACCEPT 122K packets, 15M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 19772 packets, 5662K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    1    76 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:49995
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:49995

Chain OUTPUT (policy ACCEPT 449K packets, 40M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 449K packets, 40M bytes)
 pkts bytes target     prot opt in     out     source               destination  

```

sudo ufw status shows

```

Status: active

To                         Action      From
--                         ------      ----
139/tcp                    ALLOW       Anywhere
445/tcp                    ALLOW       Anywhere
137/udp                    ALLOW       Anywhere
138/udp                    ALLOW       Anywhere
5964                       ALLOW       Anywhere
59/udp                     ALLOW       Anywhere
5/tcp                      ALLOW       Anywhere
49995                      ALLOW       Anywhere (log-all)
139/tcp (v6)               ALLOW       Anywhere (v6)
445/tcp (v6)               ALLOW       Anywhere (v6)
137/udp (v6)               ALLOW       Anywhere (v6)
138/udp (v6)               ALLOW       Anywhere (v6)
5964 (v6)                  ALLOW       Anywhere (v6)
59/udp (v6)                ALLOW       Anywhere (v6)
5/tcp (v6)                 ALLOW       Anywhere (v6)
::ffff:10.1.1.14 5964/tcp on ppp0 ALLOW       Anywhere (v6)
::ffff:10.1.1.14 5964/udp on ppp0 ALLOW       Anywhere (v6)
49995 (v6)                 ALLOW       Anywhere (v6) (log-all)

137/udp                    ALLOW OUT   Anywhere
138/udp                    ALLOW OUT   Anywhere
139/tcp                    ALLOW OUT   Anywhere
445/tcp                    ALLOW OUT   Anywhere
5964                       ALLOW OUT   Anywhere
59/udp                     ALLOW OUT   Anywhere
5/tcp                      ALLOW OUT   Anywhere
49995                      ALLOW OUT   Anywhere (log-all)
137/udp (v6)               ALLOW OUT   Anywhere (v6)
138/udp (v6)               ALLOW OUT   Anywhere (v6)
139/tcp (v6)               ALLOW OUT   Anywhere (v6)
445/tcp (v6)               ALLOW OUT   Anywhere (v6)
5964 (v6)                  ALLOW OUT   Anywhere (v6)
59/udp (v6)                ALLOW OUT   Anywhere (v6)
5/tcp (v6)                 ALLOW OUT   Anywhere (v6)
::ffff:10.1.1.14 5964/tcp  ALLOW OUT   Anywhere (v6) on ppp0
::ffff:10.1.1.14 5964/udp  ALLOW OUT   Anywhere (v6) on ppp0
49995 (v6)                 ALLOW OUT   Anywhere (v6) (log-all)

```

telnet localhost gives me

```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

telnet localhost 49995 gives me

```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

The software I'm running uses UPnP and can confirm that the port is being forwarded in on my router.
Can anyone help me figure this out?

---

### Post by TheFu on 2015-08-18
If you aren't using IPv6 for anything, might be easiest to disable it. That might get the java process to use IPv4 instead.
Looks like there is a java program listening on IPv6 on the port you want, not on IPv4. It seems tied to a 10.x.x.x IP too, which doesn't make sense either. There is probably a setting in some XML file for that program to control which network interface it should listen on.  If you connect with IPv6, it might work.

I don't think the firewall has anything to do with this.

---

### Post by ricky_buntu on 2015-08-18
Thanks for the reply. There is a setting in the software that I'm using that switches between IPv4 and IPv6. I can't remember what it's set to. When I get home I will try changing it. If that does not work I'll try disabling IPv6.

---

### Post by ricky_buntu on 2015-08-19
The software was using IPv6. I forced it to use IPv4 and disabled IPv6. Unfortunately I was still unable to open the port. I thought maybe my ISP was blocking the ports. As an experiment I installed the same software on one of my windows 7 machines and it worked fine. So this is an issue with Ubuntu. Any other suggestions?

---

### Post by ian-weisser on 2015-08-19
Here's a super-simple test using the 'netcat' tool:

Disable that java software using port 49995. You need the port free...or simply use a different port number.

Open TWO terminal windows side-by-side.

In the first terminal window, open a process to listen on the port (sudo not needed):
```
nc -l 49995
```

In the second terminal window, try to connect to that listener (sudo still not needed):
```
nc localhost 49995
```

Try sending a 'hello there' message each way (just type it in each window). If it works, then the firewall and ports are working properly.

---

### Post by TheFu on 2015-08-19
Good idea Ian!  I think it is the java config, but facts are better than guessing.

---

### Post by ricky_buntu on 2015-08-20
> **ian-weisser said:**
> Here's a super-simple test using the 'netcat' tool:

Disable that java software using port 49995. You need the port free...or simply use a different port number.

Open TWO terminal windows side-by-side.

In the first terminal window, open a process to listen on the port (sudo not needed):
```
nc -l 49995
```

In the second terminal window, try to connect to that listener (sudo still not needed):
```
nc localhost 49995
```

Try sending a 'hello there' message each way (just type it in each window). If it works, then the firewall and ports are working properly.

Thank you for your reply. The nc command worked. I was able to type a message in one terminal and see it appear in the next. Since nc worked I tried some none java based software that needs a port to work and had the same issues. I also downgraded the java software I was using but the port was still not open to the outside.

---

### Post by ricky_buntu on 2015-08-30
Well it looks like there is no help to be had with this. I guess it's time to look into reinstalling and/or using a more stable distro.

---

### Post by ian-weisser on 2015-08-30
Well, you did seem to show that there was nothing wrong with Ubuntu. Your ports worked, you could connect to them on localhost, and your firewall rules allowed external connections on that port.

Did you try connecting to the test (netcat) from another machine on that port?

Sorry your Java application doesn't seem to work.

---

### Post by TheFu on 2015-08-30
> **ricky_buntu said:**
> Well it looks like there is no help to be had with this. I guess it's time to look into reinstalling and/or using a more stable distro.

What?  The issue is with the java app - either the app or the configuration the app. That is NOT an ubuntu issue and you will probably run into the same AND other issues with a different distro.

At this point, asking for help from the team who created the java app is recommended.  I have a few java network applications running - haven't seen the issue you are experiencing. These are tomcat based and fortunately, I don't need to know the details. The installation program setup everything for me.

---

### Post by ricky_buntu on 2015-08-31
I think the problem is either Ubuntu or Java. I decided to try  installing the same software on one of my other Ubuntu machines and it  worked without editing the iptables. I also tried to run non Java based software and the ports remain closed to the outside. Everything works fine on my other machine. I've also been getting nondescript errors when Ubuntu starts up. My best guess is the update broke/misconfigured something.

---

### Post by ricky_buntu on 2015-08-31
> **ian-weisser said:**
> Well, you did seem to show that there was nothing wrong with Ubuntu. Your ports worked, you could connect to them on localhost, and your firewall rules allowed external connections on that port.

Did you try connecting to the test (netcat) from another machine on that port?

Sorry your Java application doesn't seem to work.

Netcat works from machine to machine. I also tried ```
python -m SimpleHTTPServer
``` and it works on my local network as well.

---

### Post by ian-weisser on 2015-08-31
Good test.
You seem to have conclusively demonstrated that nothing is wrong with your Ubuntu system, ports, or firewall.
You are able to run a test server and connect via local host, and connect from another machine through your firewall.
Well done.

Seems like the only piece of the puzzle remaining is your Java application, whatever it is.

---

### Post by ricky_buntu on 2015-08-31
> **ian-weisser said:**
> Good test.
You seem to have conclusively demonstrated that nothing is wrong with your Ubuntu system, ports, or firewall.
You are able to run a test server and connect via local host, and connect from another machine through your firewall.
Well done.

Seems like the only piece of the puzzle remaining is your Java application, whatever it is.

Well I think I've demonstrated the I can connect within my local network. Unfortunately this does help since I need the ports open outside of my network. I'm able to connect using the same version of the software and Ubuntu on my other machines **without any extra steps**. Just install and run. On this machine I'm unable to connect after uninstalling the software, deleting the user settings and reinstalling. **I've tried other software that is not Java based** **and I've been unable to connect to the computer from outside my network. **To me this suggests that the update broke something.

---

### Post by ricky_buntu on 2015-08-31
I think I've spent way too much time trying to get this to work. When I  have some time and I figure out all the software, commands and setting I  need I'll do a clean install. This time I'll reformat my home partition  which I hate doing. This is why I dread updating Ubuntu and stayed on  12.04 for so long. With Ubuntu updating always carries the risk of  breaking something in subtle and hard to troubleshoot ways.

Anyway  thanks for the help you guys. I learned some new things. I wish I did  not have to do a clean install but I've done it before and I'll probably  have to do it again.

---

### Post by ian-weisser on 2015-09-01
> **ricky_buntu said:**
> Well I think I've demonstrated the I can connect within my local network. Unfortunately this does help since I need the ports open outside of my network.

Your upstream router, not your Ubuntu system, controls access from the internet to your LAN.
Look at your upstream router's firewall.

---

### Post by The Cog on 2015-09-01
The Fu's suggestion with nc only tested local connections (localhost). 
Firewalls often have special clauses that allow local connections even when connections from other machines are disallowed. 
I would be inclined to run ```
sudo tcpdump -np tcp port 49995
``` and see if the connection request even reaches the server, and how the server responds.

I fail to see how changing to a different distro will fix things unless doing so ends up configuring different firewall rules. And changing distros because you haven't configured the firewall properly on the first one is not the best of reasons to change.

Incidentally, although I'm not familiar with ufw rules, it looks to me in post #1 that port 49995 is allowed to make outgoing connections on IPv6 only, and not allowed incoming connections at all. Try sudo ufw ```
disable
``` for a few minutes to see if it is the firewall that's stopping things.

---

### Post by ricky_buntu on 2015-09-01
> **ian-weisser said:**
> Your upstream router, not your Ubuntu system, controls access from the internet to your LAN.
Look at your upstream router's firewall.

It's not my router. Tested with all of firewalls hard and soft turned off. And my other machines work fine.

---

### Post by ricky_buntu on 2015-09-01
> **The Cog said:**
> The Fu's suggestion with nc only tested local connections (localhost). 
Firewalls often have special clauses that allow local connections even when connections from other machines are disallowed. 
I would be inclined to run ```
sudo tcpdump -np tcp port 49995
``` and see if the connection request even reaches the server, and how the server responds.

I fail to see how changing to a different distro will fix things unless doing so ends up configuring different firewall rules. And changing distros because you haven't configured the firewall properly on the first one is not the best of reasons to change.

Incidentally, although I'm not familiar with ufw rules, it looks to me in post #1 that port 49995 is allowed to make outgoing connections on IPv6 only, and not allowed incoming connections at all. Try ```
sudo ufw disable
``` for a few minutes to see if it is the firewall that's stopping things.

Hello the Cog and thank you for your reply. local machines can connect but not external ones. I testes with all of my firewalls turned off and IPv6 disabled. I'm at the point were I'm most likely going to do a fresh reinstall. I'm 99% sure the update from 12.04 to 14.04 hosed my system.

---

### Post by ricky_buntu on 2015-09-01
I pretty sure the update from 12.04 to 14.04 broke some things. I only started making modifications to the iptables and ufw after my software could not connect properly. My router is working fine. I've tested on other machines with no issues and testing similar non-java software on this machine produce the same connection issues. In addition to this I just tested from the 14.04 installation cd on this machine and the software worked with no issues. Looks like I know how I'm going to be spending part of the holiday weekend, LOL. Thanks again for the help guys. I wish it was a simple fix.

---

### Post by ian-weisser on 2015-09-01
> **ricky_buntu said:**
> My router is working fine. I've tested on other machines with no issues and testing similar non-java software on this machine produce the same connection issues. In addition to this I just tested from the 14.04 installation cd on this machine and the software worked with no issues.

Good troubleshooting!

---

