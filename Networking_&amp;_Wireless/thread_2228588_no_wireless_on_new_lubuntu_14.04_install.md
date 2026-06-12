---
title: "no wireless on new lubuntu 14.04 install"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by aadroque on 2014-06-08
hi , I have a old HP NX 6125 with a new install with lubuntu 14.04 , my wireless card is not working , can some one give help  how to install the correct driver please ? 
[http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c00397896-5%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1402241172793.876444892.199480143](http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay?javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken&javax.portlet.prp_ba847bafb2a2d782fcbb0710b053ce01=wsrp-navigationalState%3DdocId%253Demr_na-c00397896-5%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.tpst=ba847bafb2a2d782fcbb0710b053ce01&ac.admitted=1402241172793.876444892.199480143)

Thank you 
Roque 

the details are 
```
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:f7:d1:0f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=full firmware=5788-v3.26 ip=192.168.1.120 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0010000-d0011fff
```

---

### Post by praseodym on 2014-06-08
Hi,

you need the firmware for this card:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo service network-manager stop
sudo modprobe -rfv b43
sudo modprobe -v b43
sudo service network-manager start 
```

---

### Post by wildmanne39 on 2014-06-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

