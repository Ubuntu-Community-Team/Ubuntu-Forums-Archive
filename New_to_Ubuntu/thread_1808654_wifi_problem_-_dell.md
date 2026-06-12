---
title: "wifi problem - dell"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by soon on 2011-07-20
Hi

Ive just installed ubuntu 11 on my old dell 131L. I have managed to get the wireless working by following advice detailing installing and installing packages in sunaptic package manager. I then had to type rfkill unblock wifi in the terminal. So the wifi works. However when i restart the laptop i need to go to the terminal bd retype the rfkill comand to get wifi working again. Is there a way - dumbed down as far as possible please - to avoid doing this on restart.

thanks for any advice, 
soon

---

### Post by amjjawad on 2011-07-20
> **soon said:**
> Hi

Ive just installed ubuntu 11 on my old dell 131L. I have managed to get the wireless working by following advice detailing installing and installing packages in sunaptic package manager. I then had to type rfkill unblock wifi in the terminal. So the wifi works. However when i restart the laptop i need to go to the terminal bd retype the rfkill comand to get wifi working again. Is there a way - dumbed down as far as possible please - to avoid doing this on restart.

thanks for any advice, 
soon

Hello and Welcome :)

I'd suggest to start reading here: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)


From Terminal, please issue this command:

```
sudo lshw -C network
```

Post back the output and please wrap up the text with "CODE" tags :)

---

### Post by soon on 2011-07-20
Hi Amjjawad

thanks for your reply. Below is the output from your suggested command.


```

 SCSI                      
  *-network        
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:66:22:03
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:11:49:be
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 ip=192.168.1.67 link=yes multicast=yes wireless=IEEE 802.11bg
 
```I hope it means something.

thanks again, Soon

---

### Post by thefasterblueone on 2011-07-20
Post output of 

```
rfkill list
```

---

### Post by soon on 2011-07-21
Hi thefasterblueone

Here is the output of rfkill list.

```

admin1@admin1-Latitude-131L:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
admin1@admin1-Latitude-131L:~$ rfkill unblock wifi
admin1@admin1-Latitude-131L:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```As you can see the wifi is hard blocked every time i restart. It is fine after rfkill unblock.

thanks for any help, 
soon

---

### Post by bkratz on 2011-07-21
> **soon said:**
> Hi thefasterblueone

Here is the output of rfkill list.

```

admin1@admin1-Latitude-131L:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
admin1@admin1-Latitude-131L:~$ rfkill unblock wifi
admin1@admin1-Latitude-131L:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```As you can see the wifi is hard blocked every time i restart. It is fine after rfkill unblock.

thanks for any help, 
soon


This post should help do what you need

[http://ubuntuforums.org/showpost.php?p=10745874&postcount=4](http://ubuntuforums.org/showpost.php?p=10745874&postcount=4)

---

### Post by soon on 2011-07-21
thanks very much bkratz and everyone else. Those last commands sorted it.

thanks again, soon

---

### Post by bkratz on 2011-07-22
> **soon said:**
> thanks very much bkratz and everyone else. Those last commands sorted it.

thanks again, soon



Sure glad it worked for you---enjoy!

---

