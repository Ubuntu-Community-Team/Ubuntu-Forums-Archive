---
title: "pppd ip-up.d scripts not running"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by tomroffe on 2007-05-22
Hi All

I'm using Ubuntu server 7.04 with a Speedtouch 330 ADSL modem, I can connect and get a working connection and manually run my iptables script but i can not get pppd to run my script located in /etc/ppp/ip-up.d/ after it brings up my connection on boot.

i have set the file permission of this script to 700 and is owned by root. the script that runs is simple and like say can be run manually from the command line.


```
#!/bin/sh

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables-restore < /etc/network/iptables.up.rules
```

Aim i missing something hear. The man pages say this is the right place, and i think the other scripts in the ip-up.d directory are being executed, namely 0000usepeerdns 0dns-up or i would not get my DNS server address in resolv.conf

i done some searching and found an example iptables script distributed from the debian site [http://ftp.debian.org/doc/iptables/examples/3iptables-ppp_ip-rules](http://ftp.debian.org/doc/iptables/examples/3iptables-ppp_ip-rules) which usally lives @ /usr/share/doc/iptables/examples/3iptables-ppp_up-rules.gz this dose not seem to be invcluded in unbunu ppp package but if i place it in ip-up.d anyway and jig the iptables to suit me and run pppd still no go, the permissions are the same as 0000usepeerdns etc

Can anyone help

Tom

---

### Post by tomroffe on 2007-05-22
sorry that links dead try this [http://arthur.barton.de/cgi-bin/dwww?type=file&location=/usr/share/doc/iptables/examples/3iptables-ppp_up-rules.gz](http://arthur.barton.de/cgi-bin/dwww?type=file&location=/usr/share/doc/iptables/examples/3iptables-ppp_up-rules.gz)

---

### Post by kvonb on 2007-05-22
This might be a silly question, but is the script file marked as executable?

Try sudo chmod +x on it.

I use the Firestarter firewall and pppoe.  Firestarter has an option for starting the firewall on dial out, maybe have a look at that.

I also use a util called gpppon which is a GUI frontend to pppoe if that is of any interest to you :)

---

### Post by tomroffe on 2007-05-22
yes the file has the execute permission and is owned by root, the ppp faq requirmends 700 but i've tryed 755 (full root access, plus read and execute bit for user and group). 
also this is running ubuntu server 7.04 so X and Gnome are not installed.

---

### Post by bdk6m2007 on 2008-02-01
Did you ever figure out why the script was not running?  I'm running into the same thing (except now it's Ubuntu Server 7.10)......

---

