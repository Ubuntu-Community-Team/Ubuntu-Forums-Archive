---
title: "[SOLVED] how to adjust apt-get to use different internet connection than default"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by mkrahmeh on 2008-08-31
gurus
i connected my pc to a new DSL connection, browsing worked fine after changing the settings in firefox, but apt-get (through command line)
rendered disconnected..how do i adjust the apt-get to be able to connect through the new connection?
i searched in the related configuration files but found nothing that might help..moreover, the file /etc/apt/aptconf is not present in my system, which seems to be a problem
any suggestions??

---

### Post by dmizer on 2008-08-31
I'm not sure I completely understand what's going on here. What settings did you have to change in Firefox, and why?

What's the output of:
```
sudo ifconfig
```

---

### Post by mkrahmeh on 2008-09-01
```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:09:77:be
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe09:77be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3909207 (3.7 MB)  TX bytes:611543 (597.2 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3644 (3.5 KB)  TX bytes:3644 (3.5 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:79.173.235.152  P-t-P:194.165.130.206  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:3911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3801245 (3.6 MB)  TX bytes:506285 (494.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:f1:2b:16
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-F1-2B-16-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by mkrahmeh on 2008-09-01
am not sure if this output can help, since browsing is working fine..
i think the problem is something that has to do with configuring the apt itself

previously i had a connection through a proxy server, and firefox was set to connect through it, so i had to change it..thats all

---

### Post by dmizer on 2008-09-01
Do you have system wide proxy settings in place as well?

---

### Post by mkrahmeh on 2008-09-02
actually am not sure if i understood what you mean by system wide settings, but I defined proxy settings in the /etc/profile manually in form of exported variables..

---

### Post by dmizer on 2008-09-02
> **mkrahmeh said:**
> actually am not sure if i understood what you mean by system wide settings, but I defined proxy settings in the /etc/profile manually in form of exported variables..

Have you removed those proxy settings as well?

---

### Post by mkrahmeh on 2008-09-03
no, but all I did is that I configured firefox to use the new connection, by changing the settings of the network in preferences..
what I was trying is to change the network settings in the environment through which apt-get and others connect to the internet..
that's why i attempted to search for configuration files of the apt-get in the first place..
what to do now ??
do these progz use global variables or something for the purpose ?

---

### Post by mkrahmeh on 2008-09-03
looking through some of the manuals, i found that the apt-get looks for the variables ftp_proxy and http_proxy, and if found, they override all other settings..
so i had to comment the lines where i defined these variables in the 
/etc/profile

but what dazzles me is that there is no configuration file for the apt in my system (/etc/apt/apt.conf) :confused:
any explanations or suggestions ??

---

