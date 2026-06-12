---
title: "Can I Find Other IP Address with Terminal ?"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by rachman2 on 2015-07-11
Like IP Scanner.....

---

### Post by QIII on 2015-07-11
arp-scan and nmap are two common command line utilities available in the Ubuntu repos.

Angry IP Scanner is a Java application with a graphical interface, but I don't think it's in the Ubuntu repos.  You'd have to add the PPA, which I don't recommend if you are new to Ubuntu.

---

### Post by Christopher_Walker on 2015-07-11
Try this: [HTML]arp -a[/HTML]
This utility should allow you to view other IP Adresses on your local network. Its available on most GNU/Linux systems. You can also display the devices by mac address by removing the "-a" from the command.

---

### Post by ajgreeny on 2015-07-11
If you can login to the admin page of your router, if you have one, you can probably see all the attached devices in a list with their IP addresses.

My router allows devices to have reserved IP addresses giving all of them the equivalent of a static IP, even though everything is actually all DHCP.
This is very useful particularly for devices such as printers which really need a static IP for discovery by computers when printing.

---

### Post by SeijiSensei on 2015-07-11
Install nmap with "sudo apt-get install nmap" then scan the network with
```
nmap -sP 192.168.1.0/24
```
replacing that IP address and mask with the one appropriate to your computer and network.

Once you've done that try some other scans using "sudo nmap" to see what you can learn about the other devices on your network.  Run "man nmap" at a terminal prompt to see the full documentation.

---

### Post by rachman2 on 2015-07-11
Can I Ping Other IP Address ?

---

### Post by SeijiSensei on 2015-07-12
Yes. Try pinging 8.8.8.8, the address of Google's public DNS server.

```

$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=19.9 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=18.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=17.9 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 17.938/18.958/19.989/0.852 ms

```
Some machines have firewalls that do not return pings.  You can also install the "traceroute" package if you're interested in seeing how your traffic gets to a remote host:
```

$ traceroute -n 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.100.1  1.466 ms  2.454 ms  2.458 ms
 2  192.168.1.1  2.998 ms  4.137 ms  4.144 ms
 3  96.230.114.1  9.754 ms  11.233 ms  11.380 ms
 4  130.81.191.116  14.487 ms 130.81.191.118  16.287 ms 130.81.191.116  15.431 ms
 5  * * *
 6  140.222.226.31  21.475 ms  22.116 ms 140.222.226.37  23.300 ms
 7  152.63.19.122  21.944 ms 152.63.19.45  21.459 ms 152.63.29.226  21.922 ms
 8  204.148.18.206  22.270 ms  19.654 ms  22.767 ms
 9  64.233.175.47  19.758 ms  22.889 ms 64.233.175.69  21.891 ms
10  8.8.8.8  21.300 ms  17.652 ms  20.475 ms

```
The first two entries are routers on my network.  The entry with all stars represents a machine that blocks pings.

---

### Post by Lars Noodén on 2015-07-13
> **rachman2 said:**
> Can I Ping Other IP Address ?

Or if you mean using [nmap](http://manpages.ubuntu.com/manpages/trusty/en/man1/nmap.1.html) to ping the other machine(s) you can do it like this:

```

nmap -sn -PE 192.168.1.0/24

```

New versions of nmap use -sn instead of -sP  to skip doing a full port scan.  The addition of -PE tells it to do just a ping and only a ping instead of adding the usual probes for www (80) and https (443).

---

