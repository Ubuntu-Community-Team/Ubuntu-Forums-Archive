---
title: "Wired Connection Not Displaying"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by bigpappajohn1984 on 2014-09-11
I am connected to the internet as I am able to ping my router and navigate the web.  But when I type the following
```
[COLOR=#000000][FONT=Ubuntu Mono]nm-tool[/FONT][/COLOR]
```
This is the output that I get
```

Device: eth0
Driver: via-rhine
State: unmanaged
Default: No
HW Address: 00:1A:4D:0A:65:B7

Capabilities:
Carrier Detect: Yes
Speed: 100 MB/s

Wired Properties:
Carrier: on
```

And if I try this, it shows no active connections?!
```
[COLOR=#000000][FONT=Ubuntu Mono]nm-connection-editor[/FONT][/COLOR]
```

---

### Post by chili555 on 2014-09-11
> State: unmanagedI suspect this means that, since the device is listed in /etc/network/interfaces, Network Manager is not managing it and therefore has no details to report. If it's working as expected, I'd probably ignore it.> I am connected to the internet as I am able to ping my router and navigate the web.Perfect!

---

### Post by bigpappajohn1984 on 2014-09-11
Well - I am trying to set a static IP address for routing via FTP site.  How could I do such w/o seeing the info in the connection editor?

---

### Post by chili555 on 2014-09-11
See your address, etc. with:```
ifconfig
```If you are using /etc/network/interfaces, instead of NM for network settings, I'd make my static settings there; for example:```
auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```Get the system to re-read and use the settings:```
sudo ifdown eth0 && sudo ifup -v eth0
```Check:```
ifconfig
ping -c3 www.google.com
```Of course, substitute your specifics here.

---

### Post by bigpappajohn1984 on 2014-09-13
If I try the command
```

auto lo

```

I get the below error
```

123@ubuntu:~$ auto lo
No command 'auto' found, did you mean:
 Command 'uuto' from package 'uucp' (universe)
auto: command not found

```

---

### Post by chili555 on 2014-09-13
> **bigpappajohn1984 said:**
> If I try the command
```

auto lo

```

I get the below error
```

123@ubuntu:~$ auto lo
No command 'auto' found, did you mean:
 Command 'uuto' from package 'uucp' (universe)
auto: command not found

```That's not a command; that's the text I suggest you edit into /etc/network/interfaces if it's not already there. I assumed from your posts that you are somewhat advanced, but if you need some additional guidance, I will be happy to help.

---

### Post by bigpappajohn1984 on 2014-09-13
Oh wow, I did know that.  When I attempt to save the file referenced above I get this error
```

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

```

I am the only user on this computer so I do not know why I wouldn't have permissions.  I opened the file in gedit.

---

### Post by chili555 on 2014-09-13
Please try *sudo* gedit.

---

