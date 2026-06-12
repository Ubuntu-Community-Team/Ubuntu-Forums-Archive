---
title: "WiFi Wont Load on Start Up............"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by Nylo on 2008-09-12
As buggy as Network manager is I can usually get it to work...  That is until it decides to take a break, ie. Government employee.  ](*,)

My question is do I have the start-up set right?  It has never connected on a boot-up.  I checked in the Session Preferences and it seems to be there but on the command line it says, "disable."  I'm very new to Ubuntu so is this the issue?

[LIST]
[*]Name: Network Manager
[*]Command: nm-applet --sm-disable 
[*]Comment: Network Manager applet
[/LIST]

---

### Post by Crafty Kisses on 2008-09-12
Post the results of this command:
```
lshw -C network
```

---

### Post by Nylo on 2008-09-12
> **Codename said:**
> Post the results of this command:
```
lshw -C network
```

Thanks for the reply. There is post just above this with  a guy having issues with Ubuntu remembering the pass phrase.  I think this my issue as well. Another person says its a bug.

When I get bsck Ill post the command notes.

---

### Post by Nylo on 2008-09-14
> **Codename said:**
> Post the results of this command:
```
lshw -C network
```

Here it is.


WARNING: you should run this program as super-user.

  *-network DISABLED      

       description: Ethernet interface

       product: 82801BA/BAM/CA/CAM Ethernet Controller

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@0000:01:08.0

       logical name: eth0

       version: 03

       serial: 08:00:46:40:ac:61

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

  *-network

       description: Wireless interface

       product: AR5212/AR5213 Multiprotocol MAC/baseband processor

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wifi0

       version: 01

       serial: 00:0f:b5:34:f7:75

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11a

---

