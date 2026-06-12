---
title: "Ethernet connection, Ubuntu 16.04.2 LTS (MATE), persistent name resolution failures"
date: 2017-02-11
forum: Networking &amp; Wireless
---

### Post by windsnow on 2017-02-11
I moved to Ubuntu MATE 16.04 from Linux Mint 17.2 about 2-3 weeks ago.  I did not experience the problem under consideration under Linux Mint.  


I am now experiencing random drops of internet access.  When such drops occur, I can no longer access new websites or new webpages, I cannot refresh webpages that are already open and I cannot launch new applications accessing the internet.  However, existing connections, such as live streams, live chats, downloads or applications, usually remain operational after the drops, even though they may also break from time to time along with the drop.


After a drop, when I am trying to access a new webpage or refresh an existing one, I receive the following browser message:


“This site can’t be reached


The webpage at [https://www.youtube.com/](https://www.youtube.com/) might be temporarily down or it may have moved permanently to a new web address.
ERR_NAME_RESOLUTION_FAILED”


(This message is different from the one that I receive when I intentionally turn the internet off:


“There is no Internet connection


Try:
Checking the network cables, modem, and router
Reconnecting to Wi-Fi
ERR_INTERNET_DISCONNECTED”)


Also, after a drop, the Network Manager continues to show that the internet/Ethernet connection is up, and the modem indicators also show that intenet connection is OK.  I have an ADSL modem.


The problem can be resolved by turning the modem off and then on.  After this, the internet connection is working as normal until the next drop.


I have changed my Ethernet driver from r8169 to r8168, and this reduced the frequency of the drops.  However, the drops still occur even though at a smaller frequency.


The output of $ dmesg | grep r816 immediately after a reboot is as follows:


```
[    1.588495] r8168: module verification failed: signature and/or required key missing - tainting kernel
[    1.588839] r8168 Gigabit Ethernet driver 8.041.00-NAPI loaded
[    1.589735] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.589741] r8168  Copyright (C) 2015  Realtek NIC software team <nicfae@realtek.com> 
[    1.589878] r8168 Gigabit Ethernet driver 8.041.00-NAPI loaded
[    1.590692] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.590695] r8168  Copyright (C) 2015  Realtek NIC software team <nicfae@realtek.com> 
[    1.648874] r8168 0000:06:00.0 enp6s0: renamed from eth1
[    1.660233] r8168 0000:05:00.0 enp5s0: renamed from eth0
[   34.452482] r8168: enp5s0: link up

```

However, after the first drop the output of  $ dmesg | grep r816 changes to:


```
[    1.589145] r8168: module verification failed: signature and/or required key missing - tainting kernel
[    1.589456] r8168 Gigabit Ethernet driver 8.041.00-NAPI loaded
[    1.590311] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.590317] r8168  Copyright (C) 2015  Realtek NIC software team <nicfae@realtek.com> 
[    1.590332] r8168 Gigabit Ethernet driver 8.041.00-NAPI loaded
[    1.591136] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.591139] r8168  Copyright (C) 2015  Realtek NIC software team <nicfae@realtek.com> 
[    1.640349] r8168 0000:05:00.0 enp5s0: renamed from eth0
[    1.664192] r8168 0000:06:00.0 enp6s0: renamed from eth1
[   34.388479] r8168: enp5s0: link up
[ 4949.392006] r8168: enp5s0: link down
[ 4952.412478] r8168: enp5s0: link up
[ 4966.412007] r8168: enp5s0: link down
[ 4969.432481] r8168: enp5s0: link up
[13409.440008] r8168: enp5s0: link down
[13412.460476] r8168: enp5s0: link up
[13425.460006] r8168: enp5s0: link down
[13428.480476] r8168: enp5s0: link up

```

The output of $ ping 8.8.8.8 after a drop is as follows:


```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=19.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=18.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=19.2 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=57 time=18.7 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=57 time=17.7 ms
64 bytes from 8.8.8.8: icmp_seq=6 ttl=57 time=17.6 ms

```

and so on




I would appreciate if anyone could advise what needs to be done to get rid of this annoying problem, as apart from this issue the performance of the system has been fantastic.

---

### Post by windsnow on 2017-02-12
[FONT=Ubuntu]I have updated the system via MATE's Welcome tool. I also updated the system via the terminal&#8217;s update and dist-upgrade instructions. I also updated the system via the System Update tool in the general menu. None of those solved the problem.

[/FONT]
[FONT=Ubuntu]I have tried a number of different fixes, including installation of the WICD manager and removal of resolveconf service. None of them totally resolved the issue, even though some tested configurations demonstrated improvement in the connection&#8217;s stability.

[/FONT]
[FONT=Ubuntu]I am now back to the default configuration with the only exception that I commented line &#8220;dns=dnsmasq&#8221; with # and set &#8220;manage=true&#8221; in /etc/NetworkManager/NetworkManager.conf. The problem still persists, but now I don&#8217;t have to turn the modem off and on manually to restore the connection; I can do it by disabling and re-enabling the connection in the Network Manager.

[/FONT]
[FONT=Ubuntu]What I noticed, however, is that when I disable the default active connection, the Network Manager generates a new active connection naming it enp5s0, and that this new connection has &#8220;enp5s0([set of digits constituting HWaddr])&#8221; as its Device under the Ethernet tab of the Edit connection menu, and &#8220;Link-Local only&#8221; as its Method under the IPv6 Settings tab of this menu. This new connection is apparently used to channel the data for the existing data streams from the internet (chats, videos, downloads, program exchanges) that remain operational even after I disable the default active connection. The default active connection has the &#8220;[set of digits constituting HWaddr]&#8221; as its Device and &#8220;Automatic&#8221; as its Method, while other parameters of the default connection and the newly generated connection are identical. Does it give any clue with regard to the changes to the configuration that I need to make to sort this issue out?[/FONT]

---

### Post by Hadaka on 2017-02-12
Hi, notice that both your dmesg outputs say..
```
r8168: module verification failed: signature and/or required key missing - tainting kernel
```
This is most often the result of secure boot or UEFI being active in bios...please access bios and disable 
Then boot and test wireless.
Thanks.

---

### Post by wildmanne39 on 2017-02-12
Post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by windsnow on 2017-02-13
> **Hadaka said:**
> Hi, notice that both your dmesg outputs say..
```
r8168: module verification failed: signature and/or required key missing - tainting kernel
```
This is most often the result of secure boot or UEFI being active in bios...please access bios and disable 
Then boot and test wireless.
Thanks.

Thank you for your response, Hadaka.

My pc is pretty old and it does not even have UEFI, I used the legacy mode for the installation.  So, I dont even know what I should disable.  Also, I don't use wireless atm, my question was about wired (Ethernet) connection.  

This line about tainted kernel appears to be quite regular when you change r8169 to r8168 - I saw this line in the forum posts where this change was discussed and nobody paid any attention to or was alarmed by this line.

---

### Post by windsnow on 2017-02-13
> **wildmanne39 said:**
> Post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks


Here it is

```
$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8168
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8168
```

---

### Post by wildmanne39 on 2017-02-13
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

You may want to go into network manager and change the MTU setting from automatic to 1492 then save the changes and reboot. Installing that driver usually fixes the issue with this ethernet card.

---

### Post by windsnow on 2017-02-13
[SIZE=2]> **wildmanne39 said:**
> 

You may want to go into network manager and change the MTU setting from automatic to 1492 then save the changes and reboot. Installing that driver usually fixes the issue with this ethernet card.

Didn't help so far.

I set the MTU setting under the Ethernet tab of the network manager to 1492 bytes and then rebooted.  In about half an hour a disconnect occured.

I then changed [/SIZE][COLOR=#000000][FONT=Ubuntu][SIZE=2]/etc/NetworkManager/NetworkManager.conf back to the defaults, i.e. uncommented dns=dnsmasq and set manage=false, and rebooted.  Another disconnect occured in about an hour and a half.  Disabling the default active connection in the network manager after the disconnect leads again to the network manager generating a new connection "enp5s0", and the internet is up again (no more name resolution problem, until the next disconnect).

The output of my *$ ip addr* is as follows:

[/SIZE][/FONT][/COLOR]```
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <mac:address> brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.2/24 brd 192.168.1.255 scope global dynamic enp5s0
       valid_lft 85632sec preferred_lft 85632sec
    inet6 fe80::611d:854e:9c47:68ed/64 scope link 
       valid_lft forever preferred_lft forever
3: enp6s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <mac:address> brd ff:ff:ff:ff:ff:ff



```

My /etc/network/interfaces is currently

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

[COLOR=#000000][FONT=Ubuntu][SIZE=2]Could it be of any help in my situation if I add a static IP assignment to[/SIZE][/FONT][/COLOR]/etc/network/interfaces[COLOR=#000000][FONT=Ubuntu][SIZE=2], along the lines of [/SIZE][/FONT][/COLOR]https://ubuntuforums.org/showthread.php?t=2352231?  It would look like:[COLOR=#000000][FONT=Ubuntu][SIZE=2]

[/SIZE][/FONT][/COLOR]```

[SIZE=2]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

[COLOR=#000000][FONT=Ubuntu]auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1[/FONT][/COLOR][/SIZE]
```[COLOR=#000000][FONT=Ubuntu][SIZE=2]

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][SIZE=2]Also, when I removed resolveconf service and Network Manager in one of my previous attempts to fix this, and installed WICD instead, I had a stable connection for several hours.  My /etc/resolve.conf was as follows:

[/SIZE][/FONT][/COLOR]```
domain Home
search Home
nameserver 192.168.1.1
nameserver 192.168.1.1
```[COLOR=#000000][FONT=Ubuntu][SIZE=2]

And this was a static file, not a dynamic link as it is now under the default Network Manager configuration.  In the light of the *$ ip addr *output above, could it be of any help if I implement again this WICD configuration and add "[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]nameserver 127.0.0.1" [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][SIZE=2]to /etc/resolve.conf above?  It would look like:

[/SIZE][/FONT][/COLOR]```
[SIZE=2]domain Home
search Home
nameserver 192.168.1.1
nameserver 192.168.1.1
[COLOR=#000000][FONT=Ubuntu]nameserver 127.0.0.1[/FONT][/COLOR][/SIZE]
```[COLOR=#000000][FONT=Ubuntu][SIZE=2]


My /etc/resolve.conf currently, under the default Network Manager configuration, is

[/SIZE][/FONT][/COLOR]```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1
nameserver 127.0.1.1

search Home
```
[COLOR=#000000][FONT=Ubuntu]
Thanks a lot for your help.
[/FONT][/COLOR]

---

### Post by praseodym on 2017-02-14
> ```
[    1.590332] r8168 Gigabit Ethernet driver 8.0[COLOR="#FF0000"]41[/COLOR].00-NAPI loaded
```

Check driver version 43 instead:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb
sudo dpkg -i r8168-dkms_8.043.02-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

---

