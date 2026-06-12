---
title: "Can't ssh after mounting cifs"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by grandrigo on 2013-11-14
So I was able to ssh to a LiveDuo (other computer)  before but after I mounted the address, now I can't ssh to it anymore. How can I resolve this issue? I am able to ssh from a different computer connected to the network so its not the other computer problem.

When I type (from the ubuntu computer):

$ssh <IP_ADDRESS> 
ssh: connect to host 10.50.4.43 port 22: No route to host

$ping <IP_ADDRESS>
perea@kus-imaging2:/TROJAN$ ping  <IP_ADDRESS>
PING <IP_ADDRESS> 56(84) bytes of data.
From <IP_ADDRESS> icmp_seq=1 Destination Host Unreachable
From <IP_ADDRESS> icmp_seq=2 Destination Host Unreachable
.
.
.




Something is wrong  but I dont know what :/

---

### Post by warp4ever on 2013-11-14
In my experience the following solved this:
When you do (in a terminal) as root:
```
service ssh status
```
What's the response?
If it is ssh is not running do:
```
service ssh start
```
Then, when responded by (like):
```
auth.crit sshd[11724]: fatal: daemon() failed: No such device
```
This probably means that "/dev/null" may be created as a file and not as node.
Remove and recreate in one command:
```
rm /dev/null -f && mknod /dev/null c 1 3
```     (-f option prevents confirmation for removal of /dev/null)

Hope this helps.

---

### Post by bab1 on 2013-11-14
> **grandrigo said:**
> So I was able to ssh to a LiveDuo (other computer)  before but after I mounted the address, now I can't ssh to it anymore. How can I resolve this issue? I am able to ssh from a different computer connected to the network so its not the other computer problem.

When I type (from the ubuntu computer):

$ssh <IP_ADDRESS> 
ssh: connect to host 10.50.4.43 port 22: No route to host

$ping <IP_ADDRESS>
perea@kus-imaging2:/TROJAN$ ping  <IP_ADDRESS>
PING <IP_ADDRESS> 56(84) bytes of data.
From <IP_ADDRESS> icmp_seq=1 Destination Host Unreachable
From <IP_ADDRESS> icmp_seq=2 Destination Host Unreachable
.
.
.




Something is wrong  but I dont know what :/
Before you do anything else you should see if the host can ping itself.  The above ping response indicates that at the very least there is no IP networking at all.  Could the host be down?

---

### Post by grandrigo on 2013-11-20
The host is able to ping itself. I can ping to it from a different computer but not from "the" ubuntu machine...any other alternatives?


When I run service ssh start:

:~$ service ssh start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.270" (uid=1002 pid=24250 comm="start ssh ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

---

### Post by houstonbofh on 2013-11-20
Have both machines ping a common server, then do an **arp -a** on both machines, and the common machine.  Something may be messing with layer 2...

---

### Post by bab1 on 2013-11-20
> **grandrigo said:**
> The host is able to ping itself. I can ping to it from a different computer but not from "the" ubuntu machine...any other alternatives?

Time for diagnosis.  Is the Ubuntu machine on the same IP network.  The test @ houstonbofh has suggested will tell you if the Ubuntu host is on the same subnet or not.
> 


When I run service ssh start:

:~$ service ssh start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.270" (uid=1002 pid=24250 comm="start ssh ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
You have to be root to use that command try it with sudo```
sudo service ssh [stop start restart] 
```

---

### Post by grandrigo on 2013-11-25
Restarted but still I can't connect:

$ sudo service ssh restart
ssh stop/waiting
ssh start/running, process 19901

$ ssh 10.50.4.43
ssh: connect to host 10.50.4.43 port 22: No route to host

---

