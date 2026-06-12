---
title: "Partial printing on wireless print server DPR-1260"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by bigams68 on 2008-05-28
Help! I am having trouble printing from Hardy 8.04 on my wireless print server D-Link DPR-1260 with an HP1410 printer connected.  When I print a test page or from Firefox, it prints part of the page and then stops like its waiting for more data to be sent. The print queue shows it is still printing.  I have looked through dozens of posts and all the suggestions so far have not helped.

Background:
I have the whole setup working for my XP machine.  I also can directly connect the printer to its USB with Hardy 8.04 and print correctly.  If I browse the print servers IP address, I get to it setup page seen below:

Server Name: 	 dlinkps-bd4026
IP Address: 	 192.168.0.10 (static)
MAC Address: 	 0015E9BD4026
Firmware: 	 1.00
USB Port 1: 	 HP PSC 1400 series
Printer Status:  Unplugged
Raw TCP port: 	 9100
LPR Queue Name:  PSC1400
Scanner: 	 No Scanner Detected

So... following advice from the link
[http://ubuntuforums.org/showthread.php?t=207005&highlight=Packetcat](http://ubuntuforums.org/showthread.php?t=207005&highlight=Packetcat)
I added the printer as follows:

Description: D-Link Wireless to HP PSC1410
Location: laptop-amschw
Device URI: lpd://192.168.0.10/PSC1400
Make and Model: HP PSC 1400 Foomatic/hpijs, hpijs 2.8.2
Printer Status: Idle
Default Printer: This is the default printer

One of the post talked about checking the ports on the print server so...

amschw@amschw-laptop:~$ nmap 192.168.0.10

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-05-28 00:08 EDT
Interesting ports on 192.168.0.10:
Not shown: 1711 closed ports
PORT     STATE SERVICE
80/tcp   open  http
515/tcp  open  printer
9100/tcp open  jetdirect

Nmap done: 1 IP address (1 host up) scanned in 8.835 seconds
amschw@amschw-laptop:~$ 


Any suggestions will be most appreciated?

---

### Post by bigams68 on 2008-05-28
After additional research, I believe this problem is a known bug in the kernel as represented by the debian and ubuntu links below.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478062](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=478062)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081)

I tried the below setting to disable FRTO, which it seems some have had success with... but not for me. I returned it back to Hardy's default setting of 2.
echo "0" > /proc/sys/net/ipv4/tcp_frto

I will keep watching for the kernel patch.

---

### Post by bigams68 on 2008-10-16
Solved...

So updating to "2.6.24-21-generic" seems to fix the problem.  I have only printed a few times, but so far it seems to print quickly and completely.

This fix is also reflected in ubuntu's launchpad below.
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/213081](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/213081)

---

