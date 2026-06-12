---
title: "bcm 4306 fubared"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by natis on 2008-08-22
I was having trouble with my wireless (was working), but after about 5 min. my signal strength would plummet and would kick me off my home network (wep enabled 128 bit hex), I saw there were a few open networks available but I could not sign on any of them either. So I thought it might be a driver issue, I blacklisted by drivers and installed bcm43xx-fwcutter, and totally jacked everything up. So how do unblacklist them and at least get back to where I started at ?

lshw -C network 
v3.16 ip=192.168.1.101 latency=32 mingnt=64 module=tg3 multicast=yes 
  *-network:1 UNCLAIMED 
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:02:03.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: latency=32

 iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

thanx

---

