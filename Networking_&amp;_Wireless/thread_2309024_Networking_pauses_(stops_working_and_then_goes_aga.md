---
title: "Networking pauses (stops working and then goes again) for a while every couple of min"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by steven-wooding on 2016-01-07
I have searched quite a bit on google but it doesn't seem like anyone else has this issue. So I expect it to be a very new issue.
My laptop MSI ge72 2qf (Ubuntu 15.04 x64) has this issue as well as a friends laptop Mecer w370st (Ubuntu 15.10 x64).


What happens is that the network stops working for a short while, between 30 seconds and 2 minutes. This happens every couple of minutes, but the time between the occurances is completely random. There is no logs, visual indications that something went wrong except for the network simply not transferring any data. It's almost like someone hit the 'pause' button on the network. All applications and protocols are affected on my laptop. But other pc's on the network are not affected at all.


Was working fine but after an update around end November / beginning December 2015 it started


Wireless OR Ethernet does not matter. Both do it (I disabled wifi and connected ethernet). This means that it's likely not drivers but rather a kernel / network moduleissue. But this is just a guess


I connected to a 3 different networks at other locations, home, office and a friends house and the same symptoms occur.


I ping a fixed IP (NOT a domain) on the same network and it also stops working while the issue occurs.


'route -n' remains unchanged.


I have changed the IPv6 settings to "Link-Local Only" but without any changes. It might even be a bit worse.


Existing established connections also "pauses" when the issue occurs. Afterwards they just carry on as if there was no issue.


There are nothing that happens in syslog when the network drops


There are also no indication that the network stops working, it still says it's connected in the GUI and all looks fine, the dataflow just stops


I have disabled the ubuntu firewall with 'sudo ufw disable' but still does not make a difference


Has anyone else experienced the same issue? And what can I try to see if it works. Doing a "sudo service network-manager restart" does fix it when it happens but it will still do the same in a minute or so, so this is not exactly a solution.


I have attached the wireless info but please note that this issue happens over ethernet as well

See the 'sudo lshw -c network' output below

  *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 83
       serial: 34:e6:ad:99:cd:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-43-generic firmware=25.17.12.0 ip=192.168.11.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:a3200000-a3201fff
  *-network
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 13
       serial: d8:cb:8a:7e:85:fb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:36 memory:a3100000-a313ffff ioport:3000(size=128)

---

