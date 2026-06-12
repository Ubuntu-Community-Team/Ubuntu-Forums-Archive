---
title: "Wired Broadband not working after upgrading to Ubuntu 11.04"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by JnkPanchal008 on 2011-07-06
Hi All,

Recently I upgraded my Ubuntu 10.10 to 11.04.
After upgradation wired broadband is not working.

I tried deleting and creating new DSL connection. Not worked.

Removed and re-installed pppoeconf. Not worked.

Now I don't know what to do.:confused:

Please help.

P.S.: I have also installed Vista in other partition so I can confirm broadband is working in Vista.

---

### Post by smurphy_it on 2011-07-06
Probably drivers.  Post the results of the following commands:

```
sudo lshw -C network
```
```
sudo lspci
```

---

### Post by JnkPanchal008 on 2011-07-07
Hi, Thnx for your reply.
But I don't think its drivers, 'coz it was working in Ubuntu 10.10.

So drivers must be included in this version also.

Anyways results of the commands you told are in the attached file.

Thnx again.

---

### Post by wildmanne39 on 2011-07-07
> **JnkPanchal008 said:**
> Hi, Thnx for your reply.
But I don't think its drivers, 'coz it was working in Ubuntu 10.10.

So drivers must be included in this version also.

Anyways results of the commands you told are in the attached file.

Thnx again.
Hi, here is a link that will get your wireless working, follow the directions for the 4311 card that is your card.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by JnkPanchal008 on 2011-07-07
> **wildmanne39 said:**
> Hi, here is a link that will get your wireless working, follow the directions for the 4311 card that is your card.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

Thnx for help buddy. It is a different issue with my HP laptop.

but currently I am having trouble connecting wired broadband.:)

---

### Post by alphacrucis2 on 2011-07-07
> **JnkPanchal008 said:**
> Hi, Thnx for your reply.
But I don't think its drivers, 'coz it was working in Ubuntu 10.10.

So drivers must be included in this version also.

Anyways results of the commands you told are in the attached file.

Thnx again.


A driver that worked in 10.10 could still be broken in 11.04. This is known as a regression. I recommend trying smurphy_it's commands and reporting back with what drivers are actually in use.

---

### Post by JnkPanchal008 on 2011-07-07
> **alphacrucis2 said:**
> A driver that worked in 10.10 could still be broken in 11.04. This is known as a regression. I recommend trying smurphy_it's commands and reporting back with what drivers are actually in use.

Results of those commands are in attached text file in reply of smurphy_it's.

---

### Post by alphacrucis2 on 2011-07-07
> **JnkPanchal008 said:**
> Results of those commands are in attached text file in reply of smurphy_it's.

e100 driver. What do you get from:

```
ip link show
```

and 

```
ifconfig -a
```

---

### Post by JnkPanchal008 on 2011-07-07
HI, here are results:

```
jacky@ubuntu:~$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:16:d3:a8:eb:cd brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:1a:73:78:1f:67 brd ff:ff:ff:ff:ff:ff
4: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff

```

```
jacky@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d3:a8:eb:cd  
          inet6 addr: fe80::216:d3ff:fea8:ebcd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2720 errors:0 dropped:43 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:328747 (328.7 KB)  TX bytes:21143 (21.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1048 (1.0 KB)  TX bytes:1048 (1.0 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:78:1f:67  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by smurphy_it on 2011-07-07
What happens with:

```
sudo dhclient eth0
```
```
ifconfig -a eth0
```

---

### Post by JnkPanchal008 on 2011-07-07
```
jacky@ubuntu:~$ sudo dhclient eth0
[sudo] password for jacky: 
jacky@ubuntu:~$ ifconfig -a eth0
eth0      Link encap:Ethernet  HWaddr 00:16:d3:a8:eb:cd  
          inet6 addr: fec0::b:216:d3ff:fea8:ebcd/64 Scope:Site
          inet6 addr: 2002:1b79:672b:b:216:d3ff:fea8:ebcd/64 Scope:Global
          inet6 addr: fe80::216:d3ff:fea8:ebcd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3567 errors:0 dropped:46 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464760 (464.7 KB)  TX bytes:36605 (36.6 KB)

```

Running first command nothing happens. Just cursor blinks for about a minute.

Can you tell me what is wrong?

---

### Post by smurphy_it on 2011-07-11
Looks like Eth0 is working as expected.  I'd suspect something is amuck with the dsl settings.  Which I've never done as I don't have DSL.

---

### Post by JnkPanchal008 on 2011-07-12
> **smurphy_it said:**
> Looks like Eth0 is working as expected.  I'd suspect something is amuck with the dsl settings.  Which I've never done as I don't have DSL.

Oh! okay.

Can anyone help me out?????? ](*,)

---

### Post by Swagman on 2011-07-12
usual question

Is your ISP BT and are you using their HomeHub ?

---

### Post by smurphy_it on 2011-07-12
Doesn't the configuration of pppoe supposed to create a new ppp0 device ?  I see from looking at the previous ifconfig -a command, that device doesn't exist.

What does your /etc/network/interfaces file say ?

```
sudo cat /etc/network/interfaces
```

Surprising this file isn't updated after you've re-done the 'sudo pppoeconf'.  

I've seen other posts in relation to DSL problems, but their eth0 device was set to a static IP address, and then the dsl-provider information was stored within the /etc/network/interfaces file.

Finally another post started the DLS connection with "sudo pon dsl-provider"

---

### Post by JnkPanchal008 on 2011-07-12
Hi!! Thank u all for helping.

It was something wrong with GUI config Utility of Ubuntu.
Using System>Preferences>Network Connections, I created dsl connection that worked in 10.10 but not in 11.04.

So I recreated that dsl connection the same way but that also not worked.

And after helpful commands suggested by you people.

I did sudo pppoeconf using terminal and it worked.

and still tray icon does not show any network connected, but I can access my broadband.

This is it. May be it's a bug.

---

### Post by JnkPanchal008 on 2011-07-12
Also ubuntu software center show no network connection while synaptic and update manager is working fine.

---

### Post by JnkPanchal008 on 2011-07-12
> **JnkPanchal008 said:**
> Also ubuntu software center show no network connection while synaptic and update manager is working fine.

After updating and rebooting that also worked.

---

