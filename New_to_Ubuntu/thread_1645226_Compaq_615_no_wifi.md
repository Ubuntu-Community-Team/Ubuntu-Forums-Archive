---
title: "Compaq 615 no wifi"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by stamatiou on 2010-12-14
Hey guys, I have the Hp Compaq 615 but in the beginnings it hadn't wifi...
So I installed a package named broadcom-sta-common and it worked, then I installed Kubuntu and did the same thing so I fixed it the Same way but I switched back to ubuntu....
Finally today I installed kubuntu again, in the beginning the same problem and I installed the package but nothing worked....

---

### Post by fatharraxman on 2010-12-14
```
sudo apt-get install wireless-tools
```
then find out what with
```
lspci | grep Network
```

---

### Post by stamatiou on 2010-12-14
I did that and it replied
```
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```
What Should I do now?

---

### Post by jaykubun on 2010-12-14
Hello there!

Sorry to hijack this thread - kind of but i was about to post a very similar question... I also had my wifi already working with kubuntu 10.10 on my Dell Vostro 3700. After a suggested kernel update I lost my wifi capabilities. here is the infos that might be relevant:

```

$uname -r
2.6.35-23-generic

``````

$lspci | grep Net
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
``````
$sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fb400000-fb403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 03
       serial: f0:4d:a2:9b:9e:81
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.59 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:d000(size=256) memory:d2c04000-d2c04fff memory:d2c00000-d2c03fff memory:fb300000-fb31ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```When I go to Applications->System->Additional drivers I see two Broadcom dirvers, namely Broadcom STA and Broadcom 802.11n. I tried to activate first one, then the other  and also both, but with no change in the behavior. Currently the Additional driever panel states that the Broadcom 802.11n is activated and in use. Well, that is apparently not the case. 
In Network Manager there is a checkbox "Enable wireless" that is checked, but no network appears.

Neither ifconfig nor iwconfig show my wlan.

What is going wrong here? Please help, for I am pretty lost at this point.

Cheers,
Jay

---

### Post by fatharraxman on 2010-12-14
did you try System > Administration> Additional Drivers  then set it ti SAT ? if not try it then check MAC password and feedback
good luck

---

### Post by stamatiou on 2010-12-14
Ok thanks man....
I don't know what exactly happened but I went to Additional drivers and it wasn't installed so I clicked Activate and bingo!:p:P:):D:p;):D

---

### Post by fatharraxman on 2010-12-14
> **jaykubun said:**
> Hello there!


[/code]When I go to Applications->System->Additional drivers I see two Broadcom dirvers, namely Broadcom STA and Broadcom 802.11n. 
Cheers,
Jay

oh sorry you did hat !

---

### Post by fatharraxman on 2010-12-14
> **stamatiou said:**
> Ok thanks man....
I don't know what exactly happened but I went to Additional drivers and it wasn't installed so I clicked Activate and bingo!:p:P:):D:p;):D

cheers 
happy for you 
tag soved if it is solved
:P

---

### Post by jaykubun on 2010-12-15
stamatiou's question is solved it seems. Mine is not :(

But I will start a new thread, since my problem seems to be a different one anyway.

Jay

---

### Post by alzir512 on 2011-03-05
Exclamation Compaq 615 no wifi

---

