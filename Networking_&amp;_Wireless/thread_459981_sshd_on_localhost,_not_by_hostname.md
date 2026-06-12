---
title: "sshd on localhost, not by hostname"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by jdwinfodesign on 2007-05-31
I am wanting to set up file transfers between my laptop and desktop, similar to file transfers with my Web hosting provider. From my Feisty laptop and my Dapper desktop, I can log in and use the Nautilus file browser to connect and send files back and forth from my Web site.

However, not so easy between the two machines sitting next to each other. :)

I have sshd running on my desktop and can ssh localhost, but not by the hostname.

What do I need to do next?

---

### Post by jdwinfodesign on 2007-05-31
Turns out that my /etc/hosts file was wrong.

I edited to get:

127.0.0.1 localhost desktophostname
192.168.1.100 desktophostname
192.168.1.101 laptophostname

and can ssh from the same box, but now cannot ssh into the desktop from the laptop.

Clues would be appreciated.

---

### Post by jdwinfodesign on 2007-05-31
I can ssh to my server from the same box, but not from the laptop on the local area (wireless) network.

I am running a Linksys WRT54G with firewall enabled.

However, running nmap from the same box, I get:

jdw@jdw-desktop:~$ sudo nmap jdw-desktop
Password:

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-31 09:18 CDT
Warning: Hostname jdw-desktop resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 1694 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.135 seconds
jdw@jdw-desktop:~$ sudo nmap 192.168.1.100

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-31 09:18 CDT
All 1697 scanned ports on jdw-desktop (192.168.1.100) are closed
MAC Address: 00:0E:35:7D:A3:AF (Intel)

Nmap finished: 1 IP address (1 host up) scanned in 2.039 seconds


So, the ssh is open on the localhost (127.0.0.1) but not on jdw-desktop (the hostname of the box).

Also, I can ping localhost but can ping jdw-desktop (hostname of the box) only when the laptop is running.

Clues?

---

### Post by capn_hector on 2007-05-31
from your nmap scan your ssh damon is not running

---

### Post by jdwinfodesign on 2007-05-31
Actually, sshd is running. 

You can reach it on localhost (127.0.0.1) but not jdw-desktop (192.168.1.100)

jdw@jdw-desktop:~$ sudo nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-31 09:52 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1692 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
111/tcp open  rpcbind
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp


jdw@jdw-desktop:~$ sudo nmap 192.168.1.100 -p 22

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-31 09:50 CDT
Interesting ports on jdw-desktop (192.168.1.100):
PORT   STATE  SERVICE
22/tcp closed ssh

---

### Post by jdwinfodesign on 2007-05-31
Now I get this:

jdw@jdw-desktop:~$ sudo nmap 192.168.1.100

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-31 10:19 CDT
All 1697 scanned ports on jdw-desktop (192.168.1.100) are closed

But I can still ssh to localhost:

jdw@jdw-desktop:~$ ssh localhost
jdw@localhost's password:
Linux jdw-desktop 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

---

### Post by jdwinfodesign on 2007-05-31
Turns out it was the router. Evidently, it assigned my box a new IP address during a reboot that slipped my mind.

If anyone else sees this particular weirdness, just type 

$ ifconfig

and you will get something like the following.

jdw@jdw-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:64:C7:FC
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe64:c7fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:85738908 (81.7 MiB)  TX bytes:9409776 (8.9 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:685268 (669.2 KiB)  TX bytes:685268 (669.2 KiB)


In the first block of the response above, the " inet addr:192.168.1.101" should match the IP address you have in your /etc/hosts file. 

Mine did not, so I edited the hosts file:

127.0.0.1 localhost
192.168.1.101 jdw-desktop

And can ping and ssh from all boxes on my wireless network.

Until I reboot my desktop box again. Which should be a while considering it is running Ubuntu. ;)

---

