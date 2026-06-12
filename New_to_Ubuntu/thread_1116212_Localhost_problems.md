---
title: "Localhost problems"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by wafflcommish on 2009-04-04
I'm trying to develop my own personal website using mySQL and php.  Everything was starting out ok, then one day my loopback address started not working.  I got that restarted, but ever since then, I cannot connect to sites on localhost, i.e., phpmyadmin or even my basic "hello world" page.  Any help would be appreciated.  

Thanks in advance,

Brian

---

### Post by Iowan on 2009-04-04
Post your */etc/hosts* file - and results of **ifconfig -a**.

---

### Post by wafflcommish on 2009-04-05
Post your /etc/hosts file - and results of ifconfig -a.

/etc/hosts:
27.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:19:21:32:1b:3a  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe32:1b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8386664 (8.3 MB)  TX bytes:7031122 (7.0 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6000 (6.0 KB)  TX bytes:6000 (6.0 KB)

Thanks!
Brian

---

### Post by halitech on 2009-04-05
have you tried restarting Apache?

```
sudo /etc/init.d/apache2 restart
```

---

### Post by nandemonai on 2009-04-05
> **wafflcommish said:**
> Post your /etc/hosts file - and results of ifconfig -a.

/etc/hosts:
27.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:19:21:32:1b:3a  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe32:1b3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8386664 (8.3 MB)  TX bytes:7031122 (7.0 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6000 (6.0 KB)  TX bytes:6000 (6.0 KB)

Thanks!
Brian

27.0.0.1 localhost should be 127.0.0.1 I'm assuming you just cut it accidentally in the paste though right?

---

### Post by albinootje on 2009-04-05
> **wafflcommish said:**
> 
/etc/hosts:
All looks fine, except that your hostname is not mentioned in /etc/hosts. Is your /etc/hostname OK ?

Can you change /etc/hosts into this :
```

# /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubuntu-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Where the "ubuntu-desktop" part is the hostname you should have in /etc/hostname.

---

### Post by wafflcommish on 2009-04-05
Ok, after adding the "localhost" line I can now get at "localhost" sites, thanks!  However I have another question.  When I enter "sudo /etc/init.d/apache2 restart", I get the following:

sudo: unable to resolve host server1
 * Restarting web server apache2                                                [Sun Apr 05 13:37:55 2009] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: apr_sockaddr_info_get() failed for server1
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting [Sun Apr 05 13:37:56 2009] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: apr_sockaddr_info_get() failed for server1
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]
So it runs, but is not perfectly clean.  Any ideas?  Thanks again.

---

### Post by halitech on 2009-04-05
not sure on the alias issue but for the 127.0.0.1 for the servername

taken from [http://www.webune.com/forums/how-to-fix-could-not-determine-the-servers-fully-qualified-domain-name-t23.html](http://www.webune.com/forums/how-to-fix-could-not-determine-the-servers-fully-qualified-domain-name-t23.html)

you have to edit the /etc/apache2/apache2.conf and, at the end of the file, add:

# added servername to avoid the could not determine fqdn error
servername myserver

place your server name in place of myserver.

(post #5)

---

