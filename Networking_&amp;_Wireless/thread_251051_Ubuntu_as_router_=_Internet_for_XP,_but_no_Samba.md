---
title: "Ubuntu as router = Internet for XP, but no Samba"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by austin987 on 2006-09-04
I recently configured Ubuntu to run as a dhcp server for my xp box. Ubuntu also houses my TB raid, which should be shared over either ftp or samba to the xp box. However, when trying to connect through any sort of protocol (other than pinging) between the two boxes, the connection fails. Config:

Ubuntu Box (192.168.0.1)
Eth0 --> Crossover cable --> XP
Eth1 --> Modem (Dorm internet connection)

XP Box(192.168.0.200)
XP can ping ubuntu, and vice-versa

Both can reach the internet, and various services.

When trying to connect via SSH/FTP/Samba into Ubuntu from XP, connection fails.

[Guide Used]("http://ubuntuguide.org/wiki/Dapper#How_to_install_DHCP_Server_for_automatic_IP_addresses_assignment")

Any advice would be appreciated.

---

### Post by Iowan on 2006-09-05
Assuming you have the server component of Samba installed, do you have username and password added from smbpasswd?
[HERE]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=smbpasswd") is one how-to for Samba.

---

### Post by darrenm on 2006-09-05
Can you nmap the Ubuntu box from the Windows box then nmap localhost from the Ubuntu box and post what comes back?

---

### Post by austin987 on 2006-09-05
added user in administration/users and groups, as well as sudo smbpasswd -a user_name

as for nmap, not quite sure what that means. I'm assuming you mean mount the network drive, and when I try to do so (from xp), it gets as far as browsing the workgroup (MSHOME), sees the pc, but when trying to open it, saying I don't have permission. My username and pass are in the ubuntu box, and in addition, I've tried setting up anonymous access, with no authentication required for read and write. Even that didn't work. Which says to me that its not a Samba issue, but some sort of networking issue (related to the Ubuntu box being on two different networks at the same time?).

---

### Post by darrenm on 2006-09-05
[http://www.google.co.uk/search?hl=en&q=nmap&btnG=Google+Search&meta=](http://www.google.co.uk/search?hl=en&q=nmap&btnG=Google+Search&meta=) ;)

Just run nmap on your command line and see what happens :)

---

### Post by austin987 on 2006-09-05
From XP:

Microsoft Windows [Version 5.2.3790]
(C) Copyright 1985-2003 Microsoft Corp.

D:\Documents and Settings\Administrator>nmap 192.168.0.1

Starting Nmap 4.11 ( [http://www.insecure.org/nmap](http://www.insecure.org/nmap) ) at 2006-09-05 17:57 Central
Daylight Time
dnet: Failed to open device eth0
QUITTING!

---

### Post by austin987 on 2006-09-05
From Ubuntu

austin@white-house:~$ nmap 192.168.0.200

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-09-05 17:51 CDTInteresting ports on 192.168.0.200:
(The 1670 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1025/tcp open  NFS-or-IIS

---

### Post by darrenm on 2006-09-05
Did you use the full windows nmap installer with winpcap?

Also. do nmap localhost on the ubuntu machine.

---

### Post by austin987 on 2006-09-05
Yes, used the full installer and it was installed/run with administrator rights.

austin@white-house:~$ nmap localhost

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-09-05 19:02 CDTInteresting ports on localhost.localdomain (127.0.0.1):
(The 1671 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.332 seconds

---

### Post by darrenm on 2006-09-06
So what does Windows (putty) say exactly when you SSH to the Linux box from the Windows box?

---

### Post by austin987 on 2006-09-06
"Network error: Connection timed out."

---

### Post by jdong on 2006-09-06
I suspect somehow you have your ubuntu router's firewall configured to block connection attempts from your LAN.

---

### Post by tbonius on 2006-09-06
First off.. you seem to have connectivity to your Ubuntu machine.. try pinging it from the WIndows computer.

```
ping ip-address-of-ubuntu-computer
```

you should get replies. if you dont.. that is your first issue.  Double check your network settings on your ubuntu machine.  Things like verifying the internal IP address.. and make sure there is no default gateway configured for both interfaces.

The next step is to verify SSH connectivity to your ubuntu box.  Open a cmd prompt on your Windows box and telnet to the Ubuntu computer on the ssh port of 22

```
telnet ip-address-of-ubuntu-computer 22
```

You should see a reply like this:

```
SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4.1

```
Something similar anyways.. depending on your distribution.  Next.. verify that Putty is in fact using the SSH protocol and not telnet.. and also make sure that you are configured to use the correct port (I am assuming default port of 22).  Also make sure you have put in the correct IP address under the "Hostname (Or IP address)" section.

Once you have verified this.. save the Putty session.

You should be able to SSH into your Ubuntu computer.

Now you need to open up a share with Samba.

Move your /etc/samba/smb.conf file to /etc/samba/smb.conf.old and edit a new file called /etc/samba/smb.conf.  Make it look something like this:

```
[global]
        workgroup = WORKGROUP
        server string = Ubuntu
        interfaces = 192.168.0.0/24
        bind interfaces only = Yes
        security = SHARE
        preferred master = No
        local master = No
        domain master = No
        
[Share]
        path = /share
        read only = No
        guest ok = Yes
```

Assuming that you have a /share directory created.. and that you have "chmodded" it to allow write access for the user "nobody" under which samba runs.```


sudo chmod 777 /share
```

Now simply restart samba

```
sudo /etc/init.d/samba restart
```

And broswe to the IP address or NetBIOS name of the Ubuntu computer

Start -> Run -> \\ubuntu

You should see your SMB share.

T

---

### Post by austin987 on 2006-09-06
Microsoft Windows [Version 5.2.3790]
(C) Copyright 1985-2003 Microsoft Corp.

D:\Documents and Settings\Administrator>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:

Reply from 192.168.0.1: bytes=32 time<1ms TTL=64
Reply from 192.168.0.1: bytes=32 time<1ms TTL=64
Reply from 192.168.0.1: bytes=32 time<1ms TTL=64

Ping statistics for 192.168.0.1:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
Control-C
^C
D:\Documents and Settings\Administrator>telnet 192.168.0.1 22
Connecting To 192.168.0.1...Could not open connection to the host, on port 22: C
onnect failed

Ping works, telnet/ssh doesn't. Does seem like a firewall issue, though no firewall is setup on the ubuntu machine yet. What makes me think that it is a networking/firewall issue is that the XP machine can see the Ubuntu when browsing the network, but can't connect. Ubuntu fails when attempting to browse the network.

Ubuntu can ping XP as well, but when attempting to connect through ftp/ssh/samba, it fails.

XP's default gateway is 192.168.0.1, Ubuntu doesn't have one set on eth0 (lan connection), and eth1 (internet connection) is configured by DHCP.

Could the dhcp3-server config be an issue here?

---

### Post by jdong on 2006-09-06
What are the iptables/shorewall rules you're using? Definitely you have a firewall set if you're using your Ubuntu machine as a router.

---

### Post by austin987 on 2006-09-06
> **jdong said:**
> What are the iptables/shorewall rules you're using? Definitely you have a firewall set if you're using your Ubuntu machine as a router.

```
# Generated by iptables-save v1.3.3 on Wed Sep  6 20:40:34 2006
*mangle
:PREROUTING ACCEPT [8407443:1933440574]
:INPUT ACCEPT [5409299:335107925]
:FORWARD ACCEPT [2976107:1596086719]
:OUTPUT ACCEPT [8593224:12618376965]
:POSTROUTING ACCEPT [11570734:14214844338]
COMMIT
# Completed on Wed Sep  6 20:40:34 2006
# Generated by iptables-save v1.3.3 on Wed Sep  6 20:40:34 2006
*nat
:PREROUTING ACCEPT [1250510:163528886]
:POSTROUTING ACCEPT [6372:584321]
:OUTPUT ACCEPT [10814:1165262]
-A POSTROUTING -o eth1 -j MASQUERADE 
COMMIT
# Completed on Wed Sep  6 20:40:34 2006
# Generated by iptables-save v1.3.3 on Wed Sep  6 20:40:34 2006
*filter
:INBOUND - [0:0]
:INPUT DROP [20:6673]
:FORWARD DROP [602:33712]
:LOG_FILTER - [0:0]
:LSI - [0:0]
:LSO - [0:0]
:NR - [0:0]
:OUTBOUND - [0:0]
:OUTPUT DROP [0:0]
-A INBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INBOUND -j LSI 
-A INPUT -s 128.194.254.1 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
-A INPUT -s 128.194.254.1 -p udp -j ACCEPT 
-A INPUT -s 128.194.254.2 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
-A INPUT -s 128.194.254.2 -p udp -j ACCEPT 
-A INPUT -s 128.194.254.3 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -j ACCEPT 
-A INPUT -s 128.194.254.3 -p udp -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
-A INPUT -p icmp -m limit --limit 10/sec -j ACCEPT 
-A INPUT -s ! 128.194.52.0/255.255.254.0 -i eth1 -j NR 
-A INPUT -d 255.255.255.255 -i eth1 -j DROP 
-A INPUT -d 128.194.53.255 -j DROP 
-A INPUT -s 224.0.0.0/255.0.0.0 -j DROP 
-A INPUT -d 224.0.0.0/255.0.0.0 -j DROP 
-A INPUT -s 255.255.255.255 -j DROP 
-A INPUT -d 0.0.0.0 -j DROP 
-A INPUT -m state --state INVALID -j DROP 
-A INPUT -f -m limit --limit 10/min -j LSI 
-A INPUT -i eth1 -j INBOUND 
-A INPUT -d 192.168.0.1 -i eth0 -j INBOUND 
-A INPUT -d 128.194.53.223 -i eth0 -j INBOUND 
-A INPUT -d 192.168.0.255 -i eth0 -j INBOUND 
-A INPUT -j LOG_FILTER 
-A INPUT -j LOG --log-prefix "Unknown Input" --log-level 6 
-A FORWARD -p icmp -m limit --limit 10/sec -j ACCEPT 
-A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu 
-A FORWARD -i eth0 -j OUTBOUND 
-A FORWARD -d 192.168.0.0/255.255.255.0 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -d 192.168.0.0/255.255.255.0 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -j LOG_FILTER 
-A FORWARD -j LOG --log-prefix "Unknown Forward" --log-level 6 
-A LSI -j LOG_FILTER 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j DROP 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -j DROP 
-A LSI -p icmp -m icmp --icmp-type 8 -m limit --limit 1/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -p icmp -m icmp --icmp-type 8 -j DROP 
-A LSI -m limit --limit 5/sec -j LOG --log-prefix "Inbound " --log-level 6 
-A LSI -j DROP 
-A LSO -j LOG_FILTER 
-A LSO -m limit --limit 5/sec -j LOG --log-prefix "Outbound " --log-level 6 
-A LSO -j REJECT --reject-with icmp-port-unreachable 
-A NR -s 0.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 1.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 2.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 5.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 7.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 10.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 23.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 27.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 31.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 36.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 37.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 39.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 41.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 42.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 49.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 50.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 73.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 74.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 75.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 76.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 77.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 78.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 79.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 89.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 90.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 91.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 92.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 93.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 94.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 95.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 96.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 97.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 98.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 99.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 100.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 101.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 102.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 103.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 104.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 105.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 106.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 107.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 108.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 109.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 110.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 111.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 112.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 113.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 114.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 115.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 116.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 117.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 118.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 119.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 120.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 121.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 122.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 123.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 124.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 125.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 126.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 127.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 169.254.0.0/255.255.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 172.16.0.0/255.240.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 173.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 174.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 175.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 176.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 177.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 178.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 179.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 180.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 181.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 182.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 183.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 184.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 185.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 186.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 187.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 189.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 190.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 192.0.2.0/255.255.255.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 192.168.0.0/255.255.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 197.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 198.18.0.0/255.254.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 223.0.0.0/255.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A NR -s 224.0.0.0/224.0.0.0 -d 128.194.52.0/255.255.254.0 -i eth1 -j LSI 
-A OUTBOUND -p icmp -j ACCEPT 
-A OUTBOUND -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A OUTBOUND -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A OUTBOUND -j ACCEPT 
-A OUTPUT -s 128.194.53.223 -d 128.194.254.1 -p tcp -m tcp --dport 53 -j ACCEPT 
-A OUTPUT -s 128.194.53.223 -d 128.194.254.1 -p udp -m udp --dport 53 -j ACCEPT 
-A OUTPUT -s 128.194.53.223 -d 128.194.254.2 -p tcp -m tcp --dport 53 -j ACCEPT 
-A OUTPUT -s 128.194.53.223 -d 128.194.254.2 -p udp -m udp --dport 53 -j ACCEPT 
-A OUTPUT -s 128.194.53.223 -d 128.194.254.3 -p tcp -m tcp --dport 53 -j ACCEPT 
-A OUTPUT -s 128.194.53.223 -d 128.194.254.3 -p udp -m udp --dport 53 -j ACCEPT 
-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -s 224.0.0.0/255.0.0.0 -j DROP 
-A OUTPUT -d 224.0.0.0/255.0.0.0 -j DROP 
-A OUTPUT -s 255.255.255.255 -j DROP 
-A OUTPUT -d 0.0.0.0 -j DROP 
-A OUTPUT -m state --state INVALID -j DROP 
-A OUTPUT -o eth1 -j OUTBOUND 
-A OUTPUT -o eth0 -j OUTBOUND 
-A OUTPUT -j LOG_FILTER 
-A OUTPUT -j LOG --log-prefix "Unknown Output" --log-level 6 
COMMIT
# Completed on Wed Sep  6 20:40:34 2006

```

---

### Post by jdong on 2006-09-06
Holy mother of sysvinit that is one of the hairiest iptables NAT scripts I've seen! Where did you get that?

---

### Post by austin987 on 2006-09-07
:oops: Default from installation of dhcpd3 if I recall correctly. Hmm, could be the cause of the problem I dare say.

Now to get a guide for IPtables...

---

### Post by austin987 on 2006-09-07
Solved. My ignorance was the cause.

Firestarter was running, which I thought was disabled.

Reconfigured, allow port 22 for anyone, samba ports for lan, etc.

Working

Thanks for all the help.

---

### Post by jdong on 2006-09-07
hehe, glad you found the problem :)... That also explains the monstrous iptables script.. probably firestarter generated that one?

---

### Post by austin987 on 2006-09-07
I suppose so, I never manually configured it. Just ran sudo iptables-save >> iptables.txt

---

