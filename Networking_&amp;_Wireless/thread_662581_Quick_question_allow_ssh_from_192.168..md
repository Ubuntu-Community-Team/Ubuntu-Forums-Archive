---
title: "Quick question: allow ssh from 192.168.*"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by kikazaru on 2008-01-09
Sorry if this is an idiot question, but I have a desktop and a laptop running xubuntu 7.10 and ubuntu 7.10 respectively, connected through a wifi airstation. The desktop is a wired connection. 

I want to ssh from one to the other, but it is always denied. I tried adding:

ssh: 192.168. 

to my /etc/hosts.allow file, and eventually tried adding

ALL: ALL

to that file but always the ssh attempt fails, even when I try to ssh to the same computer. The IPs assigned are 192.168.11.3 and .4 respectively.

This is the denial message:

ssh: connect to host 192.168.11.3 port 22: Connection refused

I checked for ssh:

ps auwxx | grep ssh
kikazaru      6174  0.0  0.0   4436   544 ?        Ss   19:15   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4

---

### Post by njparton on 2008-01-09
Are the ports unblocked in iptables?

Are you connecting via a router/have you set up port forwarding if so?

---

### Post by kikazaru on 2008-01-09
How can I check if the ports are blocked and what should I do to unblock them? I'm not familiar with iptables, but -L seems to provide some information, or at least confirm a lack of settings perhaps..?

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

As for the connection I have an ADSL modem to which the airstation wireless router is connected, and one computer is has a wired connection to that, the other a wireless connection. 

I can successfully ping both machines, e.g.:

ping 192.168.11.4
PING 192.168.11.4 (192.168.11.4) 56(84) bytes of data.
64 bytes from 192.168.11.4: icmp_seq=1 ttl=64 time=0.679 ms
64 bytes from 192.168.11.4: icmp_seq=2 ttl=64 time=0.622 ms

ping 192.168.11.3
PING 192.168.11.3 (192.168.11.3) 56(84) bytes of data.
64 bytes from 192.168.11.3: icmp_seq=1 ttl=64 time=0.029 ms
64 bytes from 192.168.11.3: icmp_seq=2 ttl=64 time=0.033 ms

The latter is issued from the laptop to itself, the former from the laptop to the desktop.

I didn't configure port forwarding, maybe that's the problem..? Saying that, I have had the same problem when port forwarding definitely wasn't necessary.

---

### Post by jords on 2008-01-09
Hi

Try a Nmap, and see if it  sees an open ssh port.

Jordan

---

### Post by kikazaru on 2008-01-09
Thanks for the suggestion!

I guess there doesn't seem to be an open ssh port... any ideas why not? ssh-agent is running...

kikazaru@desktop:~$ nmap 192.168.11.4
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-09 21:41 JST
Interesting ports on 192.168.11.4:
Not shown: 1695 closed ports
PORT     STATE SERVICE
6000/tcp open  X11

Nmap finished: 1 IP address (1 host up) scanned in 13.194 seconds
kikazaru@desktop:~$ nmap 192.168.11.3

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-09 21:42 JST
Interesting ports on 192.168.11.3:
Not shown: 1694 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
902/tcp open  iss-realsecure-sensor

Nmap finished: 1 IP address (1 host up) scanned in 14.047 seconds

---

### Post by njparton on 2008-01-09
Either iptables (on which I'm not an expert) is blocking the port, or you need to forward it in your router.

---

### Post by heindsight on 2008-01-09
> **kikazaru said:**
> 
I checked for ssh:

ps auwxx | grep ssh
kikazaru      6174  0.0  0.0   4436   544 ?        Ss   19:15   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4
It appears you don't have sshd running. Do you have the openssh-server package installed?
If you do, then is sshd starting up at boot time (do you have S??sshd in /etc/rc2.d/)?

---

### Post by kikazaru on 2008-01-11
Superb, thanks for the answer! I needed to install openssh-server and also add something like 
ALL: 192.168.
to my /etc/hosts.allow files. Anyway, I could ssh to myself even without any changes to the hosts files so I knew installing openssh-server was an improvement right away. D'Oh!

Thanks for your help! (sorry for the slow reply, I was away and just got a chance to try your suggestion)

Incidentally, you wouldn't happen to know if there is an easy way to set up an internal disk, or a usb drive attached to a remote computer as if it were mounted locally? It seems intuitive that if you can ssh and scp to a remote drive then you have everything you need to mount it locally..?

---

### Post by heindsight on 2008-01-11
> **kikazaru said:**
> 
Incidentally, you wouldn't happen to know if there is an easy way to set up an internal disk, or a usb drive attached to a remote computer as if it were mounted locally? It seems intuitive that if you can ssh and scp to a remote drive then you have everything you need to mount it locally..?

Yes, have a look at sshfs (it's available in the Ubuntu repo's).

---

### Post by kikazaru on 2008-01-11
Most excellent! Thanks again.

---

