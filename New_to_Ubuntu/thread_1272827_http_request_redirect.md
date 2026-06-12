---
title: "http request redirect"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Snipershot on 2009-09-22
I got an application thats configured to connect to a certain adress, going trough it to change the adress is a very very tedious task. So I was wondering if there is a simple way to make it so that when an application tries to communicate with [http://xxxxx.com/x](http://xxxxx.com/x) it would instead try to communicate with [http://yyyyy.com/y](http://yyyyy.com/y)

---

### Post by credobyte on 2009-09-22
You should be able to fool it by adding an entry to your hosts file.

```
cat /etc/hosts

```

---

### Post by mac9416 on 2009-09-22
First, find the IP address of yyyyy.com here: [http://www.selfseo.com/find_ip_address_of_a_website.php](http://www.selfseo.com/find_ip_address_of_a_website.php)
Then, add a line to /etc/hosts...
```
$ sudo nano /etc/hosts
```
where it looks something like...
> 127.0.0.1         localhost
127.0.1.1         mac9416-laptop
<ip address here> xxxxx.com
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Unfortunately, this only directs the program to yyyyy.com and not yyyyy.com/y. I suggest you make sure /x and /y are the same. If you can't, this is going to take more than I know how to do. :-)

I added "74.125.43.105 mac9416.com" to my /etc/hosts file, so mac9416.com now equals Google. And if I use mac9416.com/x, I get a 404 from Google.

Good luck
-mac

---

