---
title: "wireless"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by ddg on 2008-06-10
Hi ....

I installed ubuntu 8.04 on my acer 4520. How to see that the wireless network is working??. Btw I don't have the facility now and I am connected to the internet using wire.

rgds,
ddg

---

### Post by superprash2003 on 2008-06-10
please post your iwconfig output

---

### Post by Ayuthia on 2008-06-10
> **ddg said:**
> Hi ....

I installed ubuntu 8.04 on my acer 4520. How to see that the wireless network is working??. Btw I don't have the facility now and I am connected to the internet using wire.

rgds,
ddg
By going to the Terminal and typing lshw -C network will help tell you your wireless card and give you a hint if your wireless is working.  If you are not sure, just post the results of lshw -C network here.

---

### Post by ddg on 2008-06-11
Hi Ayuthia,

Here is the output.

 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:2e:72:c9
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.3 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

rgds,
ddg

---

### Post by ddg on 2008-06-11
> **superprash2003 said:**
> please post your iwconfig output

Hi........,

here is the output:

lo              no wireless extensions.

eth0            no wireless extensions.

rgds,
ddg

---

### Post by ddg on 2008-06-12
Hi anybody there...,

I still have problem to activate my wireless lan of acer 4520 with ubuntu 8.04.

I installed ndis wrapper driver and it said that the hardware is present.
Any tips please??

rgds,
ddg:)

---

### Post by tysonh on 2008-06-13
What is the wireless device called on your system.  Is it a mini pci card or integrated wireless?  There are some chipsets that don't work at all with ubuntu.

---

### Post by ddg on 2008-06-13
> **tysonh said:**
> What is the wireless device called on your system.  Is it a mini pci card or integrated wireless?  There are some chipsets that don't work at all with ubuntu.

Hi, 

thanks for the email.It is my mistake, it is working now.
It is atheros 5007, (I think it is integrated). First I tried using midwifi driver but it gave error while installation and then I tried with ndis driver.
Now I can see the device from System>Administration>network
I have given the notebook to the owner for adaptation and will check again later all the functionalities

Regards,
ddg

---

