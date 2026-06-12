---
title: "Wired networking problem after upgrading to 19.04"
date: 2019-06-05
forum: Networking &amp; Wireless
---

### Post by Allan Reed on 2019-06-05
I have a desk top system with Win10 and several Linux operating systems on different hard disks. The Win10 is the normal boot system for compatibility with work but I can select to boot a Linux system by using F11 on booting. Since upgrading to Ubuntu 19.04 when I power off the Ubuntu and go back to Win10 I find that I am not connected to the internet via the cable connection from my Realtek PCI GBit card. Even though powered off, the Ubuntu seems to be retaining the connection. I have found that switching the main power off the computer for 10 secs the restarting clears the problem. I have reloaded a new Ubuntu 19.04 instead of the upgraded system but the problem remains. It is a problem I can live with but I would appreciate any ideas to correct it.

---

### Post by crip720 on 2019-06-05
Don't know if it is related to your problem, but the new/recent driver can sometimes stop ubuntu from connecting to wired if the cable is plugged in during boot.  Are you shutting down ubuntu or just restarting computer to go back to windows?  The drivers I am talking about can be found on third post of this thread.  [https://ubuntuforums.org/showthread.php?t=2400056](https://ubuntuforums.org/showthread.php?t=2400056)

---

### Post by Allan Reed on 2019-06-06
No problem with ubuntu connecting to BT hub on rebooting, it's that the connection seems to be locked onto Ubuntu and not avaiable to Win10 after Ubuntu has been powered down and the computer booted into Win10.

---

### Post by chili555 on 2019-06-06
Hmmmm. Wake-on-lan??

Please run and post:```
ip add show
```This will give the interface name needed in the next steps. For example:```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s25: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 68:f7:28:ae:83:47 brd ff:ff:ff:ff:ff:ff

```In this example, the ethernet interface is enp0s25.

Next, run and post:```
sudo ethtool enp0s25
```Of course, susbstitute your relevant interface if not enp0s25.

ethtool may not be installed; if not, then:```
sudo apt update && sudo apt -y install ethtool
```

---

### Post by Allan Reed on 2019-06-06
output from ip add show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:25:22:7d:1c:4c brd ff:ff:ff:ff:ff:ff
3: enp4s5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0a:cd:2b:24:fd brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.87/24 brd 192.168.1.255 scope global dynamic noprefixroute enp4s5
       valid_lft 84706sec preferred_lft 84706sec
    inet6 fdaa:bbcc:ddee:0:51d6:5b66:4f39:8d9d/64 scope global temporary dynamic 
       valid_lft 603124sec preferred_lft 84696sec
    inet6 fdaa:bbcc:ddee:0:54cb:2154:a89:d5c0/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 2a00:23c5:2c88:d600:51d6:5b66:4f39:8d9d/64 scope global temporary dynamic 
       valid_lft 603124sec preferred_lft 84696sec
    inet6 2a00:23c5:2c88:d600:4f99:d461:4fa2:55b/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 315359962sec preferred_lft 315359962sec
    inet6 2a00:23c5:2c88:d600:7533:31bd:3621:ebb7/64 scope global temporary dynamic 
       valid_lft 603108sec preferred_lft 84680sec
    inet6 fdaa:bbcc:ddee:0:7533:31bd:3621:ebb7/64 scope global temporary dynamic 
       valid_lft 603108sec preferred_lft 84680sec
    inet6 fe80::9d57:b54a:85d6:e73b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


Output from sudo ethtool enp4s5

Settings for enp4s5:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Supported FEC modes: Not reported
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Advertised FEC modes: Not reported
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Link partner advertised FEC modes: Not reported
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

---

### Post by chili555 on 2019-06-06
Please try:```

sudo ethtool -s enp4s5 wol d


```Next, test and report.

Also, I wonder if the wake-on-lan setting in Windows changes the behavior. In other words, assuming you do not need WOL, toggle it off in Windows and test.

---

### Post by Allan Reed on 2019-06-06
No (blank) output from sudo ethtool -s enp4s5 wol d.

Will try changing Win10 wol settings.

---

### Post by chili555 on 2019-06-06
> 
No (blank) output from sudo ethtool -s enp4s5 wol d.
Perfect. In Linuxland, that means that the command was executed as requested and that there are no errors or warnings to report. It's just what we wanted.

---

