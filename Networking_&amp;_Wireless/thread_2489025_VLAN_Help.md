---
title: "VLAN Help"
date: 2023-07-15
forum: Networking &amp; Wireless
---

### Post by mwei19 on 2023-07-15
Hi all!

As I am still a beginner when it comes to networking I am attempting to play around and configure multiple VLANs utilizing my **ubuntu isc-dhcp server** that is connected to a managed **TP-Link switch (TL-SG108E).** 

I have my DHCP server up and running but it does not seem like the created VLANs are working as I am unable to get a test device that is connected to a port that is configured for a VLAN (VLAN20) to work. When I set the device to use DHCP network settings it still gets assigned an IP Address in the **old (pre VLAN/subnet) 192.168.0.x subnet/VLAN** and not the correct subnet/VLAN that I configured for (10.0.0.x). 

Currently playing around with just one **VLAN (VLAN20)** that I am trying to configure for **10.0.0.x subnet**. 

**My current isc-dhcp configurations:**

```
subnet 192.168.0.0 netmask 255.255.255.0 {range 192.168.0.1 192.168.0.253;
authoritative;
filename "grubx64.efi";
option routers 192.168.0.1;
option domain-name-servers 192.168.0.200, 192.168.0.201, 8.8.8.8, 8.8.4.4;
option domain-name "mwei.dns";
}




#VLAN20 (need a managed router to enable)
subnet 10.0.0.0 netmask 255.255.255.224 {
authoritative;
option routers 10.0.0.1;
option domain-name-servers 8.8.8.8, 8.8.4.4;
range 10.0.0.1 10.0.0.30; 
}

```


[B]/etc/default/isc-dhcp-server

[/B]```
INTERFACESv4="wlp2s0 enp0s31f6"
```
[B]
netplan configuration[/B]


```
network:  version: 2
  #renderer: networkd
  ethernets:
    enp0s31f6:
     dhcp4: no
     addresses: [ 192.168.0.200/24 ]
     routes:
     - to: default
       via: 192.168.0.1 


  vlans:
    vlan.20:
      id: 20
      link: enp0s31f6
      addresses: [ 10.0.0.1/27 ]

```

Please advise. Did I misconfigure something? 

Thanks,
Max

---

### Post by mwei19 on 2023-07-15
Attached are screenshots of my current TP-Link Switch VLAN configurations.

port 6- test system
port 7- DHCP server
port 8- gateway/router

---

### Post by mwei19 on 2023-07-17
Just an update as I'm playing around more with the configurations...

I was finally able to get the test DCHP client/test system to get assigned the correct 10.0.0.x IP range! 

However, no matter what I do/try I am unable to get the DNS to resolve/work within the VLAN. I even attempted to create a new bind9 DNS server in the VLAN to no success. 

I am able to ping my 10.0.0.1 gateway alongside my original DNS server (192.168.0.200) from the new VLAN but am unable to ping 8.8.8.8. 

Please advise, am I missing something to get the DNS to resolve from the new VLAN?

---

### Post by mwei19 on 2023-07-18
Finally figured it out after going through many many articles, guides, forums, and googling, LOL! 

I was just missing the iptables configuration part. Once I created the appropriate iptable rules everything started to work flawlessly! 

These were the steps that I followed, from online documentation. that got everything to work (did some fine tuning afterwards):

```
[COLOR=#5E6065][FONT=Menlo]iptables -A FORWARD -j ACCEPT
[/FONT][/COLOR][COLOR=#5E6065][FONT=Menlo]iptables -t nat -A POSTROUTING -j MASQUERADE
[/FONT][/COLOR]
```

---

