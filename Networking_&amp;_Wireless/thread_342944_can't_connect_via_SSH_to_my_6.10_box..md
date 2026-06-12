---
title: "can't connect via SSH to my 6.10 box."
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by caffienda on 2007-01-20
I am trying to connect over the network to backup files.  I have tried PuTTY, and it always times out.  I installed Cygwin (which is much larger that I thought) and when I try to connect with this it always times out as well.  

I am using the following command and it has not worked once:
-ssh user@address 

(I've tried sftp, pscp, pftp, and others with the correct command) It seems that the linux box is not accepting the SSH connection.  To install the SSH I did "sudo apt-get install ssh" and it ran through the install process.

Is there a way to figure out why the two systems don't connect?  I can connect to my web-host via SSH, sftp and scp with the Linux/ubuntu box that I am trying to connect to.  

What's going on?

---

### Post by PilotJLR on 2007-01-20
Let's make sure sshd is actually running before we look at firewalls... what is the output of this:
```

ps -ef | grep ssh

```

---

### Post by caffienda on 2007-01-20
Thanks for the assistance!  I really appreciate it!

root      4592     1  0 13:21 ?        00:00:00 /usr/sbin/sshd
michael  11982 11947  0 19:47 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
michael  17442 17419  0 23:13 pts/1    00:00:00 grep ssh

---

### Post by PilotJLR on 2007-01-20
Hmm... yeah it sure appears to be running. Would you also port scan yourself, and see if the service is open on port 22?
This is how (from the problem computer):
```

sudo apt-get install nmap
nmap localhost

```

I'm wondering if you see a line like:
```

22/tcp   open  ssh

```

---

### Post by caffienda on 2007-01-21
Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-01-21 00:02 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 1673 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
631/tcp  open  ipp
902/tcp  open  iss-realsecure-sensor
3306/tcp open  mysql
5900/tcp open  vnc

Nmap finished: 1 IP address (1 host up) scanned in 0.511 seconds

---

### Post by PilotJLR on 2007-01-22
Hmm - the ssh port is open...

Can you ping this machine from elsewhere?? If so, can you also go to its IP address in a web browser (I noticed you have that open too)?

---

### Post by caffienda on 2007-01-22
I can ping it no problem, but I can't reach it with the web browser.  I assume to reach it with the browser I just type in it's IP addy.?.

If I can't log in to this machine, is it possible to set a SSH server on my XP box and SSH into that machine?  So this would be the opposite, instead of logging into the Linux box, log into the XP box.  

I just need to get 55GB of files from the Linux PC to another.  

Any ideas?

---

### Post by PilotJLR on 2007-01-22
You could always install an ftp server on the windows box and do that too...

But a couple more things to check... what is the output of this:
```

sudo iptables --list

```

And to just make sure we're on the same page... what is the output of this:
```

ifconfig

```
And also what is the address you pinged that was successful? Part of what I'm wondering is if we're talking about PC's NOT on the same lan... which could make this a port forward issue.

---

### Post by caffienda on 2007-01-22
I pinged and tried to connect (in the browser) to 192.168.1.130  and [http://192.168.1.130](http://192.168.1.130)

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dns.eph.ptd.net      anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns.eph.ptd.net      anywhere            
ACCEPT     tcp  --  dns2.ptd.net         anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns2.ptd.net         anywhere            
ACCEPT     tcp  --  dns.sth.ptd.net      anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns.sth.ptd.net      anywhere            
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.130        dns.eph.ptd.net     tcp dpt:domain 
ACCEPT     udp  --  192.168.1.130        dns.eph.ptd.net     udp dpt:domain 
ACCEPT     tcp  --  192.168.1.130        dns2.ptd.net        tcp dpt:domain 
ACCEPT     udp  --  192.168.1.130        dns2.ptd.net        udp dpt:domain 
ACCEPT     tcp  --  192.168.1.130        dns.sth.ptd.net     tcp dpt:domain 
ACCEPT     udp  --  192.168.1.130        dns.sth.ptd.net     udp dpt:domain 
ACCEPT     tcp  --  192.168.1.130        192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.130        192.168.1.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere   

*******************************************
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:E7:F7:F8  
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fee7:f7f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35089528 (33.4 MiB)  TX bytes:3978741 (3.7 MiB)
          Interrupt:209 Base address:0xf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:268356 (262.0 KiB)  TX bytes:268356 (262.0 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.41.1  Bcast:172.16.41.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.244.1  Bcast:172.16.244.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by dmizer on 2007-01-23
> **caffienda said:**
> I can ping it no problem, but I can't reach it with the web browser. I assume to reach it with the browser I just type in it's IP addy.?

um ... please don't take offense to this, but are you trying to ssh via firefox?  you can't connect via http unless apache is installed on the remote machine, and this would give you website like access, not ssh access. ssh is a command line only connection.  to use ssh, you simply type:
```
ssh remote-user-id@remote.ipaddress
```
into the command line.  you should get a request to grant a key, and then type in the password for the remote machine and you will have COMMAND LINE access to your remote computer.

if you want to copy files, you will have to use scp or rsync (both are a part of the scp package).  [click here for scp howto](http://easylinux.info/wiki/Ubuntu_dapper#How_to_copy_files.2Ffolders_from_remote_Ubuntu_machine_into_local_machine_.28scp.29) 

just seemed strange that you're talking about a browser but the utility is a command line utility, so forgive me if i've missunderstood.

---

### Post by caffienda on 2007-01-23
Apache is installed and was working.


I was in the command line when I tried to connect with SSH.   I am unable to connect with ssh, scp, sftp, ftp.

---

### Post by caffienda on 2007-01-23
pilotJLR:  I installed a FTP server and it's working very well to copy the files.  Thank you for the suggestion!

I'm going to scrap this install of Ubuntu.  I seem to be able to destroy even Linux installs:lolflag:   Oh-well.  thanks a lot for the help, I really appreciated it!

---

### Post by BeachBum on 2007-01-29
[QUOTE=caffienda;2051013]I pinged and tried to connect (in the browser) to 192.168.1.130  and [http://192.168.1.130](http://192.168.1.130)

Forgive me also if I've misunderstood your situation, but I believe PilotJLR was correct in assuming this to be a port forwarding issue.

That address you're using is a LAN address; you should be able to do everything, ping and all, using that address from within your home network, but accross the internet, that address means nothing.  Based on that address, I'm assuming you're using a router, and if you want to connect to a computer behind a router, you need to forward some ports (just google around for some how-to's for your model router) to your server box, and determine if your IP is static or dynamic.  If it is dynamic, there is a nice how-to on using DynDns some where on these forums.  
 
Once you set that up you can connect via ssh over the net.

---

