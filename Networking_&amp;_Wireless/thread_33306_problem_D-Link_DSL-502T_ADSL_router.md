---
title: "problem D-Link DSL-502T ADSL router"
date: 2005-05-10
forum: Networking &amp; Wireless
---

### Post by SilvioTO on 2005-05-10
With this router I don't have problems connect with windows and damn small linux, but connection don't work with Ubuntu hoary. The connection estabilish but don't browse the web or mail.
can you help me please? Thanks.

---

### Post by dataw0lf on 2005-05-10
Could you post your resolv.conf here please?

as well, ping yahoo.com and post the first several lines of output.

---

### Post by SilvioTO on 2005-05-10
the content of file resolv.conf:

nameserver 192.168.1.1



result of ping yahoo.com:

ping: unknow host yahoo.com

---

### Post by joplass on 2005-05-10
How do you know is the router?  How confident are you about you card working properly.  Most people have problems with their cards and not the router itself.

---

### Post by SilvioTO on 2005-05-10
with another router all work fine. This D-Link is for my customer, I tryed befor install on  his pc. 

I have suspect: I re-tryed and with windows don't work too... and now Damn Small linux don't connect too... It's a faulty router?  :roll:

---

### Post by SilvioTO on 2005-05-10
after various tests, with winxp work perfect. hoary no. suggestion?

---

### Post by SilvioTO on 2005-05-10
I'm reset router, and tryed again ping command; the results:

ping google.com
PING google.com (216.239.37.99) 56(84) bytes of data.
64 bytes from google.com (216.239.37.99): icmp_seq=1 ttl=242 time=178 ms
64 bytes from google.com (216.239.37.99): icmp_seq=2 ttl=242 time=185 ms
64 bytes from google.com (216.239.37.99): icmp_seq=3 ttl=242 time=177 ms
64 bytes from google.com (216.239.37.99): icmp_seq=4 ttl=242 time=181 ms
64 bytes from google.com (216.239.37.99): icmp_seq=5 ttl=242 time=180 ms
64 bytes from google.com (216.239.37.99): icmp_seq=6 ttl=242 time=181 ms
64 bytes from google.com (216.239.37.99): icmp_seq=7 ttl=242 time=177 ms

--- google.com ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7006ms
rtt min/avg/max/mdev = 177.277/180.314/185.087/2.619 ms
martina@ubuntu:~$ ping ubuntuforums.org
PING ubuntuforums.org (64.21.33.9) 56(84) bytes of data.
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=1 ttl=52 time=169 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=2 ttl=52 time=161 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=3 ttl=52 time=168 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=4 ttl=52 time=162 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=5 ttl=52 time=164 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=6 ttl=52 time=172 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=7 ttl=52 time=174 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=8 ttl=52 time=165 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=9 ttl=52 time=167 ms

--- ubuntuforums.org ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8006ms
rtt min/avg/max/mdev = 161.676/167.355/174.682/4.206 ms


Ping now works but no page display in firefox or synaptic update...

---

### Post by SilvioTO on 2005-05-11
Problem fixed.

The Router D-Link DSL-502T don't work in Linux with automatic ip assignment. In web interface of router configuration, you must specify DNS primary and secondary, and ip of router as gateway.

---

### Post by Andre O on 2005-05-28
I am using the **D-Link DSL-g604T** router, to which I am connected by cable (Ethernet).
In **live Ubuntu 5.04**,  I can ping all sites in the internet and I can as well connect to ftp servers. Firefox and synaptic, though, do not work - It is impossible to connect to and visualise any standard web site (my problem is thus similar to the one you have ecountered and resolved).

Could you please post a step by step solution for viewing websites on Live Ubuntu. I don't understand what exactly you mean by specifying "DNS primary and secondary, and ip of router as gateway". 

Thank you very much

---

### Post by Andre O on 2005-06-09
Everything OK now, I have resolved the problem thanks to the post by "python" on the following adress:

[http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router)

Actually, it should have been obvious: Firefox doesn't work even though you are connected to the Internet because it needs to find numeric server name equivalents to the internet adresses normally entered in the URL bar (ex. [http://www.ubuntuforums.org)](http://www.ubuntuforums.org)). And it can only achieve this with the help of the DNS service of your internet provider: thus, the DNS primary and secondary (DNS1 and DNS2) are the ones indicated by your ADSL connection provider...

---

