---
title: "Can't connect to local computers"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by aurir_ on 2008-03-09
I got 3 computers, 1 running Ubuntu 7.1 and the other two running WindowsXP.

I used to run Fedora and I was able to remote log into my Windows XP computers using:

ssh -X username@192.168.1.144
or
ssh -X username@RouterExternalIP:portNum

When I try that on Ubuntu, the request is timing out.

Here's my ifconfig results for Ubuntu computer.
thekpr@thekpr-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:B9:39:DF  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:feb9:39df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9151362 (8.7 MB)  TX bytes:2820240 (2.6 MB)
          Interrupt:19 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3044 (2.9 KB)  TX bytes:3044 (2.9 KB)

---

### Post by Eiríkr on 2008-03-09
Aha -- Ubuntu actually doesn't come with sshd installed by default.  You need to install it yourself.  So either fire up Synaptic or apt-get and pull down the openssh-server package, and then you should be good to go.  

HTH,

Eiríkr

---

### Post by aurir_ on 2008-03-09
Still doesn't seem to work.

---

### Post by Eiríkr on 2008-03-09
Forgive me, I misunderstood your first post and was working backwards (from Windows to Ubuntu).  :-P  I've never tried ssh-ing from Ubuntu to Windows; what ssh server are you using on XP?  Presumably Cygwin?

---

### Post by aurir_ on 2008-03-09
I'm not using any server. I never have. What is that cgwin?

---

### Post by aurir_ on 2008-03-09
Ok, I installed ssh server that came with cygwin. Now I'm getting:

 port 22: Connection refused

It can't be the router cause I can ssh from Windows to Linux. It cannot be firewall on Windows machine cause it's deactivated. What else can be blocking the connection?

---

