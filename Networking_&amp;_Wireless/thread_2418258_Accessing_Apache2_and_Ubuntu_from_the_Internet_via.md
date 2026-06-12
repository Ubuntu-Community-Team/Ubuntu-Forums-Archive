---
title: "Accessing Apache2 and Ubuntu from the Internet via ipv6 (within LAN successful)"
date: 2019-05-04
forum: Networking &amp; Wireless
---

### Post by piezo2 on 2019-05-04
Hello,

I am trying to reach the Apache2 Ubuntu Default Website from the Internet by using odroid.[anonymized].myfritz.net but it fails. My browser on my Desktop-Computer says ERR_NAME_NOT_RESOLVED.

I can successfully reach the Apache2 Ubuntu Default Website on [http://192.168.178.52/](http://192.168.178.52/) from the LAN. The apache webserver is on a single board computer Odroid-N2 connected to a LAN cable. Ubuntu 18.04.2 (MATE DESKTOP) is running.

I can successfully ping from the Odroid-N2 to the Internet:

```

root@odroid:~# ping6 ipv6.google.com
PING ipv6.google.com(ham11s01-in-x0e.1e100.net ([anonymized])) 56 data bytes
64 bytes from ham11s01-in-x0e.1e100.net ([anonymized]): icmp_seq=1 ttl=56 time=7.83 ms
64 bytes from ham11s01-in-x0e.1e100.net ([anonymized]): icmp_seq=2 ttl=56 time=7.17 ms
64 bytes from ham11s01-in-x0e.1e100.net ([anonymized]): icmp_seq=3 ttl=56 time=7.03 ms
^C
--- ipv6.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 7.032/7.347/7.833/0.362 ms
```

A ping from [https://www.subnetonline.com/pages/ipv6-network-tools/online-ipv6-ping.php](https://www.subnetonline.com/pages/ipv6-network-tools/online-ipv6-ping.php) to odroid.[anonymized].myfritz.net is unsuccessful.

Just pinging the router works, the result is

```

IPv6 Ping Output:

PING [anonymized].myfritz.net([anonymized] ([anonymized])) 32 data bytes
40 bytes from [anonymized] ([anonymized]): icmp_seq=1 ttl=58 time=17.1 ms
40 bytes from [anonymized] ([anonymized]): icmp_seq=2 ttl=58 time=17.0 ms
40 bytes from [anonymized] ([anonymized]): icmp_seq=3 ttl=58 time=17.0 ms
40 bytes from [anonymized] ([anonymized]): icmp_seq=4 ttl=58 time=17.0 ms

--- [anonymized].myfritz.net ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 17.040/17.085/17.142/0.135 ms

 ---- Finished ------ 
```

My settings on my router are 

[ATTACH=CONFIG]283179[/ATTACH]

I am using the Dyn DNS service (myfritz.net) of the manufacturer of the router.

I would be grateful for your advice on how I can access the Apache2 Ubuntu Default Website from the Internet.

Kind regards,
piezo2

---

### Post by piezo2 on 2019-05-04
I was able to get a ping from outside, 

```
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 19.310/19.669/20.004/0.342 ms

 ---- Finished ------ 
```




but I still cannot access the Apache2 Ubuntu Default Page from the Internet.

---

### Post by piezo2 on 2019-05-04
I found the mistake by entering

```
apachectl -S
```

That gave the error: 

```
AH00526: Syntax error on line 9 of /etc/apache2/ports.conf:
Cannot define multiple Listeners on the same IP:port
Action '-S' failed.

```

So I went into ports.conf with 

```
sudo nano /etc/apache2/ports.conf
```

and removed one of the "443" that was there too many. Everything is working fine now.

---

