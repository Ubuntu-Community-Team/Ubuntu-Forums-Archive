---
title: "internet randomly completely died"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by hamiltonstal on 2007-03-26
My internet just stopped loading. I have a working connection because i am on my other computer with the same cord plugged into it. I have ubuntu edgy on my laptop. Last night i installed jedit and java and everything was working fine. I turned off my computer woke up this morning turned it back on -> everything still working fine, i checked my email etc. Turn off my computer go to class, come home and turn it back on, firefox will not connect any more. It just says "loading google.com" at the bottom. There is no reason for it to randomly stop working. I cant tell you how unconvient this is, i am about to just re-install xp pro on it again. Any ideas? I have been trying to fix it for the last 2.5 hours.

---

### Post by moogman on 2007-03-26
Hi there. Can you open a terminal (Applications->Accessories->Terminal), and give the output of the following five commands:

ping google.com
host google.com
ping 72.14.207.99
cat /etc/resolv.conf
route -n
ifconfig


Hopefully we'll be able to help you out from there!

---

### Post by hamiltonstal on 2007-03-26
it looked something like this: ->



w-stallings@V2000z:~$ ping google.com
ping: unknown host google.com
w-stallings@V2000z:~$ host google.com
;; connection timed out; no servers could be reached
w-stallings@V2000z:~$ ping 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
cat /etc/resolv.conf
--- 72.14.207.99 ping statistics --
96 packets transmitted, 0 received, 100% packet loss, time 95005ms
w-stallings@V2000z:~$ cat /etc/resolv.conf
search Belkin
nameserver 192.168.2.1
w-stallings@V2000z:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref  Use   Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0      0   
eth0
0.0.0.0  192.168.2.1  0.0.0.0         UG    0      0        0 
eth0

w-stallings@V2000z:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:BD:8B:27  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0        inet6 addr: fe80::2c0:9fff:febd:8b27/64 Scope:Link
  
        UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1    
     RX packets:722 errors:0 dropped:0 overruns:0 frame:0        TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
   
       collisions:0 txqueuelen:1000      RX bytes:72619 (70.9 KiB)  TX bytes:14902 (14.5 KiB)  
    Interrupt:201 Base address:0x2000 
lo        Link encap:Local Loopback  
     inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
       RX packets:2 errors:0 dropped:0 overruns:0 frame:0
        TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
w-stallings@V2000z:~$

---

### Post by moogman on 2007-03-26
Can you try this further command:

ping 192.168.2.1

It looks like your machine can't access your router. The above command will be able to confirm this.

Is 192.168.2.1 the address of your home router?

---

### Post by hamiltonstal on 2007-03-26
it still said 100% packet loss, however i live in an appartment complex and usually i will start up the internet and it will immediately take me to a login screen where i log in and am free to surf. Otherwise i just plug the ethernet cord straight into the laptop. About 3 months ago this same thing happened and i restarted my computer and it worked again. I also was using Opera at the time, i tried to download opera and transfer it to my laptop but it had too many dependecies that i didnt want to figure out how to get.

---

### Post by Austin_KW on 2007-03-26
Can you still ping the default gateway 'ping 192.168.2.1'

try disabling ipv6
change to 'alias net-pf-10 off #ipv6' in /etc/modprobe.d/aliases & reboot

---

### Post by hamiltonstal on 2007-03-26
i cannot ping 192.168.2.1, it still says 100% packet loss.

I disabled ipv6 and that did not solve the problem.

I dont understand how it can immediately stop working so randomly without me changing anything at all. Could it be a firefox problem? Is there any way for me to install another browser that doesnt depend on a lot of extra dependencies?

---

### Post by Austin_KW on 2007-03-26
It is not firefox, you cannot even get to your local network gateway if ping 192.168.2.1 is failing

---

### Post by Austin_KW on 2007-03-26
Are you using dhcp? no way you configured static addresses/routes?
cat /etc/network/interfaces

---

### Post by hamiltonstal on 2007-03-26
they all say 'dhcp' except 'lo' which says 'iface lo inet loopback'. And i have never changed anything about connecting to anything. Since day one i just installed ubuntu and plugged in the cord and it worked. The network connection icon on the topright of the screen right by my battery meter has always said 'lo'. And like i said, this morning i checked my email and facebook with no problems. The only thing i have done since it was working until failure was shut down my computer and start up again.

---

### Post by hamiltonstal on 2007-03-26
also when i usually start up firefox it will go straight to the log in screen. But if i try to open 'gaim' or mozilla thunderbird it will fail until i log in.

---

### Post by Mr. C. on 2007-03-26
> **hamiltonstal said:**
> ...usually i will start up the internet and it will immediately take me to a login screen where i log in and am free to surf... 
 
This sounds like your apartment's internet service uses a captive portal, where you must bring up your browser to sign-in, and then once authenticated, you receive a new IP address.  This must be done uniquely for each computer.
 
If this is the case, then you must open a browser to allow authentication to occur.
 
If I'm understanding "I have a working connection because i am on my other computer with the same cord plugged into it" correctly, you are saying that you unplug the Ethernet cable from the Ubuntu system and plug it into the (Windows?) system, and that works?  If so... don't do this.  The captive portal remembers your MAC address (the hardware address of your Ethernet card), and allocates the IP information based on that.  Change network cards creates problems, and your Ubuntu system's ethernet card will not be authenticated.

There is nothing "random" about this.

I suppose you do not have your own router/firewall/NATing device?

MrC

---

### Post by Austin_KW on 2007-03-26
Very odd, eth0 gets its dhcp config from the router and then you cant use it. What happens if you try to get the configurion again?
 sudo ifdown eth0
 sudo ifup eth0

---

### Post by hamiltonstal on 2007-03-26
Austin_KW my internet is now working again! I did both of those commands. Thank you very much.

Mr. C ->To prevent this in the future.. Should i never switch back and forth ethernet cords to the seperate machines? And no i do not have my own router/etc..

---

### Post by Mr. C. on 2007-03-26
Without knowing your apartments setup, I can't say for sure.  I can only tell you that captive portals associate a MAC address with and IP address, and use a proxy service.

If you are going to use multiple computers, get yourself a cheap router/NAT box, that allows you to plug in all systems at the same time.  This will help mitigate this problem.

MrC

---

