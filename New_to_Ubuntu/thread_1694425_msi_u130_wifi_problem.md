---
title: "msi u130 wifi problem"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by spacedoubtcowboy on 2011-02-24
have installed ubuntu 10.10 and the wifi is showing that it is connected and picking up wireless options but will not actually connect to internet  or allow downloads through torrent programs. any ideas?

---

### Post by komputes on 2011-02-24
Can you right click network manager applet and select connection information. What is the first octet (part.x.x.x) of the IP address?

Are you able to ping google? Open a terminal and run the command:
```
$ ping google.com
```

Are you able to ping google by IP address?
```
$ ping 74.125.225.20
```

---

### Post by asampau on 2011-02-27
> **komputes said:**
> Can you right click network manager applet and select connection information. What is the first octet (part.x.x.x) of the IP address?

Are you able to ping google? Open a terminal and run the command:
```
$ ping google.com
```Are you able to ping google by IP address?
```
$ ping 74.125.225.20
```

I have similar situation. In my wifi network I have 2 notebooks connected.
One have they have different repospose times as ping from the same host.

This is a win machine.
--- 192.168.0.64 ping statistics ---
111 packets transmitted, 111 received, 0% packet loss, time 111091ms
rtt min/avg/max/mdev = 0.891/7.781/204.965/32.440 ms

This is a U130 netbook running Ubuntu 10.10
--- 192.168.0.57 ping statistics ---
102 packets transmitted, 102 received, 0% packet loss, time 102016ms
rtt min/avg/max/mdev = 1.604/75.122/987.642/96.088 ms

Any ideas what is the possible cause of this?

---

### Post by spacedoubtcowboy on 2011-03-01
that did not work it said wrong command prompt. i found a section of code a while back that i cut and pasted in to terminal and it worked but stupidly did not save the link and now cant find it again. sorry i cant be more helpfull

---

