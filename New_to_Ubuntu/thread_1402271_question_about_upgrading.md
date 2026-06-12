---
title: "question about upgrading"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-02-08
im currently using ubuntu 8.04  and there is an upgrade to 9.04  well 9.04 looks like its pretty cool but the last time i tried this it wouldnt pick up my internet connection no matter what and one of my buddies in networking told me it was a missing driver

so what im asking is if i upgrade to 9.04 from 8.04  will it give me the necessary stuff to run the internet connections and such

---

### Post by Cheezespread on 2010-02-08
When you say "there is an upgrade to 9.04 " , you mean you want to upgrade it or the update manager shows you an update ?

Wouldn't it show an update to Ibex ( 8.10 ) first than 9.04 ?. Or does it skip it ?.

Can you try this in the terminal please and post the output. Should give an idea of your networking device.
```
sudo lshw -C network
```

---

### Post by nhasian on 2010-02-08
pyrofreak99, may i make a suggestion?  hold off on upgrading until 10.04 LTS comes out (April 29th).  you will have a clean upgrade path from 8.04 LTS.  if you upgrade now you will have to upgrade to 8.10, then 9.04.

---

### Post by pyrofreak99 on 2010-02-08
> **Cheezespread said:**
> When you say "there is an upgrade to 9.04 " , you mean you want to upgrade it or the update manager shows you an update ?

Wouldn't it show an update to Ibex ( 8.10 ) first than 9.04 ?. Or does it skip it ?.

A bit more info of your machine you are running would help a great deal if someone with similar configs could advise you.

Can you try this in the terminal please.
```
sudo lshw -C network
```



ok my bad its in the update manager
*-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:a8:9b:e6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.254.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:7a:bd:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:fa:7e:ce:7c:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Cheezespread on 2010-02-09
> **nhasian said:**
> pyrofreak99, may i make a suggestion?  hold off on upgrading until 10.04 LTS comes out (April 29th).  you will have a clean upgrade path from 8.04 LTS.  if you upgrade now you will have to upgrade to 8.10, then 9.04.

I would actually second that one too. Considering that the Lucid is right around the corner ( or the block) . 

Sorry for my persistant inquiry on this . Are you getting a prompt to upgrade to 9.04 while you are in 8.04 ?. I thought you get upgrade notifications for the subsequent releases and LTS's from an alreay LTS release. I am a bit confused on this now :-(

**logical name: wmaster0**
 **wmaster0 is a generic driver used by the kernel, and if this is the logical name assigned there is usually a problem with the driver also** : **from the **[**WifiDocs**]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw")

---

### Post by pyrofreak99 on 2010-02-09
yes i am in 8.04 now  and was prompted to upgrade to 9.04  by the update manager

---

### Post by nhasian on 2010-02-09
go to System->Administration->Software Sources

click on the Updates tab.  Then under Release upgrade change the dropdown menu to say "Long Term Support release only"

now it will not prompt you to upgrade until Ubuntu 10.04 comes out April 29th.

> **pyrofreak99 said:**
> yes i am in 8.04 now  and was prompted to upgrade to 9.04  by the update manager

---

### Post by HPD2 on 2010-02-09
Small pice of advice, dont upgrade. I went that route for a while and it cause nothing but problems, all kinds of things would break and performance would drop. I would recomend backing up your data then doing a fresh install. Thats just me and my experience though.

---

### Post by nhasian on 2010-02-09
well upgrading from LTS to LTS is supposed to have much more extensive testing and should be pretty painless.  One thing to note though is that upgrading from 8.04 to 10.04 will not update grub to grub2 or update your filesystem from EXT3 to EXT4.  So in this particular instance, a fresh install would be preferable but it is not required. 

> **HPD2 said:**
> Small pice of advice, dont upgrade. I went that route for a while and it cause nothing but problems, all kinds of things would break and performance would drop. I would recomend backing up your data then doing a fresh install. Thats just me and my experience though.

---

