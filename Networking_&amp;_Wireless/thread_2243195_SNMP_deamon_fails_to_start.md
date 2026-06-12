---
title: "SNMP deamon fails to start"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2014-09-07
I've got this strange issue with SNMP. This is the first time I ever start the SNMP deamon on Linux and from what I've read - it should be a pretty straight forward procedure. So, I've installed the package and than configured it in /etc/snmp/snmpd.conf where I've only put the community string. 
It turned out though that the deamon fails to start.
@NUC-desktop:~$ sudo service snmpd restart
 * Restarting network management services:                                                                                   
@NUC-desktop:~$ sudo service snmpd status
 * snmpd is not running

When I force the deamon to start, I get an error that it cannot open UDP port 161... but nothing is running on port 161:
@NUC-desktop:~$ sudo /usr/sbin/snmpd -f
Turning on AgentX master support.
Error opening specified endpoint "udp:161"
Server Exiting with code 1

@NUC-desktop:~$ sudo nmap -sU localhost


Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2014-09-07 12:36 EEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000037s latency).
Not shown: 994 closed ports
PORT     STATE         SERVICE
68/udp   open|filtered dhcpc
123/udp  open          ntp
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
631/udp  open|filtered ipp
5353/udp open|filtered zeroconf


Nmap done: 1 IP address (1 host up) scanned in 3.60 seconds

I saw in some posts that there should be a log file for the snmpd in /var/log/snmpd.log. On my system such a file does not exist, how can I enable logging?

---

### Post by lz1dsb on 2014-09-11
Bump! Anyone? 
I am not able to find anything on that. It's really frustrating, SNMP configuration in Linux should be... well straight forward. What am I missing?

---

