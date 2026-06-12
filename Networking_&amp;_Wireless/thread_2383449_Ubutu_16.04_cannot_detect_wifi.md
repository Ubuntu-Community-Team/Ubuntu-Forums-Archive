---
title: "Ubutu 16.04 cannot detect wifi"
date: 2018-01-25
forum: Networking &amp; Wireless
---

### Post by wseng92 on 2018-01-25
[COLOR=#111111][FONT=Ubuntu]My PC cannot detect wifi. This is the output for ```
sudo lshw -class network
```

[/FONT][/COLOR][B][FONT=Helvetica Neue]Output
[/FONT][/B]
```
seng@wseng:~$ sudo lshw -class network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7200000-f7207fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 07
       serial: 74:e6:e2:39:02:7c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:e000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff[COLOR=#111111][FONT=Ubuntu]Will the issue because of **network UNCLAIMED**?
```
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do let me know if you need any further information.[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]Thanks.[/FONT][/COLOR]

---

### Post by wseng92 on 2018-01-25
I managed to solve it by these two steps !

[B]1) Remove bcmwl-kernel-source
    [/B]```
sudo apt-get purge bcmwl-kernel-source
```[B]
2) Re-install bcmwl-kernel-source .
    [/B]```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

---

### Post by Hadaka on 2018-01-27
Hi, glad you found a solution !
Please mark your thread solved by logging into your first post
and clicking **Thread Tools** [on the right...just above join date]
then choose **Solved**.
Thank You

---

### Post by 1jackr on 2018-01-27
Total newbe here, trying to get away from Windows..... Same problem only with live install. When I get to the command line, (alt+F2 I think) I can't get anything to happen. Type any command hit enter and the system goes back to the home screen. Pretty sure I am typing the command correctly, even using copy and paste from the help menus always the same result. I am  in need of some assistance. Thank you in advance.

---

### Post by wseng92 on 2018-01-29
> **1jackr said:**
> Total newbe here, trying to get away from Windows..... Same problem only with live install. When I get to the command line, (alt+F2 I think) I can't get anything to happen. Type any command hit enter and the system goes back to the home screen. Pretty sure I am typing the command correctly, even using copy and paste from the help menus always the same result. I am  in need of some assistance. Thank you in advance.What did you mean by can't get anything to happen ? I would suggest you to post a new thread instead of comment below my post as I will [COLOR=#000000]mark my thread solved.[/COLOR]

---

### Post by wseng92 on 2018-01-29
> [COLOR=#000000]Hi, glad you found a solution ![/COLOR]
[COLOR=#000000]Please mark your thread solved by logging into your first post[/COLOR]
[COLOR=#000000]and clicking [/COLOR][B]Thread Tools [on the right...just above join date]
then choose [B]Solved.
Thank You[/B][/B]No problem.

---

