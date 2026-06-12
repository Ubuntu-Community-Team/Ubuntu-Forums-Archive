---
title: "unable add/remove or synaptic. o/s wont access internet"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by dlolson on 2009-05-19
Dual boot install of Hardy and winxp. The firefox browser connects as is normal, however the operating system cant find the connection. I am unable to update or select packages. On reload, it starts the process, gets to about 50 of 75 and then flashes warning about no connectivity. Here is the result of ifconfig.
eth0      Link encap:Ethernet  HWaddr 00:17:31:C0:5E:89  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fec0:5e89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92017 (89.8 KiB)  TX bytes:40685 (39.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

I have Hardy running on an other computer with no problems, and as far as I can see the network settings are the same. What's up?

---

### Post by superprash2003 on 2009-05-19
in your terminal type **ping google.com** and post output

---

### Post by dlolson on 2009-05-19
ping: unknown host google.com

---

### Post by gandaran on 2009-05-19
check your repositories in sources list maybe on one of them the connection fails or post the output of running  
*sudo apt-get update* here
you are not using a proxy server or are you?

---

### Post by dlolson on 2009-05-19
Here is the last dozen lines or so.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Qu'est que sais proxy server?
I have a wired connection to a router.Firefox works when I set it to roaming mode, but the add/remove does not.

---

### Post by gandaran on 2009-05-19
> **dlolson said:**
> Here is the last dozen lines or so.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz) Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Qu'est que sais proxy server?
I have a wired connection to a router.Firefox works when I set it to roaming mode, but the add/remove does not.

this is a old (feisty) repository, it doesn't belong in hardy, try removing it from the sources list then run again the command.

---

### Post by dlolson on 2009-05-19
Need a little more information.
Where is the source list. Looked in software sources but no way to add or remove.
Thanks.

---

### Post by gandaran on 2009-05-19
> **dlolson said:**
> Need a little more information.
Where is the source list. Looked in software sources but no way to add or remove.
Thanks.
you should see it in system » administration » software sources, if it's not then open it with this command  
*sudo gedit /etc/apt/sources.list*

---

### Post by dlolson on 2009-05-19
I am now baffled. It appears that I have version 7.04 Feisty installed here. I dont know how that happened as I installed it from the same disc that i used for my other computer and it has version 8.04 Hardy. Gremlins maybe. I think I will start all over. Thanks for your help.
BTW, shouldn't it still work or are there bugs?

---

### Post by regala on 2009-05-19
> **dlolson said:**
> I am now baffled. It appears that I have version 7.04 Feisty installed here. I dont know how that happened as I installed it from the same disc that i used for my other computer and it has version 8.04 Hardy. Gremlins maybe. I think I will start all over. Thanks for your help.
BTW, shouldn't it still work or are there bugs?

BTW, given you have no DNS resolution (google.com: unknown host), the numerous posts about sources.list are completely nonsense.

how do you connect your box to the internet ? seems like your provider doesn't seem to provide you a nameserver address in a sane way. Can you post the content of /etc/resolv.conf

br, mathieu

---

### Post by dlolson on 2009-05-19
My box is connected to a linksys router (hardwired) . My other computer is right beside me connected in the same manner. It is working fine.
On this machine I can access the internet within Ubuntu with firefox but not with the operating system. Winxp is working also, as far as I have tried.
Here is the contents of the file you requested.
# generated by NetworkManager, do not edit!

search eastlink.ca


nameserver 24.222.0.94
nameserver 24.222.0.95

Does this help.

---

### Post by dlolson on 2009-05-19
I am connected by wire to a linksys router. The computer beside me is connected in the same manner and running fine on ubuntu os. On this machine I can access the internet with firefox but the os wont find it. no update feature etc. here is the contents of the file
# generated by NetworkManager, do not edit!

search eastlink.ca


nameserver 24.222.0.94
nameserver 24.222.0.95

---

### Post by regala on 2009-05-19
> **dlolson said:**
> I am connected by wire to a linksys router. The computer beside me is connected in the same manner and running fine on ubuntu os. On this machine I can access the internet with firefox but the os wont find it. no update feature etc. here is the contents of the file
# generated by NetworkManager, do not edit!

search eastlink.ca


nameserver 24.222.0.94
nameserver 24.222.0.95

what do you get when ping 24.222.0.94 (on both boxen) ?
oh, BTW, can you give the output of /sbin/route from both again ?

---

### Post by dlolson on 2009-05-19
PING 24.222.0.94 (24.222.0.94) 56(84) bytes of data.
64 bytes from 24.222.0.94: icmp_seq=1 ttl=249 time=22.3 ms
64 bytes from 24.222.0.94: icmp_seq=2 ttl=249 time=20.1 ms
64 bytes from 24.222.0.94: icmp_seq=3 ttl=249 time=21.3 ms
64 bytes from 24.222.0.94: icmp_seq=4 ttl=249 time=19.7 ms

--- 24.222.0.94 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 19.724/20.885/22.305/1.015 ms

same on both machines. except for last line numbers
output of file to follow.

---

### Post by dlolson on 2009-05-19
unable output from /sbin/route 
its an executable how do I output it.

---

### Post by regala on 2009-05-19
> **dlolson said:**
> unable output from /sbin/route 
its an executable how do I output it.

run it and post what it tells you, I mean :)

and for the time being, in your sources.list, change any archive.ubuntu.com by 91.189.88.40
so that you can install "bind-tools" and give us what
```
dig
```
and ```
dig @24.222.0.94
``` tell you.

---

### Post by gandaran on 2009-05-19
> BTW, given you have no DNS resolution (google.com: unknown host), the numerous posts about sources.list are completely nonsense.
nonsense?
click on the achive-ubuntu.com link in post #5
can you connect to that link, bet you wont! url not found!

---

### Post by regala on 2009-05-19
> **gandaran said:**
> nonsense?
click on the achive-ubuntu.com link in post #5
can you connect to that link, bet you wont! url not found!

given his machine doesn't resolve google.com, I bet he won't be able to connect to a "correct" url either and I also bet that this is a mistype error on the forum (but this can be another error too). Either way, no dns resolution seems to me to be the problem. ;)

---

### Post by superprash2003 on 2009-05-20
post output of **ping 208.67.222.222** in your terminal

---

