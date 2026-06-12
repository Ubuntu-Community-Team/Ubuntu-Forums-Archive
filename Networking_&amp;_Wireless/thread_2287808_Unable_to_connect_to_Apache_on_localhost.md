---
title: "Unable to connect to Apache on localhost"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by peter1897 on 2015-07-22
I installed Ubuntu 14.04 on virtualbox and after this installed apache2 and mysql servers. But i am not able to connect to apache from my browser. If i type 127.0.0.1 in the browser  i get: **Firefox can't establish a connection to the server at 127.0.0.1.**

The apache is running though it shows that it is running on IPv6 address:
```
max@ubuntu:~$ sudo netstat -ntlpa
[sudo] password for max:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      900/sshd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      965/mysqld
tcp        0      0 10.0.2.15:22            10.0.2.2:61031          ESTABLISHED 1239/sshd: max [pri
tcp6       0      0 :::22                   :::*                    LISTEN      900/sshd
tcp6       0      0 :::80                   :::*                    LISTEN      1194/apache2
```

These are the ifconfig settings:
```
max@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:08:36:e5
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe08:36e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:78067 (78.0 KB)  TX bytes:83693 (83.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Why i am not able to connect to apache?

---

### Post by Lars Noodén on 2015-07-22
Just as a quick test can you connect to ::1/128 instead of 127.0.0.1?  If so, then the question is why it is listening only to IPv6

---

### Post by peter1897 on 2015-07-22
No, i am not able to connect to **::1/128**. I get this:
```
This address is restricted

This address uses a network port which is normally used for purposes other than Web browsing. Firefox has canceled the request for your protection.
```

---

### Post by Lars Noodén on 2015-07-22
Try a slightly modified form with brackets:

[http://[::1]/](http://[::1]/)

In your /etc/hosts file, is there a line something like the following?

```

127.0.0.1       localhost

```

---

### Post by peter1897 on 2015-07-22
If i type the address with brackets i get:
```
Unable to connect

Firefox can't establish a connection to the server at [::1].
```

And yes, i have the line: **127.0.0.1 localhost** in my /etc/hosts file.

I found a solution which i don't know if it is the best but it is working. I created a second network interface which look like this:

```
# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.56.105
netmask 255.255.255.0
network 192.168.56.1
broadcast 192.168.56.255
```

And now if i type 192.168.56.105 in the browser i am able to connect to apache. 

But i still don't know why i am not able to connect to 127.0.0.1.

---

### Post by peter1897 on 2015-07-22
Is it possible the reason to not be able to connect to apache is that the virtualbox dhcp server assigns ip addresses in the range 192.168.56.101 to 192.168.56.254 and the default ubuntu network interface eth0 ip address is 10.0.2.15 which is out of the range of the virtualbox dhcp ip addresses?

```
max@ubuntu:/var/www$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:08:36:e5
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe08:36e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:478690 (478.6 KB)  TX bytes:351782 (351.7 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:06:13:e0
          inet addr:192.168.56.105  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe06:13e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31389 (31.3 KB)  TX bytes:22269 (22.2 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by SeijiSensei on 2015-07-22
Are you trying to connect from the host computer?  Then you'll need to use the 10.0.2.x address assigned to the VM's virtualized Ethernet adapter.  You can only use 127.0.0.1 if you are using a browser on the guest.

---

### Post by peter1897 on 2015-07-22
Yes, i am trying to connect from my host machine Windows 7 to guest machine Ubuntu 14.04, but if i type in the browser 10.0.2.15 i get:

```
The connection has timed out

The server at 10.0.2.15 is taking too long to respond.
```

---

### Post by SeijiSensei on 2015-07-22
You might try using "bridged" instead of "NAT" mode in the VM setup.  That would give the virtual machine an IP in the same subnet as the host.  If you haven't yet read this section of the VirtualBox manual, I suggest starting there:  [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by peter1897 on 2015-07-23
I am using host-only connection. I tried bridged connection and i was able to connect to apache, but i think the better way is to create second interface with static ip address because this way the virtual machine will not change its IP address.

---

### Post by SeijiSensei on 2015-07-23
You can have a static IP with a bridged configuration.  You just need to use an address outside the range assigned by DHCP on your router.

---

### Post by peter1897 on 2015-07-23
Thanks. I will test it.

---

