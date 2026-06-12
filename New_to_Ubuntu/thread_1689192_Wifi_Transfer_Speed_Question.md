---
title: "Wifi Transfer Speed Question"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-02-16
I have a kinda off topic questions I cant understand.  I have a wireless N in my laptop, wireless N in my other computer and wireless N for my WIFI Router.  When I transfer files from 1 computer to another via WIFI (on windows or ubuntu) I transfer between 3 - 4 MBps.  Doesnt that seem kind of low for wireless N?  When I transfer with ethernet I transfer at around 10 MBps.  

Can someone explain why it is this slow and possibly even let me know how to increase it?  Thank you

---

### Post by cariboo on 2011-02-16
Network transfer speeds will only be as fast as the slowest device on the system. To test your transfer speeds properly I would suggest you install iperf, it's in the repositories. There is also a windows version available. This is a command line utility. Install iperf on one system and run it as a server using the following command:

```
iperf -s
```

on the client start iperf using the following command:

```
iperf -c <server name or ip address>
```

On my netbook with a standard BCM4312 running at 54Mb I get the following result:

```
iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.250 port 5001 connected with 192.168.1.106 port 55705
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.2 sec  29.2 MBytes  24.1 Mbits/sec
```

which works out to 3Mbps. In real life I average about 2Mbps

---

### Post by pl@yer on 2011-02-16
> **cariboo907 said:**
> 
which works out to 3M**B**ps. In real life i average about 2M**B**ps

ftfy :)

---

### Post by hunter99507 on 2011-02-16
So I did the test and it seems slow to me. I had 17.02 Mbps write and 15.73 Mbps speed. That seems pretty slow for wireless N on all sides.  Is their anyway i can tweak these settings to make it faster?

---

### Post by Paqman on 2011-02-16
First thing i'd do is try changing the location of the router. The part of the spectrum wifi is on is clogged full of competing devices that all interfere with each other. Plug it into a different phone socket and see if your speed changes.

---

### Post by grahammechanical on 2011-02-16
Here is a link the the wikipedia article

[http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)

Notice the mention of maximum and average bit rates. Notice how the bits rates increase by segments. I guess that the device needs to work up to speed. It may only get to full speed for very large files.

Regards.

---

### Post by pl@yer on 2011-02-17
I had tried wireless N back in 2008.
I ended up getting 16-20Mb/s with it sitting next to the router. I have read that it might help enabling AES encryption on the router.

---

### Post by add1kt on 2011-12-26
some things to consider:
[http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed](http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed)

Also I use dd-wrt, and I forget where it was mentioned, but it was recommended that XMT pwr of the router be set to about 30 mW (assuming you don't need a lot of range).  With the above suggestions taken into account, using Debian 6.0 and ASUS USB N-13 wireless n device I get xfer speeds to a wired client on my LAN at 54-64 Mb/s (7-8 MB/s).  I can't test wireless to wireless because my other computer is a "g" client.

When I connect using 802.11g I see speeds at 2-3 MB/s.  So it's worth noting the vastly increased xfr speeds.

---

