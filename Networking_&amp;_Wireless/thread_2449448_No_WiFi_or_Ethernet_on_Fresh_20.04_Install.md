---
title: "No WiFi or Ethernet on Fresh 20.04 Install"
date: 2020-08-26
forum: Networking &amp; Wireless
---

### Post by bunik on 2020-08-26
Hi All, 

I performed a fresh install of 20.04 on my ODROID-H2+ and upon completion there was no connection to the internet...

I figured this was odd and went to the 'Network' tab in 'Settings' and the only options that were available are 'VPN' and 'Network Proxy'. 

In short, I have no connection to the internet via ethernet or WiFi and I need help... is there a driver I can download from a separate computer and install on my ODROID? Any and all help is appreciated. I have scoured the internet for answers with zero-to-little progress.

---

### Post by chili555 on 2020-08-26
According to these specifications, there is no wifi: [https://ameridroid.com/products/odroid-h2](https://ameridroid.com/products/odroid-h2)

As for the RTL8125B ethernet, these links may help: [https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04](https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04)

[https://askubuntu.com/questions/1213999/how-do-i-get-a-rtl8125-2-5gbe-controller-working-on-18-04-lts](https://askubuntu.com/questions/1213999/how-do-i-get-a-rtl8125-2-5gbe-controller-working-on-18-04-lts)

Which kernel version are you running?

```
uname -r
```

Are there any clues here?

```
dmesg | grep r816
dmesg | grep -i rtl
```

---

### Post by bunik on 2020-08-27
> **chili555 said:**
> According to these specifications, there is no wifi: [https://ameridroid.com/products/odroid-h2](https://ameridroid.com/products/odroid-h2)
Yes, thank you. I was more alluding to the fact that it isn't an option to help troubleshooting purposes. 

> **chili555 said:**
> As for the RTL8125B ethernet, these links may help: [https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04](https://askubuntu.com/questions/1259947/cant-get-rtl8125b-working-on-20-04)

[https://askubuntu.com/questions/1213999/how-do-i-get-a-rtl8125-2-5gbe-controller-working-on-18-04-lts](https://askubuntu.com/questions/1213999/how-do-i-get-a-rtl8125-2-5gbe-controller-working-on-18-04-lts)
When I go through these links I receive the following: 

'Check old driver and unload it.
rmmod 8169
Build the module and install
autorun.sh: 30: make: not found'

When I try to run 'rmmod 8169' I run into the following error: 
'rmmod: ERROR: Module r8169 is not currently loaded'

Little stuck about what to do here. I have the drivers on a thumb drive and I'm trying to install from there. 

> **chili555 said:**
> Which kernel version are you running?

```
uname -r
```[LEFT][COLOR=#222222][FONT=Verdana][/FONT][/COLOR][/LEFT]

5.4.0-42-generic

[LEFT][COLOR=#222222][FONT=Verdana]> **chili555 said:**
> [/FONT][/COLOR][/LEFT]Are there any clues here?

```
dmesg | grep r816
dmesg | grep -i rtl
```

This is what I receive: 

[     1.079972] r8169 0000:02:00.0: unknown chip XID 641
[     1.080152] r8169 0000:03:00.0: unknown chip XID 641

ANY further help is greatly appreciated; thank you so much.

---

### Post by chili555 on 2020-08-27
We are stuck in a dilemna. Shall we try the method that is hard or shall we try the method that is very, very hard? Hmmm...

The very, very hard method is to download and install make and its dependencies and the dependencies of the dependencies until we are half insane and finally the install.sh runs and installs the driver. We will also find that firmware is recommended and we'll find it and install it, too. Whew!

The merely hard method is that many posts suggest that later kernel versions include the driver by default. We could either download and install a mainline kernel version 5.9 or so along with it's merely two depndencies. We'd still need the firmware.

Another alternative is to try a live session of Ubuntu 20.10 from here: [http://www.cdimage.ubuntu.com/daily-live/current/](http://www.cdimage.ubuntu.com/daily-live/current/) If the ethernet works and all other features work as you expect, either install it, or else, check the kernel version:

```
uname -r
```

...and we'll download and install the mainline kernel as above.

I will be happy to help in any case.

---

### Post by bunik on 2020-08-27
I actually was able to get ethernet to show in the Network settings from following this tutorial, here: [https://wiki.odroid.com/odroid-h2/hardware/install_ethernet_driver_on_h2plus](https://wiki.odroid.com/odroid-h2/hardware/install_ethernet_driver_on_h2plus)

However, the problem that persists is that the 'Connection failed; Activation of network connection failed' and the ethernet is stuck 'connecting' and will fail to initialize. 

Thank you for your help so far; the error message from 'dmesg' was what allowed me to find that wiki post; however, I'm now stuck on the connection issue... getting close though.

---

### Post by chili555 on 2020-08-27
What is the interface name? enp-someting?

```
ip addr show

```
Are there any clues in the log?

```
dmesg | grep -e enp -e r816
```

---or eno or eth or whatever your ethernet interface is named.

---

### Post by bunik on 2020-08-27
> **chili555 said:**
> What is the interface name? enp-someting?

```
ip addr show

```

```
brendan@ODROID0:~$ ip addr show1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1e:06:45:30:36 brd ff:ff:ff:ff:ff:ff
3: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:1e:06:45:30:37 brd ff:ff:ff:ff:ff:ff
```

Are there any clues in the log?

```
dmesg | grep -e enp -e r816
```

```
brendan@ODROID0:~$ dmesg | grep -e enp -e r816
[    4.418685] r8125 0000:02:00.0 enp2s0: renamed from eth0
[    4.437253] r8125 0000:03:00.0 enp3s0: renamed from eth1
[    5.854942] enp2s0: 0xffffb7ee40700000, 00:1e:06:45:30:36, IRQ 133
[    6.437662] enp3s0: 0xffffb7ee407e0000, 00:1e:06:45:30:37, IRQ 135
[   24.219204] r8125: enp2s0: link up
[   24.222259] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   24.377462] r8125: enp2s0: link down
[   30.300865] r8125: enp2s0: link up
[   55.893584] r8125: enp2s0: link down
[   62.044215] r8125: enp2s0: link up
[   85.717424] r8125: enp2s0: link down
[   91.724906] r8125: enp2s0: link up
[  115.413354] r8125: enp2s0: link down
[  121.437376] r8125: enp2s0: link up
[  121.444105] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[  187.093978] r8125: enp2s0: link down
[  888.350835] r8125: enp2s0: link up
```



---or eno or eth or whatever your ethernet interface is named.

Thank you again for your help so far; I wouldn't be this far without you!

---

### Post by chili555 on 2020-08-27
Is Network Manager installed and in control here? Are there any clues here?

```
dmesg | grep etwork

cat /etc/netplan/*.yaml

cat /etc/NetworkManager/NetworkManager.conf
```

---

