---
title: "Debian 5.0, DHCP, USB Modem issues"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Madonnas BoyToy on 2010-02-23
Okay, so here's my latest dilemma.

I recently re-installed Debian on my friend's ancient PC.  (The reason why I had to reinstall it is pretty detailed, so I'll leave that out).
The first time Debian was on it, the internet worked just fine via USB Cable Modem.

This time around however, for some reason, DCHP assignment fails, every time.
I've googled again and again, and tried multiple different 'solutions', but no avail.  

It's pretty much driving me crazy, but I'm not at my wit's end quite yet.

The PC is a Gateway 2000, with an Intel Pentium III
128 MB Ram; 10GB Hard Drive.
Debian Lenny

Please help if you can.

---

### Post by kerry_s on 2010-02-23
not really much info to go on. have you looked through the /var/logs to see if it shows any errors that could help?

---

### Post by superfrogman94 on 2010-02-23
try giving us the output of a few commands like

```
lsusb
``````
lshw
``````
ifconfig
```

---

### Post by Madonnas BoyToy on 2010-02-23
Let's see.  
Well, I couldn't find anything relevant to the issue in /var/log.

The output of lsusb:

```
debian:/home/molly# lsusb
Bus 001 Device 003: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 002: ID 0489:e007 Foxconn / Hon Hai 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Output of ifconfig:
```
debian:/home/molly# ifconfig
eth0      Link encap:Ethernet  HWaddr 90:4c:e5:33:10:cf  
          inet6 addr: fe80::924c:e5ff:fe33:10cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:276336 (269.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560 (560.0 B)  TX bytes:560 (560.0 B)

```

lshw - command not found

---

### Post by Madonnas BoyToy on 2010-02-23
Okay, well I feel like a complete and utter invalid right now.
I just reset the modem/router and that did the trick.  
Thanks for the help though.  :)

---

