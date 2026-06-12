---
title: "Unable to create hotspot in 16 due to no DHCP available  under IPv4 Settings"
date: 2016-05-01
forum: Networking &amp; Wireless
---

### Post by expatver on 2016-05-01
Upgraded to 16.04. Motherboard is an Asus Z97  Mk1. Wifi adapter is a TP Link via USB. I am able to connect to external networks  no problem. However when creating a hot spot using the "create new wifi  network"  tab under Network, I am able to set up a network that can be seen by other listening wifi devices in the area. However I can not connect to it because of DHCP.  Under IPv4 settings,  the ability to select DHCP  is grayed out. The only available options under the IPv4 settings  tab are either "shared to other computers" or "Disabled".  The Grayed out options are "Link Local Only", "Manual", "Automatic (DHCP Addresses only)", and "Automatic DHCP".  None of these are available. 

Other settings are under General tab,  All Users may connect is the only item checked.  Wifi tab  SSID is network name, Mode is Hotspot,  Band B/G, Channel default and Automatic MTU. WiFi Security  is WEP 128 Bit WEP Index 1 (default),  Authentication is Open System. The IPv6 tab is set to Ignore. 

I also notice that when I disable Wifi that the light on the Wifi box does not go off so I am assuming that the  system is not taking the adapter down. I also have another TP Link adapter, this one a USB dongle. Results with both adapters the same. 

I assume the primary problem is that  either I have not figured out how to enable DHCP due to an error in some other setting or a bug in the network stack somehow.  Any suggestions deeply appreciated. 

Thanks

expatver

---

### Post by gordintoronto on 2016-05-02
Are you connected to your router by an Ethernet cable?

---

### Post by expatver on 2016-05-02
Hi Gordintoronto

Thanks for the  reply and interest.  Yes I am connected via ethernet to the router. One thing I have not thought of trying  until today was  after the wifi is visible , trying to force DHCP with  sudo dhclient (adapter) to see if this will force the wifi adapter into DHCP.

---

### Post by expatver on 2016-05-22
OK this is an old thread I created but....per my last post unable to enable DHCP even after using sudo dhclient eth0. When I try that, the terminal window hangs i.e. does not return to the prompt. 

Creating a wifi hotspot is a fairly simple deal. I ve been unable to create one either with CLI or GUI. DHCP is the problem. The adapter, a TP Link TL-WN822N  works fine  when connecting to an existing network but in creating a hotspot, forget it. Where is the config for this and for that matter, how?

Thanks

Expat

---

