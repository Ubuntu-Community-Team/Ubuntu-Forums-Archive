---
title: "Not able to do password-free access to remote machine!"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by Ravi Singh on 2013-09-06
When I run

```
 ravbholua@ravbholua-Aspire-5315:~$ rlogin 109.202.101.166
```
it promps me for password as below:
```

ravbholua@ravbholua-Aspire-5315:~$ rlogin 109.202.101.166
ravbholua@109.202.101.166's password:

```To make password free access, I created a file /etc/hosts.equiv
in the remote machine (ravi.com) as below:
```

root@ravi:/etc# cat hosts.equiv
localhost
42.110.54.211
root@ravi:/etc#

```But still whenever I run the above command to login to this remote
machine, it asks for password.

Additionally, I also created .rhosts file in my same like-to-like account
in remote machine in home dir. as below:

```

ravbholua@ravi:~$ cat .rhosts
localhost
42.110.54.211
ravbholua@ravi:~$

```What may be the problem that I am not able to have password-free access.

One important point to be noted:
To know what's my internet IP address is, I got from the below two sites > [http://www.ipchicken.com/](http://www.ipchicken.com/)
[http://whatismyip.org/]("http://whatismyip.org/These")

---

### Post by Ravi Singh on 2013-09-06
Then I ran command : ifconfig

Please have a look at the below output of ifconfig:[B]
For my local box:
-----------------[/B]
```

ravbholua@ravbholua-Aspire-5315:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:d0:45:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85372 (85.3 KB)  TX bytes:85372 (85.3 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.224.108.37  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2352345 (2.3 MB)  TX bytes:698847 (698.8 KB)

ravbholua@ravbholua-Aspire-5315:~$[B]
```
For my remote box
------------------[/B]
```

root@ravi:/etc# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3571 (3.5 KB)  TX bytes:3571 (3.5 KB)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:155219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118966 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182245690 (182.2 MB)  TX bytes:9737063 (9.7 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:109.202.101.166  P-t-P:109.202.101.166  Bcast:109.202.101.166  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
```
Finally  looking at the above outputs, I configured the remote box with the ip  address as 10.224.108.37 (this is what the above command mentions for  local box) but still it's asking for password.

---

