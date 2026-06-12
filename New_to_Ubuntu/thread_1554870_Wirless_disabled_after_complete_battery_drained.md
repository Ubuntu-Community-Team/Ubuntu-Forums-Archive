---
title: "Wirless disabled after complete battery drained"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by dagarshali on 2010-08-17
Hi, 
I have a 64bit lucid lynx on my laptop. Yesterday, I was watching a video and didn't realize that i was on battery and it just powered off when the battery drained completely. Since then, I see that the wireless is disabled. I have the physical wireless switch on my laptop turned on.

if i do sudo ifconfig wlan0 up I get
**SIOCSIFFLAGS: Unknown error 132**

The output of rfkill list is below
> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

the output of **lshw -C network**
>   *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:28:73:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:f4100000-f4101fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:8b:f2:51:1a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.106 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:33 memory:f4000000-f400ff

I also tried using the live cd and I still see that the wireless is disabled.

Any help please.. Have no idea where to start.

Best Regards,
Vishwa

---

### Post by silverglade00 on 2010-08-17
Not sure where to go if this doesn't work, but it sounds like it lost track of what the hardware switch was on. Try to put it in the off position and boot up. Once it is up and running, try turning the switch on.

---

### Post by dagarshali on 2010-08-17
Hi,
I did try to do what you suggested ( switching it off and then turning it on once it booted), but didn't make any difference. I see on the web that there are many questions about the same problem.. but nobody actually suggested any solution..:(

Any body.??? pleaseeeeeeeee

---

### Post by aeiah on 2010-08-17
i cant really offer much help, but it sounds like your laptop probably went into hibernation - perhaps widening your search to this will yield something useful.

---

### Post by jonnywombat on 2010-08-17
Are you dual booting?

If so boot into windows, and turn the wireless on via the switch.

Reboot into ubuntu and you should be good to go.

I have had similar issue, where I have turned off the wireless in windows and ubuntu can't turn it back on again... maybe your complete loss of power did something similar.

---

### Post by dagarshali on 2010-08-17
Hi,
it is not a dual boot..(

vishwa

---

### Post by foldingstock on 2010-08-17
Dagarshali, can you check your BIOS and see if the wireless is disabled there? I have a Dell inspiron laptop which will cut the wireless off when the battery drains and can only be turned back on using Windows or the BIOS option.

---

### Post by dagarshali on 2010-08-17
Hi,
The bios does have wireless enable and disable.. I checked it and it showed enabled.

Still no luck..:(

Regards,
vishwa

---

### Post by Mr_VeRiTy on 2010-08-17
> **dagarshali said:**
> Hi,
The bios does have wireless enable and disable.. I checked it and it showed enabled.

Still no luck..:(

Regards,
vishwa
This probably won't work but try hibernating your laptop again, when my battery runs out my laptop disables everything (wireless, mouse, keyboard, USBs)until it has power again and has been un-hibernated properly

---

### Post by dagarshali on 2010-08-17
am trying to drain the battery again to see if that fixes the problem, like one of the members suggested..

Also, I tried using opensuse live cd and the wireless is disabled there too..Any help..I am running out of options...:(

vishwa

---

### Post by Mr_VeRiTy on 2010-08-17
> **dagarshali said:**
> am trying to drain the battery again to see if that fixes the problem, like one of the members suggested..

Also, I tried using opensuse live cd and the wireless is disabled there too..Any help..I am running out of options...:(

vishwa
You don't have to drain the battery to hibernate, just select hibernate from the power button menu.

---

### Post by dagarshali on 2010-08-18
Hi,
When i do the hibernate, i get this message before it hibernates..

**iwlagn 0000:6:00.0 Mac is in deep sleep CSR_GP_CNTRL 0X000403D8** 

and then** hardware error: restarting**..

But when i start the laptop again, the same message briefly blinks and comes to login screen..but the situation is still the same.. 

could this is be of any help in fixing this problem..:(

---

### Post by dagarshali on 2010-08-19
HI Guys,
I have tried everything that was suggested and I still can't get my wireless back..

I checked that in the file /var/lib/Network-Manager/Network-Manager.state,

wireless enabled=false

I then changed it to true and restarted the network manager. Unfortunately, when i restarted the network manager, the wireless enabled=false was set in network-manager.state file.

any ideas...pleaseeeeeee

---

