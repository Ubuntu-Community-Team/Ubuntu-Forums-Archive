---
title: "Intel 3495 Driver Causing Temporary Freezing"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by hf1111 on 2007-08-06
I installed ubuntu, card worked and connected just fine, then shortly after my cpu would freeze for about a second, then unfreeze for few seconds, then do it again, followed shortly by not being able to use wireless at all.  Problem stopped after I disabled the driver (intel 3495) from restricted drivers. Im getting a "intel_ring: FHW no detected" error at startup as well as a few others pertaining to this wireless card but they scroll too fast to see.  Im fairly new to ubuntu, so if anyone could help me in resolving this problem I would be very gratefull.

---

### Post by noob12 on 2007-08-06
Run ```
dmesg
``` to see the same info that scrolled by too fast at boot-time.

Posting the output from running these would be helpful
```

lspci -nn

lshw -C network

dmesg

```

---

### Post by hf1111 on 2007-08-06
Thanks for the reply

for "**dsmeg**" i get the following errors repeated many times:

> [   44.924000] ipw3945: Microcode SW error detected.  Restarting.
[   44.924000] ipw3945: Error Reply type 0x000000FF cmd TX (0x1C) seq 0x0000 ser 0x00030000
[   44.924000] ipw3945: Can't stop Rx DMA.
[   45.200000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)


and for "[B]lspci -nn

lshw -C network

dmesg[/B]" i get:

> 0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
dwe@dwe-laptop:~$ 
dwe@dwe-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:89:0a:a6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.110 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:efdff000-efdfffff irq:17


---

### Post by noob12 on 2007-08-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/118110](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/118110) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is a filed bug.  

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/118110](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/118110)

You could try ndiswrapper + the Windows driver.

---

### Post by hf1111 on 2007-08-07
I installed the ndiswrapper, wireless networking still didnt show up, just had to go into the manual configuration to connect, and it works.  Thanks I really appreciate it, was worried after seeing how nice ubuntu was, id be forced to go back to vista.

---

### Post by noob12 on 2007-08-07
With ndiswrapper it should work with Network Manager just fine.  Let me know if you want help with that.

---

### Post by hf1111 on 2007-08-07
Everything seems fine, just when I click on the networking icon in the top right theres no wireless option, so I have to manually configure it, im just thankfull it works though.

---

### Post by noob12 on 2007-08-07
We should be able to address this if you want to.  You should comment out all of the lines pertaining to eth1 from /etc/network/interfaces.  NetworkManager assumes you are dealing with them if they are in there.

---

### Post by hf1111 on 2007-08-07
> **noob12 said:**
> We should be able to address this if you want to.  You should comment out all of the lines pertaining to eth1 from /etc/network/interfaces.  NetworkManager assumes you are dealing with them if they are in there.

Worked perfectly, thanks man I really appreciate it, had everything working perfect cept for wireless, and now that works, thanks again.

---

