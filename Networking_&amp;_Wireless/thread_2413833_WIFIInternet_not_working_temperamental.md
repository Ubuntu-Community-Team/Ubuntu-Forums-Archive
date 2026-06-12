---
title: "WIFI/Internet not working /temperamental"
date: 2019-03-02
forum: Networking &amp; Wireless
---

### Post by flyinghigh2 on 2019-03-02
Hi I am having problem connecting to internet on Ubuntu

sometimes (like now) it works
sometimes (more ofen) it doesnt

i have windows installed on machine also and have to boot that up to acces internet which is slow, also there are times when no internet on my machine but my mothers is working fine so It would appear its not the router or phone line being the problem??

any suggestions ?

---

### Post by kc1di on 2019-03-02
Hello flyinghigh2,

We need to know what wireless card is in your machine.   If your not sure go to a terminal and copy and past this command and post the output here.
```
sudo lshw -C network
```

---

### Post by flyinghigh2 on 2019-03-02
hi I havent used this forum for a while and have forgotten how to post code from terminal is it ```
,
```??



lets try

```
 



*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:b1:82:13:07
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-141-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:ff600000-ff60ffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:a9:88:f7
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:ff500000-ff53ffff ioport:d000(size=128)


```





also my application updater "Ubuntu Software" doesnt seem to be populated with the same amount of software as it was and doesnt seem to be working properly... Is that past of the same problem or should I post somewhere else for that.

thanks

---

### Post by kc1di on 2019-03-03
Ok that card is quite old.  But there a few things you can try  
1.  Go to [this page]("https://www.smarthomebeginner.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/") and perform the recommended modification to the file.  
2. click on Network tray Icon and select your network and the networksetting go to your network in settings and click on the little gear emblem.  When you get to the settings box  click on IPv6 tab and change it from automatic to disabled. 
3. disable power manager as directed in [this post]("https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on").  Scroll down to post 21 and follow the instructions there.  
Try each of these one at a time see if it helps. 
Good Luck.

---

### Post by flyinghigh2 on 2019-03-03
thanks dave

it seems to be working at the moment

but this is useful info incase it doesnt work in future

---

### Post by flyinghigh2 on 2019-03-03
thanks Dave

How to know what edtion of ubuntu i'm running?

i think it says 16.04 on start up....

---

### Post by kc1di on 2019-03-03
one way is to issue this command in a terminal ```
lsb_release -a
```

you will get a reply that looks something like this:
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic

```

---

### Post by flyinghigh2 on 2019-03-03
thanks

---

### Post by flyinghigh2 on 2019-03-07
thanks this problem seems to have resolved itself ~ maybe it was and error witht he signal/phone line.....?

---

