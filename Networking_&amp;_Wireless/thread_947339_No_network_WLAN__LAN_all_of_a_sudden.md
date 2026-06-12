---
title: "No network WLAN / LAN all of a sudden"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by heinz57g on 2008-10-14
had a (wubi installed) version of UBUNTU on my laptop for
6 months, regular updates, last one some 10+ days ago.

all worked fine, constant connection to the router on LAN,
and occasionally on trip to a WLAN, also no problems.

just came back from a weekend trip (without laptop, for 
once), turned it on, and there is no network connection
at all - not the normal LAN, nor, after trying that too,
any connection to a WLAN - nothing.

everything else works fine, even the bluetooth mouse ...

am baffeled because of the initial logic, nothing to do with
X or ubuntu as such, or even the laptop: [I]works on friday,
sits untouched over the weekend, does not see any networks
on monday at all.[/I]

where do i start looking?

greetings    - heinz -

---

### Post by superprash2003 on 2008-10-14
in your terminal type ifconfig and post output.. are you able to ping/access your router?

---

### Post by heinz57g on 2008-10-14
will do in a few minutes - doubt though it is the router, works
fine on two other WIN computers and another linux (not mine) laptop.

actually, even on the WIN on the same computer. remember, this UBUNTU
is in a WUBI installation, in a 'container' file.

under WIN it pings fine.

and the router anyhow would have nothing to do with the WLAN also
not connecting, no?

greetings       - heinz -

---

### Post by heinz57g on 2008-10-14
here it is:

~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:170300 (166.3 KB)  TX bytes:170300 (166.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:d3:6d:56:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-6D-56-53-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2008-10-15
please post output of lshw -C network .. we first need to see if ubuntu recognizes your card

---

### Post by heinz57g on 2008-10-15
prashant, slow pls: where do i put this command ''lshw -C network'' ?

and which card should it recognize, since, i assume, WLAN and LAN are
different cards anyhow?

greetings      - heinz -

---

### Post by superprash2003 on 2008-10-16
sorry.. go to the terminal(Applications->Accessories->terminal) and type in that command.. you would get an output.. highlight it and copy paste it here.. im hoping we could find drivers for both.. the output of that command should tell us that..

---

### Post by heinz57g on 2008-10-16
copy/paste from the terminal into a WIN system started
later does not work, have to find another solution again.

also, how can these drivers just have vanished, me not even
touching the computer?

that question bugs me most, as i was under the impression
UBUNTU wld be at least as solid as WIN XP.

greetings    - heinz -

---

### Post by heinz57g on 2008-10-16
here we are again:

xxxxxx: ~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network:0 DISABLED    
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: af:ab:55:55:bb:af
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28
         latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wmaster0
       version: 01
       serial: 00:13:d3:6d:56:53
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64
         module=rt2500pci multicast=yes wireless=IEEE 802.11g

xxxxxxx: ~$

---

### Post by superprash2003 on 2008-10-17
this could happen incase you upgrade your ubuntu or the kernel.. anyways try this link [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by heinz57g on 2008-10-18
prashant, tks, but i am lost here, the link you gave refers
to an older version of UBUNTU, not my 8.04, and most of the
'answers' there sound like chinese to me. and refers mainly
to WLAN anyhow.

**nothing tells me what to actually DO!**

sorry, but this means goodbuy UBUNTU, back to WIN for me. 
can you just imagine what it would have meant on my office
laptop to be out-of-work for a week plus, with no fix even
in sight, if i had not had WIN XP in the background, working
fine? i could have lost my job.

 *>> this could happen incase you upgrade your ubuntu*

an upgrade destroys a perfectly working system to the point 
of not being accessible at all, both LAN **as well as** WLAN 
affected? you are not joking? even the worst of WIN progs
have not done this over the years, and even if there was a
hiccup, there was a fix avaiable shortly. here now i am 
sitting since a week++ and have no solution in sight. great.

tks a lot for yr assistance, but i guess i will give up. on
this computer for sure.

greetings      - heinz -

PS: going back to older kernels (option while logging in)
does not help either.

---

