---
title: "help with permissions"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by wlraider70 on 2010-06-13
I'm working on getting Bind9 to work. I seem to be having a permission issue

If you look at my code I was told permission denied

so then I set it to the lowest level permission

yet its still denied.


What am i missing, 


```


luke@media:~$ named -g -p 53
12-Jun-2010 23:46:09.053 starting BIND 9.5.1-P2.1 -g -p 53
12-Jun-2010 23:46:09.055 found 1 CPU, using 1 worker thread
12-Jun-2010 23:46:09.057 using up to 4096 sockets
12-Jun-2010 23:46:09.064 loading configuration from '/etc/bind/named.conf'
12-Jun-2010 23:46:09.064 none:0: open: /etc/bind/named.conf: permission denied
12-Jun-2010 23:46:09.065 loading configuration: permission denied
12-Jun-2010 23:46:09.065 exiting (due to fatal error)

**luke@media:~$ sudo chmod 777 /etc/bind/named.conf**
[sudo] password for luke: 

luke@media:~$ named -g -p 53
12-Jun-2010 23:47:26.418 starting BIND 9.5.1-P2.1 -g -p 53
12-Jun-2010 23:47:26.418 found 1 CPU, using 1 worker thread
12-Jun-2010 23:47:26.419 using up to 4096 sockets
12-Jun-2010 23:47:26.425 loading configuration from '/etc/bind/named.conf'
12-Jun-2010 23:47:26.425 none:0: open: /etc/bind/named.conf: permission denied
12-Jun-2010 23:47:26.426 loading configuration: permission denied
12-Jun-2010 23:47:26.426 exiting (due to fatal error)
luke@media:~$ 

luke@media:~$ sudo /etc/init.d/bind9 start
 * Starting domain name service... bind9                                 [fail] 
luke@media:~$ /etc/init.d/bind9 start
 * Starting domain name service... bind9                                        chmod: changing permissions of `/var/run/bind/run': Operation not permitted
named: chroot(): Operation not permitted
                                                                         [fail]


```

---

