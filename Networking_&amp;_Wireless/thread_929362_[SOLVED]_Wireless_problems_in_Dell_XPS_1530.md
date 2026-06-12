---
title: "[SOLVED] Wireless problems in Dell XPS 1530"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by summertanks on 2008-09-24
Well The situation is: my Dell XPS 1530 with PRO/Wireless 3945ABG card.

Problems
1. The card dosnt show up on network manager (Administrator>network)
2. No Wlan0 detected or found

what I tried
1. to lshw I get

 *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=iwl3945 latency=0 module=iwl3945

well card is there and drivers are loaded.

2. To lsmod | grep iwl

iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211

3. but problem remains with ** sudo lshw -businfo**
pci@0000:00:1c.0        bridge     82801H (ICH8 Family) PCI Express Port 
pci@0000:02:00.0  eth0  network    88E8040 PCI-E Fast Ethernet Controller
pci@0000:00:1c.1        bridge     82801H (ICH8 Family) PCI Express Port 
pci@0000:03:00.0        network    PRO/Wireless 3945ABG Network Connection
 
now the wireless card all detected is still not pointing to my device wlan0

4. network manager does not help...at all :(

5. I am running Ubuntu 8.04 and ndiswrapper is installed

hope some one can help me out

---

### Post by willca on 2008-09-25
Can you try the following.

sudo iwlist wlan0 scan

If this finds wireless networks in the area, thens its loading correctly. 
Otherwise, see if ndiswrapper is loading the driver.

sudo ndiswrapper -l

If not I will try to redo ndiswrapper.

---

### Post by VorDesigns on 2008-09-25
Check out:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=dell+wireless+1395](http://ubuntuforums.org/showthread.php?t=766560&highlight=dell+wireless+1395)
and
[https://wiki.ubuntu.com/LaptopTestingTeam/Dell](https://wiki.ubuntu.com/LaptopTestingTeam/Dell)

Additionally; consider using the Dell iso
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by Crafty Kisses on 2008-09-25
I'd also want to see this command:
```
lshw -C network
```

---

### Post by summertanks on 2008-09-25
ok... thnx for inputs... these are the result of it

1. iwlist
harkirat@summertanks:~$ sudo iwlist wlan0 scan
[sudo] password for harkirat: 
wlan0     Interface doesn't support scanning.

2. iwconfig
harkirat@summertanks:~$ sudo iwconfig wlan0
wlan0     No such device

3.ndiswrapper
harkirat@summertanks:~$ sudo ndiswrapper -l 
harkirat@summertanks:~$

4. Hence i removed ndiswrapper and my card is detected fine... drivers are loaded and modinfo without ndiswrapper is
harkirat@summertanks:~$ modinfo iwl3945
filename:       /lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     8E95C617988943846696F97
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)   <------ here is the issue????
parm:           hwcrypto:using hardware crypto engine (default 0 [software]) (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

5. lshw

harkirat@summertanks:~$ sudo lshw -C network
[sudo] password for harkirat: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:44:b4:ca
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945

some extra info if it helps

contents of /etc/udev/rules.d/70-persistent-net.rules 
# PCI device 0x11ab:0x4354 (sky2)

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:09:44:b4:ca", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:3c:19:f0:6f", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

and a log msg from Network Manager

> iwl3945: MAC is in deep sleep
> iwl3945: Unable to init nic

also i checked the links supplied... first didnt help...second says there is no problem with the wireless on dell.(yeah right!!!) and well the dell iso thing... i am on a dial up in no mans land with a burst speed of 5kbps... so lets not even go in that direction ... plz... or i'll do something obscene to the modem

so thats all the things i can think off... HELP

---

### Post by carpii on 2008-09-25
I just got an XPS 1530 this week, with the Intel wireless card.

I had all sorts of problems, but it seems stable now

You could try this

sudo nano /boot/grub/menu.lst

Find the bit where its passing options to the kernel (a few lines under "## End of Default Options")

Add onto the end 'noapic' (without quotes)

While youre there, if youre mousepad is going crazy when you use it, you might want to also want to add 'i8042.nomux=1' after the noapic (on same line)

Then reboot and try wireless again. Mine still has problems reconnecting on boot, so I sometimes have to go into network manager and retap in my wireless key. Annoying but at least it works

HTH

---

### Post by summertanks on 2008-09-25
well tried and didnt work...

kernel parm already i8042.nomux=1 noapic

i think it might have something to do  with the roaming mode thing... i went into roaming mode for wireless... and the thing is still being a pain in the ***

---

### Post by summertanks on 2008-09-26
well it just decided to start working today morning... no idea why...

last things i tried were backports and kernel parm noapic... though the next boot showed no promise... but this is linux... who the hell really knows what happens .. :)

also in case u r on static eth0 Networkmanager will be cheeky so to go to wlan0  get out of static (to dhcp) 
i have to mark this as solved... if only i knew how... :(

---

### Post by carpii on 2008-09-26
Its most likely noapic, trust me 
I spent many hours trying to troubleshoot this one :)

---

