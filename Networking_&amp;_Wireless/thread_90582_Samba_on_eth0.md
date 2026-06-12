---
title: "Samba on eth0"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by ilbozo on 2005-11-15
I got 2 network cards on my notebook. One Gigabit Ethernet (eth1) and one wifi 2200bg (eth0). 
How can i tell ubuntu to use eth0 for windows network? :confused: 
Please tell me if there is another topic to read... i searched everywhere and i can't find any instruction!

---

### Post by ilbozo on 2005-11-15
i add thi lshw part...


> *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@01:02.0
                logical name: eth0
                version: 05
                serial: 00:12:f0:42:6a:1f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 ip=192.168.0.2 multicast=yes wireless=unassociated
                resources: iomemory:fe9fe000-fe9fefff irq:18
           *-network:1
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@01:03.0
                logical name: eth1
                version: 10
                serial: 00:01:4a:1d:48:1e
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 ip=1.255.59.114 multicast=yes



---

### Post by mgor on 2005-11-15
hm, i don't understand your question?

by looking at the topic it seems like you want samba only to listen to eth0? but when i read the thread it seems like you want to connect to the rest of the network via your wlan card?

any way, if you want samba to only listen to one interface (in this case ip address) and not all, add the following to /etc/samba/smb.conf
```
socket address = <ip address of eth0>
```

the wlan card is disabled and proably not configured. you can configure it via `network-admin` which can be found in the gnome menu; system -> administration -> network. select your card and configure ssid, wep-key (if needed) and how to obtain ip address (static or dynamic).

---

### Post by ilbozo on 2005-11-15
sorry i noticed after posting that the tile was not correct!
I'm quite noob with ubuntu and linux... i thought that samba was the network interface software able to connect to windows network... Doh!
The problem is that i want to connect to my windows network! 
I configured the wireless network card with static ip, i enabled it and... what have i to do? When i look at Resorces->network i can't see my network!!
Ah, i forgot... i'm using ad-hoc connection.

---

### Post by womd on 2008-03-31
hi !

you could use smbmount to access you windoz machine !

fe:

smbmount //windowsmachine/share /local-mount-point -U Username


cu

---

### Post by Eiríkr on 2008-03-31
How to connect depends on what you mean.  

By "connect to my windows network", do you mean:
[list=1][*]you have a network of Windows machines connected to the internet, and you want your Ubuntu machine to connect to the internet through this network?
[*]you have a bunch of Windows machines sharing files, and you want your Ubuntu machine to also have access to those files?
[*]you havea bunch of Windows machines sharing files, and you want those Windows machines to be able to access files on your Ubuntu machine?[/list]

If 1, that's usually pretty straightforward.  You should be able to do that pretty automatically.

If 2, your Ubuntu machine needs to be able to act as a Samba client.  Samba is the Linux package for filesharing with Windows machines.  The two specific packages you need to have installed for Samba client access are [font=courier]smbclient[/font] and [font=courier]smbfs[/font].  Fire up Synaptic and make sure those two are installed.  Then, open Nautilus (your default Ubuntu file browser), then click Go -> Network, double-click the Windows Network icon, double-click the icon for your Windows workgroup, double-click the icon for the Windows machine you want, double-click the icon for the shared folder you want, and then enter the appropriate username and password for that Windows machine to get access to the shared files.  If for some reason the icons don't display properly, there seems to be a known bug with WinXP that can sometimes screw this up.  In such cases, in Nautilus, hit Ctrl+L or click View -> Location Bar to show the location bar, then type in [font=courier]smb://IP.ADD.RE.SS[/font], replacing the caps with the IP address of the Windows machine you want to access.

If 3, you want your Ubuntu machine to serve shared files via Samba.  In this case, fire up Synaptic and make sure you have the [font=courier]samba[/font] package itself installed.  Then you'll have to properly configure your Samba server; this can be complicated, and I don't want to overwhelm you :), so if you need to do this, let us know, and I can walk you through the process.

Cheers,

Eiríkr

---

