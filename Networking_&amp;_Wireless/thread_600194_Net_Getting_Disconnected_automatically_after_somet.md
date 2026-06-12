---
title: "Net Getting Disconnected automatically after sometime on U?BUNTu 7.10 Gusty"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by aneeshkj on 2007-11-02
hi guys i am new here at the community..

I am having problems accessing net on Ubuntu gusty..

I am using one onboard ethernet an another lancard..
I can connect to net initailly and vie the sites..
But it automatically gets disconnected after 4-5 minutes..

I am using a cable modem to connect to the internet..

I can access net initially ,but gets disconnected soon without showing any error  or something...

Due to this i am unable to update  my s/w packages  and all..

Waiting for your replies...

---

### Post by PaulFr on 2007-11-02
AFAICS, not enough information to diagnose any problems. However, you could start by looking at the output of ```
dmesg
``` **immediately after the network fails** to see if anything is being reported. You could also look in the various files in **/var/log directory** to see if anything seems out of the ordinary.

---

### Post by aneeshkj on 2007-11-02
sorry guys i am a noob here..
So sorry for not providing those necessary....

This is the output of dmesg after net gets disconnected..
[Output of Dmesg]("http://aneeshkj.googlepages.com/dmesg.txt")

---

### Post by PaulFr on 2007-11-03
Some basics: You seem to have eth0 at ```
[   17.944152] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [LNKA] -> GSI 19 (level, low) -> IRQ 17
[   17.944300] eth0: RealTek RTL-8029 found at 0xec00, IRQ 17, 00:C0:DF:E3:2C:95.
``` and eth1 at ```
[   21.193062] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 21
[   21.193069] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   21.193076] forcedeth: using HIGHDMA
[   21.712093] eth1: forcedeth.c: subsystem: 01462:7207 bound to 0000:00:14.0
```.

Can you show the output of the following commands (each line is a separate command, but you know that already):
```
ifconfig -a
cat /proc/interrupts ; sleep 5; cat /proc/interrupts
cat /proc/ioports

```

Also, please see **[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87078/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87078/comments/22)** - maybe your problem will only be fixed in 2.6.23.

---

### Post by aneeshkj on 2007-11-05
Output of ifconfig -a [here]("http://aneeshkj.googlepages.com/ifconfig.txt")
Output of cat /proc/interrupts ; sleep 5; cat /proc/interrupts [here ]("http://aneeshkj.googlepages.com/cat1.txt")
Output of cat /proc/ioports [here ]("http://aneeshkj.googlepages.com/cat2.txt")

---

### Post by aneeshkj on 2007-11-09
any idea guys..??
 :-)

---

### Post by aneeshkj on 2007-11-12
is there some DHCP fix that i can download on another system and apply on my ubuntu..??

---

