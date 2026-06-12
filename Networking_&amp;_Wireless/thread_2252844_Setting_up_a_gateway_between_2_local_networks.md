---
title: "Setting up a gateway between 2 local networks"
date: 2014-11-15
forum: Networking &amp; Wireless
---

### Post by didi2 on 2014-11-15
Hi! :)

On my computer, I'm virtualizing 2 networks with 3 VMs:
NET1: 192.168.0.0/24
NET2: 192.168.1.0/24

VM1:
eth0 192.168.0.1

VM2:
eth0 192.168.0.2
eth1 192.168.1.1

VM3:
eth0 192.168.1.2


I want VM1 to be able to ping VM3, even if they're not in the same network.
So, i wrote this line in my VM1 /etc/network/interfaces:
```
gateway 192.168.0.2
```

When I try to make VM1 ping VM3, I can see on Wireshark that these packets are sent to VM2 (OK), but VM2 doesn't send them to VM3, why?
VM1 can ping my VM2 eth1 interface.

Thanks for your help! :)

---

### Post by The Cog on 2014-11-15
You need to configure VM2 to forward packets (forwarding is disabled by default).

There is a virtual file /proc/sys/net/ipv4/ip_forward that contains either 0 or 1. You can see the current state with 
```
cat /proc/sys/net/ipv4/ip_forward
```
and you can turn it on (change to 1) with a text editor or with the command
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
There is a file /etc/sysctl.conf that contains startup settings. To enable forwarding on startup, remove the # from the front of this line:
```
#net.ipv4.ip_forward=1
```

Nice clearly stated question by the way.

P.S.
Don't forget the reply has to get back. Lots of people forget to worry about the return path.

P.P.S.
[http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](http://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)

---

### Post by didi2 on 2014-11-15
Thanks, everything works now. :)

However, the path to [FONT=courier new]ip_forward[/FONT] was different, but nothing serious:
```
/proc/sys/net/**ipv4**/ip_forward
```


Problem solved.
Have a nice day! :)

---

