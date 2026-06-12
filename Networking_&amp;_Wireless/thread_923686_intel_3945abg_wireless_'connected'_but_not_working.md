---
title: "intel 3945abg wireless 'connected' but not working"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Papa-san on 2008-09-18
'Bout pulling my hair out again... 

I have a Dell inspiron 1525 with the Intel 3945abg wireless card in it. It's set up as a dual boot system alongside the Vista virus. It was plug-n-play when I got my DSL modem/router, which was rather exciting at that time.

We have moved since, and DSL isn't available here. We have cable now. The Windows OS works seamlessly with the Linksys 8011g router, but something is wrong with the Ubuntu 8.04 OS: I used WICD, and now my wireless icon thingy up by the clock shows that I am connected to the router, but there is no real connectivity. Firefox, Opera, Frostwire, etc all time out and say there is no connection...

I don't know where to begin looking for the problem... I'd greatly appreciate it if someone could help me get this figured out...


(I haven't changed my signature line, cause it was so helpful with my old laptop) :-D

---

### Post by danmif on 2008-09-18
i have the same problem withe the same networkcard, on sony vgn fe48e ubuntu deos not support Intel 3945abg wireless card

---

### Post by Papa-san on 2008-09-18
It was working flawlessly for many months. I am sure I am dealing with operator error at this point... 

We tried to log on to a weak signal from a neighbor, but couldn't get it to work. His ESSID and WEP key can be found in a few different places in this computer where they should have been changed. 

My 'Network Tools' GUI tells me that eth0 and eth1 do not exist... I know they do, because when I plug into the router, eth0 works even though it keeps telling me it doesn't exist...

Maybe we can get someone to help us get through this. I've learned a lot about Linux, but not NEARLY enough to poke around too deep into the guts of the thing without guidance...

---

### Post by Crafty Kisses on 2008-09-18
Post the results of this command:
```
lshw -C network
```

---

### Post by Papa-san on 2008-09-19
I ran it and this is what I got:
```
john@john - 1525n:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
    description: Ethernet interface
    product: 88E8040 PCI-E Fast Ethernet Controller
    vendor: Marvell Technology Group Ltd.
    physical id: 0
    bus info: pci@0000:09:00.0
    logical name: eth0
    version: 12
    serial: 00:1d:09:41:fd:39
    width: 64 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
 *-network
    description: Wireless interface
    product: PRO/Wireless 3945ABG Network Connection
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@0000:0b:00.0
    logical name: wmaster0
    version: 02
    serial: 00:1c:bf:c9:92:1d
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list logical ethernet physical     wireless configuration: broadcast=yes driver=iwl3945 ip=192.168.1.103 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
john@john-1525n:~$
```(I had to type it all in, so it might not look exactly right...)
I looked in the 'Network Tools' GUI for 'wmaster0' and it was in there. It also said that that interface didn't exist...

---

