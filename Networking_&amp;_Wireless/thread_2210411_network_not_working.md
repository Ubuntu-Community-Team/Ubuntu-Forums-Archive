---
title: "network not working"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by sylvain2 on 2014-03-10
Hi all,

I am new here.
can't ping inside or outside same with nslookup.
I am unable to ping localhost also not unable to nslookup the  localhost, My Version is Ubuntu 13.4.

Thanks for any help

---

### Post by sylvain2 on 2014-03-10
I am able to ssh in it, unable to ping anything it the host file.
Like I said before not able to ping local host.

---

### Post by steeldriver on 2014-03-10
Hello and welcome to the forums 

What exactly happens (timeout? no route to host?) - please add a cut and paste of the terminal command and any error messages

---

### Post by sylvain2 on 2014-03-10
when I try to ping it just stays there:
 ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.

and when I try to nslookup localhost I get:
nslookup localhost
;; connection timed out; no servers could be reached

here what is in my /etc/hosts :
127.0.0.1        localhost.localdomain  localhost server

---

### Post by Iowan on 2014-03-10
loopback (lo) is set up in /etc/network/interfaces?
It shows up in **ifconfig**?

---

### Post by sylvain2 on 2014-03-10
in my /etc/network/interface I have:
# The loopback network interface
auto lo
iface lo inet loopback

my ifconfig:
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28912 (28.9 KB)  TX bytes:28912 (28.9 KB)

---

### Post by Iowan on 2014-03-10
Firewall rules?
You can also check **route -n**, though it doesn't seem like a likely problem.

---

### Post by sylvain2 on 2014-03-10
here is my firewall rules:
target     prot opt source               destination
ACCEPT     tcp  --  99.99.146.24        anywhere             tcp dpt:2014
ACCEPT     tcp  --  99.99.222.126      anywhere             tcp dpt:9100
ACCEPT     tcp  --  99.99.222.126      anywhere             tcp dpt:mysql
ACCEPT     tcp  --  99.99.128.0/24      anywhere             tcp dpt:2014
ACCEPT     tcp  --  99.99.179.0/24       anywhere             tcp dpt:mysql
ACCEPT     tcp  --  99.99.179.0/24       anywhere             tcp dpt:9100
DROP       all  --  anywhere             anywhere
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

here is the result of route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         99.99.9.129    0.0.0.0         UG    0      0        0 eth0
10.8.0.0        10.8.0.9        255.255.0.0     UG    0      0        0 tun0
10.8.0.9        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
127.0.0.1       0.0.0.0         255.255.255.255 UH    0      0        0 lo
99.99.9.128    0.0.0.0         255.255.255.128 U     0      0        0 eth0

I have modified the ip a bit

---

### Post by Iowan on 2014-03-10
My (12.04) machine doesn't list the lo route, but it doesn't have the firewall or tunneling, either.

---

### Post by sylvain2 on 2014-03-10
how can I stop iptables?
how to remove the route to the lo?

---

### Post by sylvain2 on 2014-03-10
I have found my problem, I did iptables -F  voila its working now. now I have to recreate my rules

Thanks for you help          [**[COLOR=#990303][B]Iowan**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=65323")
and[**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500")

---

### Post by Iowan on 2014-03-10
Glad you found it. I'm unfamiliar enough with iptables that I didn't want to suggest something that could make things worse.
If you're certain it's fixed, please mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

