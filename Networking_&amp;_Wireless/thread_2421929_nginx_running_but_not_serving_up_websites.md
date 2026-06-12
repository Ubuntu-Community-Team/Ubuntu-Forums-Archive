---
title: "nginx running but not serving up websites"
date: 2019-06-29
forum: Networking &amp; Wireless
---

### Post by weavil on 2019-06-29
[COLOR=#242729][FONT=Arial]Need a little help. I had Nginx up and running for about 2 years. I am not sure what I did when trying to update a certificate but now my sites are not accessible.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I went to my website:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][URL="https://ttrss.shiromar.com/"]
[/URL][/FONT][/COLOR]```
[COLOR=#242729][FONT=Arial][https://ttrss.shiromar.com]("https://ttrss.shiromar.com/")[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I noticed the certificate expired so I went about renewing it and ran:
[/FONT][/COLOR]
```
sudo certbot --nginx -d ttrss.shiromar.com
```[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]and I got an error about Certbot not being able to access the website for verification. I checked networking and forwarding rules and everything seemed fine so I decided to start the certificate process anew and ran:[/FONT][/COLOR]
sudo certbot delete --cert-name ttrss.shiromar.com
[COLOR=#242729][FONT=Arial]This was when my site became inaccessible. Certbot can't reach my site so it can't issue a certificate. I commented out the SSL lines in the server block and restarted Nginx and PHP and still couldn't reach it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is the server block for ttrss:[/FONT][/COLOR]
```
server  {
    listen          80;
    listen          [::]:80;
    server_name     ttrss.shiromar.com [www.ttrss.shiromar.com;]("http://www.ttrss.shiromar.com%3B/")
    return          301 https://$server_name$request_uri;
    }
    server {
    listen          443 ssl http2;
    listen          [::]:443 ssl http2;
    server_name     ttrss.shiromar.com [www.ttrss.shiromar.com;]("http://www.ttrss.shiromar.com%3B/")
    root /var/www/ttrss;
    index index.php;
    access_log /var/log/nginx/ttrss_access.log;
    error_log /var/log/nginx/ttrss_error.log info;
    location = /robots.txt {
    allow all;
    log_not_found off;
    access_log off;
    }
    location / {
    index           index.php;
    }
    #ssl_certificate         /etc/letsencrypt/live/ttrss.shiromar.com/fullchain.pem;
    #ssl_certificate_key     /etc/letsencrypt/live/ttrss.shiromar.com/privkey.pem;
    #ssl_trusted_certificate /etc/letsencrypt/live/ttrss.shiromar.com/chain.pem;
    location ~ \.php$ {
    try_files $uri = 404; #Prevents autofixing of path which could be used for exploit
    fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    fastcgi_index index.php;
    include /etc/nginx/fastcgi.conf;
    }
    }

```
[COLOR=#242729][FONT=Arial]here is a netstat showing ports open[/FONT][/COLOR]
```
sudo netstat -tanpl|grep nginx
    tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2052/nginx: master
    tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2052/nginx: master
    tcp6       0      0 :::80                   :::*                    LISTEN      2052/nginx: master
    tcp6       0      0 :::443                  :::*                    LISTEN      2052/nginx: master
```
[COLOR=#242729][FONT=Arial]This server is running in a VM on Hyper-V. I did have a checkpoint from early last year. I tested it and that does work but it's a bit too old.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have triple checked IP addresses and port forwarding rules and I keep coming back to an issue with Nginx or a setting in Ubuntu that's blocking all 443/80 traffic. Oh and this is Ubuntu 18.04 and Nginx version: nginx/1.14.0 (Ubuntu)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is a status of ufw:[/FONT][/COLOR]
```
sudo ufw status
    Status: active
    To                         Action      From
    --                         ------      ----
    OpenSSH                    ALLOW       Anywhere
    8181/tcp                   ALLOW       Anywhere
    Nginx Full                 ALLOW       Anywhere
    443/tcp                    ALLOW       Anywhere
    80/tcp                     ALLOW       Anywhere
    3000                       ALLOW       Anywhere
    OpenSSH (v6)               ALLOW       Anywhere (v6)
    8181/tcp (v6)              ALLOW       Anywhere (v6)
    Nginx Full (v6)            ALLOW       Anywhere (v6)
    443/tcp (v6)               ALLOW       Anywhere (v6)
    80/tcp (v6)                ALLOW       Anywhere (v6)
    3000 (v6)                  ALLOW       Anywhere (v6)
```

---

### Post by TheFu on 2019-06-29
```
$ ping ttrss.shiromar.com
PING ttrss.shiromar.com (209.6.66.94) 56(84) bytes of data.
^C
--- ttrss.shiromar.com ping statistics ---
8 packets transmitted, 0 received,[COLOR="#FF0000"] 100% packet loss[/COLOR], time 6999ms

```
Seems the server isn't up.  I checked the DNS and it looks fine.  I didn't scan the IP for open services, but that would be my next task. The scan must come from outside.  A **traceroute** is taking a very long time, so there might be some funky internet routing happening that your system is caught up inside. 

Basically, from my location to yours has too many hops.  I'd contact the ISP where that server is located.
```
 9  hge0-0-0-4.core1.bos.ma.rcn.net (207.172.19.52)  52.871 ms hge0-0-0-4.core1.sth.ma.rcn.net (207.172.19.66)  54.227 ms  54.544 ms
10  hge0-2-0-0.aggr1.bos.ma.rcn.net (207.172.19.184)  56.678 ms  55.790 ms hge0-2-0-2.aggr1.bos.ma.rcn.net (207.172.19.188)  53.729 ms
11  port-chan2.abr-cbr1.sbo-abr.ma.cable.rcn.net (146.115.22.202)  49.940 ms  50.301 ms  53.006 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```
Then it gives up.

Looks like a routing issue to me. Call the ISP.

---

### Post by weavil on 2019-06-29
that's exactly my issue @TheFu, 

The server is running and not taking traffic.

This is self hosted, the server is right in front of me. I too wondered about the ISP. Like I wrote, this all happened very sudden. One moment everything was working and the next it wasn't.

We can rule out the ISP because as I wrote, the backup checkpoint works fine. I actually have the backup VM running right now and if I want the backup to start serving I just need to change the port forwarding rules but that backup is way too old. I actually tested this yesterday, I changed the port forwarding and everything was fine.

---

### Post by TheFu on 2019-06-29
"checkpoint"  I'm unfamiliar with that term. Please explain.
Is it like a full backup or an LVM/ZFS snapshot?

If you have a backup working, why not just compare the config files between the backup server and the primary one?  I'm confused.  I'd use rsync in test-only mode to see which files are different, then dig deeper using the normal diff/sdiff/meld tools on specific files.

If a server is that important, I'd have automatic, daily, backups created.  Not just for this sort of issue, but to handle the other 1001 problems that daily, versioned, backups solve.

---

### Post by weavil on 2019-06-29
checkpoint is the hyper-v term for backup. 

I have them running side by side, the nginx server block for ttrss matches exactly between the backup and the current.

---

### Post by TheFu on 2019-06-29
I've never seen hyper-v anywhere. Sorry for my ignorance.  On the surface, it sounds like a qcow2 snapshot, assuming it is instantaneous. I'll have to look it up.

If the nginx config file is identical, then it is something else, yes?  Did you use the rsync technique I suggested to find all the config files that were different?

And just to be certain, you did change the LAN IP address between the primary and backup system, yes?

---

### Post by weavil on 2019-06-29
they are both running at the same time and are on separate IP's yes.

As for the nginx server block configs, they are all identical to the backup.

---

### Post by weavil on 2019-06-29
Here's something interesting. I am able to ping the site from inside my network. I can't access the site in my network however and uptrends shows my site as inaccessible. 

```
ping ttrss.shiromar.com                                                                              
Pinging ttrss.shiromar.com [209.6.66.94] with 32 bytes of data:
Reply from 209.6.66.94: bytes=32 time=9ms TTL=63
Reply from 209.6.66.94: bytes=32 time=3ms TTL=63
Reply from 209.6.66.94: bytes=32 time=2ms TTL=63
Reply from 209.6.66.94: bytes=32 time=8ms TTL=63


Ping statistics for 209.6.66.94:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 9ms, Average = 5ms
```

I tried from a few sources with in my network. Mobiles other PC's. So what could be causing this kind behavior is the question.

---

### Post by TheFu on 2019-06-29
> **weavil said:**
> they are both running at the same time and are on separate IP's yes.

As for the nginx server block configs, they are all identical to the backup.

What other config files are different on the system?  Is there a reason you don't use rsync (or some other tool) to get that list? 

You seem very confident that it isn't a network issue.  Could it be a hyper-v issue?  
What about a VM network config problem?
Do both VMs run using exactly the same physical connections?  
Are they bridged or do you use PCI passthru for the NICs?
Is the routing all the same?

I still can't ping that public IP from here. 100% packet loss. Does your WAN router block pings?

---

### Post by weavil on 2019-06-29
> **TheFu said:**
> What other config files are different on the system?  Is there a reason you don't use rsync (or some other tool) to get that list? 

You seem very confident that it isn't a network issue.  Could it be a hyper-v issue?  
What about a VM network config problem?
Do both VMs run using exactly the same physical connections?  
Are they bridged or do you use PCI passthru for the NICs?
Is the routing all the same?

I still can't ping that public IP from here. 100% packet loss. Does your WAN router block pings?

I'm not familiar with how to produce a list in rsync to get a result like that.

On the contrary I think it is a network issue, within ubuntu probably. 

The VM is a backup there's nothing different.

Yes they use the same physical connection.

They are not bridged, each VM has it's own unique IP.

The routing is the same.

We can see above that the ports are open and ufw looks correct. I'm trying to find out what else could be causing it.

---

### Post by TheFu on 2019-06-29
> **weavil said:**
> I'm not familiar with how to produce a list in rsync to get a result like that.

Neither am I. I'd have to read the manpage. I know it is possible.  manpages are freakin' amazing. It is like a cheat sheet right on your system for every command. From the rsync manpage:
```
        -n, --dry-run               perform a trial run with no changes made

```

> **weavil said:**
> On the contrary I think it is a network issue, within ubuntu probably. 
 Possible.  I would like to see all the network stuff posted from both machines.
```
ifconfig
route -n
/etc/resolv.conf
```
to start.  Proof, not descriptions.

> **weavil said:**
> 
The VM is a backup there's nothing different.
 I'm having trouble believing this statement.  Your idea of "nothing different" is different from my idea, is seems.  At a minimum, the network configs would be different.  Log files would be different. Hostnames too.  rsync will show the files that are different, but feel free to accomplish it anyway you like.
[https://superuser.com/questions/576687/how-to-print-files-that-would-have-been-changed-using-rsync](https://superuser.com/questions/576687/how-to-print-files-that-would-have-been-changed-using-rsync) has a few more details. 

> **weavil said:**
> 
Yes they use the same physical connection.

Then it is bridged.

> **weavil said:**
> 
They are not bridged, each VM has it's own unique IP.

I don't think we understand "bridged" in the networking world the same way.

> **weavil said:**
> 
The routing is the same.

While I don't think this is untrue, please prove it.  Humor an old, senile, man.

> **weavil said:**
> 
We can see above that the ports are open and ufw looks correct. I'm trying to find out what else could be causing it.
Perhaps there are conflicting, duplicate ufw rules?  You have separate rules for 443/tcp and 80/tcp, then there is also an "nginx full" rule, which covers both of those.

Have you looked at the system and nginx log files?  Any errors or warnings there?

I don't use certbot. Had some issues with renewals, so I switched to **acme.sh** and have acme.sh run a standalone web server when it is time to renew certs.  I have a mix of webapps local and on other systems, plus local and other system static websites. Nginx is effectively a reverse proxy for about 20 of my small websites.  

Which version of Ubuntu are you running. For network stuff, it matters since they recently changed everything.  **lsb_release -a** will show the needed info.

---

### Post by weavil on 2019-06-30
Correct me if I'm wrong but isn't bridged if the host and the VM share the same IP?

the following is for the backup.
```
ifconfigbr-b480800e04d3: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.18.0.1  netmask 255.255.0.0  broadcast 172.18.255.255
        ether 02:42:01:27:c9:66  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:79:41:51:90  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::215:5dff:fecb:8d15  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:cb:8d:15  txqueuelen 1000  (Ethernet)
        RX packets 656986  bytes 865580428 (865.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 194620  bytes 22017245 (22.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 515414  bytes 231213386 (231.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 515414  bytes 231213386 (231.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-b480800e04d3
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
Codename:       bionic

/etc/resolv.conf
nameserver 127.0.0.53
options edns0

```




and now for the main

```
ifconfigbr-b480800e04d3: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.18.0.1  netmask 255.255.0.0  broadcast 172.18.255.255
        ether 02:42:82:9c:7c:10  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:11:b3:b4:7b  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.99  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::215:5dff:fecb:8d13  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:cb:8d:13  txqueuelen 1000  (Ethernet)
        RX packets 596748  bytes 783702187 (783.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 190548  bytes 15601125 (15.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 441337  bytes 204666713 (204.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 441337  bytes 204666713 (204.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-b480800e04d3
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
Codename:       bionic

/etc/resolv.conf
nameserver 127.0.0.53
options edns0

```


The UFW conflict comment is interesting. I'll try removing the other rules but please note, the UFW settings do match with the backup and I have tried with UFW disabled. So I don't have my hopes up for that. 

iptables for backup

```
iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere


Chain FORWARD (policy DROP)
target     prot opt source               destination
DOCKER-USER  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-1  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere
ufw-track-forward  all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere


Chain DOCKER (2 references)
target     prot opt source               destination


Chain DOCKER-ISOLATION-STAGE-1 (1 references)
target     prot opt source               destination
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain DOCKER-ISOLATION-STAGE-2 (1 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain DOCKER-USER (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere


Chain ufw-after-forward (1 references)
target     prot opt source               destination


Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination


Chain ufw-after-output (1 references)
target     prot opt source               destination


Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere


Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination


Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere


Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere


Chain ufw-reject-forward (1 references)
target     prot opt source               destination


Chain ufw-reject-input (1 references)
target     prot opt source               destination


Chain ufw-reject-output (1 references)
target     prot opt source               destination


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-track-forward (1 references)
target     prot opt source               destination


Chain ufw-track-input (1 references)
target     prot opt source               destination


Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh /* 'dapp_OpenSSH' */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8181
ACCEPT     tcp  --  anywhere             anywhere             multiport dports http,https /* 'dapp_Nginx%20Full' */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3000
ACCEPT     udp  --  anywhere             anywhere             udp dpt:3000


Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination


Chain ufw-user-output (1 references)
target     prot opt source               destination
```

and for the main:

```
iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere


Chain FORWARD (policy DROP)
target     prot opt source               destination
DOCKER-USER  all  --  anywhere             anywhere
DOCKER-ISOLATION-STAGE-1  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
DOCKER     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere
ufw-track-forward  all  --  anywhere             anywhere


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere
ufw-track-output  all  --  anywhere             anywhere


Chain DOCKER (2 references)
target     prot opt source               destination


Chain DOCKER-ISOLATION-STAGE-1 (1 references)
target     prot opt source               destination
DOCKER-ISOLATION-STAGE-2  all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain DOCKER-ISOLATION-STAGE-2 (1 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere
RETURN     all  --  anywhere             anywhere


Chain DOCKER-USER (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere


Chain ufw-after-forward (1 references)
target     prot opt source               destination


Chain ufw-after-input (1 references)
target     prot opt source               destination
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination


Chain ufw-after-output (1 references)
target     prot opt source               destination


Chain ufw-before-forward (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere


Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination


Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere


Chain ufw-logging-allow (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere


Chain ufw-reject-forward (1 references)
target     prot opt source               destination


Chain ufw-reject-input (1 references)
target     prot opt source               destination


Chain ufw-reject-output (1 references)
target     prot opt source               destination


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-track-forward (1 references)
target     prot opt source               destination


Chain ufw-track-input (1 references)
target     prot opt source               destination


Chain ufw-track-output (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination


Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh /* 'dapp_OpenSSH' */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8181
ACCEPT     tcp  --  anywhere             anywhere             multiport dports http,https /* 'dapp_Nginx%20Full' */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3000
ACCEPT     udp  --  anywhere             anywhere             udp dpt:3000


Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination


Chain ufw-user-output (1 references)
target     prot opt source               destination
```

---

### Post by TheFu on 2019-06-30
Sorry, my email server needed some maintenance today.  Some emails were long delayed.
 
By chance, is the server network connection over wifi?  I ask because bridges are known not to work with most wifi devices. Since it worked previously, this idea is a stretch.

I haven't moved any of my systems to 18.04 yet. The way networking is configured on that release is entirely different from 16.04, so I'm afraid to make many suggestions.  The networking changes are THE MAIN reason I haven't moved to 18.04.  I don't think netplan is ready.  I have the same issue with systemd and avoided it about 2 yrs on my production systems.  Systemd has broken a number of things months after the forced upgrade to use it.  I've had a number of issues with systemd-resolv the last 8 months, including a failure due to it TODAY on my email gateway.

Anyways, it is all looking the same to me.

And as for bridging ... there are 3 main types of network connections in the virtual machine world.
[LIST=1]
[*]Bridged
[*]NAT
[*]Host-Only
[/LIST]
You can read up about each of those in the user's guide for whatever hypervisor you use. They are pretty standard.  [https://www.virtualbox.org/manual/ch06.html#networkingmodes](https://www.virtualbox.org/manual/ch06.html#networkingmodes) has a reasonable description.  VMware's version: [https://www.vmware.com/support/ws4/doc/network_bridged_ws.html](https://www.vmware.com/support/ws4/doc/network_bridged_ws.html)  and KVM using libvirt: [https://wiki.libvirt.org/page/Networking](https://wiki.libvirt.org/page/Networking)

Bridged makes the VM part of the same subnet as the host connection.  If the host IP is .5/24 then the bridged guest IP is within the same /24 always.  The guest VM can either use DHCP from the host subnet or set a static IP inside that /24 following the normal subnet collision rules.  This is good for server VMs that have been hardened.

NAT makes the VM have a NAT address which the hostIP is seen by the outside world.  Basically, the guestVM uses the host machine like a NAT router. This is good for desktop VMs.

Host-only would place the guestVM on a subnet that only other VMs running on the same VM-host can see. This is good for labs and running services that only other VM guest machines should ever access.

How hyper-V handles these, I don't know.  VirtualBox, VMware Player, Workstation, ESX and ESXi all have configuration options in their GUI interfaces.  Xen and KVM/QEMU use networking provided by the Linux hostOS, so anything possible by any router can be accomplished, including NAT, Bridged, and host-only networking.

---

