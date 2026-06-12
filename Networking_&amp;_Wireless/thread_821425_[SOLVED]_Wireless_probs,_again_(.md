---
title: "[SOLVED] Wireless probs, again :("
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by Kinnza on 2008-06-07
Hi guys,
thanks to you guys i got my wireless to finnaly work about a week ago
it worked PERFECTLY for this time... 

but now , all of sudden, just in the middle of browsing the web, it stopped working.

when i look in the network manager thingie i see that "enable wireless" isnt checked, and its disabled so i cannot check it.

output of: lshw

```

kinnza@kinnza-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:97:9d:7f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:37:f2:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

as you can see its says its DISABLED

how can i enable it?

also yesterday i was installing somethings and some messaged poped suggesting i will do : apt-get autoremove
could that have removed something important? :S
if it did, why did it not stopped working then?

---

### Post by chili555 on 2008-06-07
By any chance, did you nudge the switch that turns your wireless on and off? Let's see:```
sudo cat /var/log/messages | grep -e switch
```

---

### Post by Kinnza on 2008-06-07
you mean like the button that turns wireless on and off? 
i dont think im that dumb... its not set to no-wireless

```

Jun  6 11:17:43 kinnza-laptop kernel: [  810.822608] SMP alternatives: switching to UP code
Jun  6 11:17:43 kinnza-laptop kernel: [    0.498994] SMP alternatives: switching to SMP code
Jun  6 16:24:11 kinnza-laptop kernel: [ 1287.560073] SMP alternatives: switching to UP code
Jun  6 16:24:11 kinnza-laptop kernel: [    0.497688] SMP alternatives: switching to SMP code
Jun  6 16:24:11 kinnza-laptop kernel: [    1.657715] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x014f0900
Jun  6 21:26:52 kinnza-laptop kernel: [ 1237.143157] SMP alternatives: switching to UP code
Jun  6 21:26:52 kinnza-laptop kernel: [    0.497378] SMP alternatives: switching to SMP code
Jun  7 00:29:03 kinnza-laptop kernel: [ 8281.643319] Kill switch must be turned off for wireless networking to work.
Jun  7 00:29:09 kinnza-laptop kernel: [ 8287.876837] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 00:29:14 kinnza-laptop kernel: [ 8292.376732] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 13:37:41 kinnza-laptop kernel: [ 8294.483635] SMP alternatives: switching to UP code
Jun  7 13:37:41 kinnza-laptop kernel: [    0.497279] SMP alternatives: switching to SMP code
Jun  7 13:47:33 kinnza-laptop kernel: [  591.387744] Kill switch must be turned off for wireless networking to work.
Jun  7 13:47:35 kinnza-laptop kernel: [  593.410594] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 13:49:34 kinnza-laptop kernel: [  712.972967] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 13:51:48 kinnza-laptop kernel: [   17.389124] SMP alternatives: switching to UP code
Jun  7 13:51:48 kinnza-laptop kernel: [   17.989719] SMP alternatives: switching to SMP code
Jun  7 13:51:48 kinnza-laptop kernel: [   18.340908] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  7 13:51:54 kinnza-laptop kernel: [   47.707241] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 13:54:12 kinnza-laptop kernel: [   93.387294] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 13:54:38 kinnza-laptop kernel: [   96.535542] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 14:44:15 kinnza-laptop kernel: [   16.984435] SMP alternatives: switching to UP code
Jun  7 14:44:15 kinnza-laptop kernel: [   17.589682] SMP alternatives: switching to SMP code
Jun  7 14:44:15 kinnza-laptop kernel: [   17.938882] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  7 14:44:20 kinnza-laptop kernel: [   47.315885] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 14:47:26 kinnza-laptop kernel: [  155.015912] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 15:09:37 kinnza-laptop kernel: [  628.873885] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 15:15:25 kinnza-laptop kernel: [  630.634591] SMP alternatives: switching to UP code
Jun  7 15:15:25 kinnza-laptop kernel: [    0.493670] SMP alternatives: switching to SMP code
Jun  7 15:16:06 kinnza-laptop kernel: [   12.733906] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 15:40:37 kinnza-laptop kernel: [  599.768257] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 21:14:49 kinnza-laptop kernel: [  601.167018] SMP alternatives: switching to UP code
Jun  7 21:14:49 kinnza-laptop kernel: [    0.497562] SMP alternatives: switching to SMP code
Jun  7 21:15:33 kinnza-laptop kernel: [   13.423891] iwl3945: Radio disabled by HW RF Kill switch
Jun  7 23:09:20 kinnza-laptop kernel: [   25.008606] SMP alternatives: switching to UP code
Jun  7 23:09:20 kinnza-laptop kernel: [   25.609086] SMP alternatives: switching to SMP code
Jun  7 23:09:20 kinnza-laptop kernel: [   25.963094] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  7 23:09:26 kinnza-laptop kernel: [   57.449410] iwl3945: Radio disabled by HW RF Kill switch

```

---

### Post by Kinnza on 2008-06-07
ok you are probably right
im probably am stupid enough
it wasnt the hardware switch it was the software one..

i dont know what happand but i probably clicked Fn+F5 instead of Fn+F4 when i wanted to put it to sleep mode...
how stupid of me

weird thing was that i had to restart after switching it again
:S 

but it worked.... 

thanks again :D

---

### Post by chili555 on 2008-06-07
Thanks for your thanks and your kind comments. The main reason some of us here know the answer is because we've made the same mistake and struggled for a few days, had nightmares for a few nights and considered the sledgehammer. Then we've discovered the simple answer. You have a new tool for your toolbox.

---

### Post by Kinnza on 2008-06-08
thanks honey for trying to make me feel better about that :P

im guessing there isnt a software solution for that right? (only the silly Fn button....)

---

### Post by chili555 on 2008-06-08
> im guessing there isnt a software solution for that right? (only the silly Fn buttonThere may be an ugly hack that does this, I've never seen one that I could reliably recommend. I think the assumption is that we *are* going to want to turn off the wireless sometimes to save battery power. Watching a DVD on the airplane, perhaps.

---

