---
title: "OpenVPN + Website Access"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by thecaligarmo on 2015-10-24
So I've seen issues similar to the I'm having, but none of them seem to have what I'm having so I figured I'd ask.

Current setup: I'm using OpenVPN to tunnel into another server. After tunneling I'm able to ping everything properly:
```
root:~ $ ping 10.8.0.1
PING 10.8.0.1 (10.8.0.1) 56(84) bytes of data.
64 bytes from 10.8.0.1: icmp_seq=1 ttl=64 time=124 ms
```

When I try to access a particular ip everything seems to work properly.
```
root:~ $ ping 10.0.0.14
PING 10.0.0.14 (10.0.0.14) 56(84) bytes of data.
64 bytes from 10.0.0.14: icmp_seq=1 ttl=63 time=673 ms

```

Additionally, when I hit 10.0.0.14 from web browsers (FF and Chromium) everything works fine. (I setup a page that says 'test' which shows up properly)

The weird part. I also have a site that I have directly within the server. I can ping the site:
```
root:~ $ ping php.xxx.dev
PING php.xxx.dev (127.0.53.53) 56(84) bytes of data.
64 bytes from 127.0.53.53: icmp_seq=1 ttl=64 time=0.014 ms

```

But whenever I try and access the site from a browser it doesn't load. I get the error "Webpage not available: ERR_ICANN_NAME_COLLISION" (in FF).

Now for the really weird part. I tried connecting using a windows box. (I have a dual boot, so technically it's windows on the exact same machine). I set everything up, and I was ABLE to access the site from the browser.

So that's the weird part. Everything seems to work in Windows, but is failing in Ubuntu, but only when trying to use browsers. I'm assuming it's a DNS issue, but I don't know DNS well enough to be able to debug exactly what's going on. I tried a netstat and got:

```
root:~ $ netstat -nr http://php.xxx.dev/
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
10.0.0.0        10.8.0.25       255.255.255.0   UG        0 0          0 tun0
10.8.0.1        10.8.0.25       255.255.255.255 UGH       0 0          0 tun0
10.8.0.25       0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0

```

So it seems like something weird is going on? Any help would be greatly appreciated. If you need any more information just lemme know and I'll try and get it for you.

---

### Post by SeijiSensei on 2015-10-24
[http://superuser.com/questions/919278/err-icann-name-collision-when-trying-to-use-localhost-dev-in-chrome](http://superuser.com/questions/919278/err-icann-name-collision-when-trying-to-use-localhost-dev-in-chrome)

---

