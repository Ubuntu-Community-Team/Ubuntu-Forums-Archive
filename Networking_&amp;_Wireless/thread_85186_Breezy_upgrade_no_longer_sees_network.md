---
title: "Breezy upgrade: no longer sees network"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by BrianS on 2005-11-02
Hello all,

I'm having a networking problem that is driving me nuts.  I installed Hoary (dual-boot with W2k) on my PC a few months ago, and it worked great -- autodetected everything, no problems.  This past weekend, I decided to upgrade to breezy.  Changed everything in Synaptic, fired it off.  Everything went fine, no problems, EXCEPT now the systems does not see my ethernet card.

I burned a live breezy cd and tried that; it also did not identify my ethernet card.  Even more interestingly, on boot-up, I can still see the old 2.6.10 kernel; if I start breezy using 2.6.10, the networking works.

Using the 2.6.12 kernel, I can see the ethernet card using lspci, but I cannot see eth0 using ifconfig -a.  (I can also ping lo without any problem.)  When I try sudo ifconfig etho I get "error fetching interface information: device not found."

Suggestions?  What am I doing wrong?  My system is an older 750MHz Athlon and a Linksys LNE100TX ethernet card (identified as an NC100), connected to a Linksys cable modem.  The following is the output from sudo lspci -v:

0000:00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Linksys: Unknown device 0574
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at de00 [size=256]
        Memory at effffc00 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at effc0000 [disabled] [size=128K]
        Capabilities: [c0] Power Management version 2

The following is the ifconfig output from 2.6.10, which is the older kernel that works:
eth0      Link encap:Ethernet  HWaddr 00:04:5A:69:87:95
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3422877 (3.2 MiB)  TX bytes:437610 (427.3 KiB)
          Interrupt:10 Base address:0xde00

Thanks for any help,
Brian

---

### Post by costoa on 2005-11-02
Could you please post the output from "ifconfig" (a list of all network devices).

costoa

---

### Post by BrianS on 2005-11-02
Sure.  ifconfig only shows the loopback device:

lo     Link encap: local loopback
       inet address:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:2327 errors:0 dropped:0 overruns:0 frame:0
       TX packets:2327 errors:0 dropped:0 overruns:0 carrier:0

ifconfig -a shows only lo and sit0

That lspci does show the ethernet card.

Thanks,
Brian

---

### Post by costoa on 2005-11-02
Ouch. Well, since lo is up we know your IP stacks are functioning. So your machine sees the card **but** doesn't see it as a NIC. My first guess is a bug was introduced into the driver. Simplest workaround is if you have another ethernet card swap it out for the linksys. Clearly not the best solution but it could get you going in a few minutes.

I'll research this some more and followup.

costoa

---

### Post by BrianS on 2005-11-02
Yes, not good.  Unfortunately, I don't have an extra ethernet card here at home; I may try to borrow one from work tomorrow.

I've been looking at the output from "sudo dmesg."  On the 2.6.10 kernel (ethernet working) I'm seeing:

Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 10 (level, low) -> IRQ 10
tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
tulip0:  MII transceiver #2 config 1000 status 786d advertising 05e1.
tulip0:  MII transceiver #3 config 1000 status 786d advertising 05e1.
tulip0:  MII transceiver #4 config 1000 status 786d advertising 05e1.
eth0: ADMtek Comet rev 17 at 0001de00, 00:04:5A:69:87:95, IRQ 10.  

From the 2.6.12 kernel (ethernet not found) I see:

[4294679.670000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294679.670000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294679.670000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0b.0

Looks like an interrupt conflict?  In 2.6.12 IRQ10 may be being used by ACPI.  Looking in /proc/interrupts for 2.6.10 I see:

besst@BESLinux:~$ more /proc/interrupts
           CPU0
  0:    1056530          XT-PIC  timer
  1:        320          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          1          XT-PIC  parport0
  8:          1          XT-PIC  rtc
  9:       2817          XT-PIC  Ensoniq AudioPCI
 10:       7513          XT-PIC  ohci_hcd, eth0
 11:          1          XT-PIC  acpi
 12:      37226          XT-PIC  i8042
 14:       9746          XT-PIC  ide0
 15:      17334          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

I need to reboot in 2.6.12 and see what I see.  Also, can I boot with ACPI off?  Google shows some stuff on the LKML about "Unable to reserve I/O region."  I'm almost proud to have a problem that Alan Cox and Andrew Morton have worked on.
Almost. 

Thanks for the help,
Brian

---

### Post by BrianS on 2005-11-02
Fixed.

It seems to have been an interrupt conflict with ACPI.  I added "acpi=no" to GRUB, and now everything is working fine.  The issue is with a desktop PC, so I'm not overly concerned about killing ACPI.

I assume some minor tweak in the 2.6.12 kernel ACPI code was the problem -- perhaps when I get a chance I'll install 2.6.14 and see what happens. 

Thanks again costoa,
Brian

---

