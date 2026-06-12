---
title: "DHCP daemon freezes Feisty"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by kenji-san on 2007-09-15
I've searched around for this problem but I can't seem to find an answer.  So, sorry if this is redundant.

My system periodically freezes completety, no mouse, sometimes no screen (just empty boxes), no keyboard, no ctrl-alt-backspace, no ctrl-alt-delete.  I can only use atl-sysrq to reboot the system.  It has done this many times but it only did it once while I was actually using the system, the rest of the time it happens while I'm away and come back to a frozen computer.

After checking system logs periodically over the past week, the networking and DHCP daemons seem suspect.  Here is a snippet from my syslog:
```
Sep 15 15:36:33 shinobu NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Sep 15 15:36:33 shinobu dhclient: bound to 207.228.60.174 -- renewal in 258 seconds.
Sep 15 15:40:51 shinobu dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Sep 15 15:41:09 shinobu last message repeated 2 times
Sep 15 15:41:18 shinobu dhclient: DHCPACK from 192.168.0.1
Sep 15 15:41:18 shinobu kernel: [17100.064000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 15 15:41:18 shinobu kernel: [17100.064000] eth0: transmit timed out, tx_status 00 status e601.
Sep 15 15:41:18 shinobu kernel: [17100.064000]   diagnostics: net 0ccc media 8880 dma 0000003a fifo 0000
Sep 15 15:41:18 shinobu kernel: [17100.064000] eth0: Interrupt posted but not delivered -- IRQ blocked by another device?
Sep 15 15:41:18 shinobu kernel: [17100.064000]   Flags; bus-master 1, dirty 19813(5) current 19813(5)
Sep 15 15:41:18 shinobu kernel: [17100.064000]   Transmit list 00000000 vs. c1beb520.
Sep 15 15:41:18 shinobu kernel: [17100.064000]   0: @c1beb200  length 80000156 status 0c010156
Sep 15 15:41:18 shinobu kernel: [17100.064000]   1: @c1beb2a0  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   2: @c1beb340  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   3: @c1beb3e0  length 8000002a status 8001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   4: @c1beb480  length 8000002a status 8001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   5: @c1beb520  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   6: @c1beb5c0  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   7: @c1beb660  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   8: @c1beb700  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   9: @c1beb7a0  length 8000006a status 0001006a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   10: @c1beb840  length 8000006a status 0001006a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   11: @c1beb8e0  length 8000006a status 0001006a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   12: @c1beb980  length 8000006a status 0001006a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   13: @c1beba20  length 80000156 status 0c010156
Sep 15 15:41:18 shinobu kernel: [17100.064000]   14: @c1bebac0  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000]   15: @c1bebb60  length 8000002a status 0001002a
Sep 15 15:41:18 shinobu kernel: [17100.064000] eth0: Resetting the Tx ring pointer.
```
I also get IP assignments for only between 250-350 seconds and then it resets.  I'm not sure if this is in my system or it is a problem with my internet service DHCP servers.  Somehow, just after I get the errors above, it completely freezes my system.

One time it froze and when I got to the computer, the "activity" light on my DSL modem was flashing like crazy.  I notice that at times, the modem gets quite hot.  To help with that problem, I put the modem on top of my computer, just over an air intake vent and that keeps it much cooler but doesn't solve the crashing problem.

Is there a solution for this?  I have an onboard NIC that I can use to test the problem, if that would help.

Thank you for reading my post.


My hardware:
ASUS M2N motherboard
AMD64x2 3800+
512x2 DDR2
nVidia GeForce 7600GS
3COM PCI NIC coupled to a speedstream DSL modem (no router)
Feisty Fawn with all available updates/fixes.

---

### Post by noob12 on 2007-09-16
It's not DHCP per se.  The following indicates that it is the ethernet driver and it has been given a bad IRQ assignment.

```

Sep 15 15:41:18 shinobu kernel: [17100.064000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 15 15:41:18 shinobu kernel: [17100.064000] eth0: transmit timed out, tx_status 00 status e601.
Sep 15 15:41:18 shinobu kernel: [17100.064000]   diagnostics: net 0ccc media 8880 dma 0000003a fifo 0000
Sep 15 15:41:18 shinobu kernel: [17100.064000] eth0: Interrupt posted but not delivered -- IRQ blocked by another device?
Sep 15 15:41:18 shinobu kernel: [17100.064000]   Flags; bus-master 1, dirty 19813(5) current 19813(5)

```

Can you post the output of this command:

```

lspci -nn

```

In any case I would try booting with the flag **pci=noacpi** and seeing if that helps.  If you need instructions to do that let us know.

---

### Post by kenji-san on 2007-09-16
Thank you for the informative reply.

I have just rebooted after adding the **pci=noapci** flag to my menu.list.  Let's see if it crashes!  I also added noapic and nolapic.

Here is my output from lspci:
```
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a2)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:08.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
01:09.0 RAID bus controller [0104]: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller [1095:0680] (rev 02)
01:0a.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
01:0a.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
01:0a.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GS] [10de:0392] (rev a1)
```

---

### Post by noob12 on 2007-09-16
I'm not sure if you needed the additional flags disabling the apic.  If it works, try it with just the one I suggested.  It will be interesting to know what worked in any case.

---

### Post by kenji-san on 2007-09-16
OK, for some reason either I am ignorant or GRUB is not cooperating.

I edited /boot/grub/menu.lst and added those parameters the the default kernel.  Then I ran "sudo update-grub" and I didn't get any errors.  Upon reboot, my edits were gone.  I really don't have a firm grasp on GRUB and it has been a very long time since I used it last.

On the DCHP front, I am still getting IP leases for less than 5 minutes.
From my syslog:
```
Sep 16 13:28:28 shinobu dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Sep 16 13:28:28 shinobu dhclient: DHCPACK from 192.168.0.1
Sep 16 13:28:28 shinobu NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Sep 16 13:28:28 shinobu dhclient: bound to 207.228.62.150 -- renewal in 250 seconds.
```
I get this repeatedly until it acts up and kills my system.

Any thoughts?

---

### Post by noob12 on 2007-09-16
For the boot flags, once you edit /boot/grub/menu.lst you do not need to run anything.  It should be in your menu.  You can verify if you got the flags on boot by looking **dmesg | grep 'Kernel command line'**.

If necessary, type e at the boot-time menu, navigate to the kernel line and e again to edit it for that one boot.  Hit Enter and b to boot.

The lease time is usually configured on the DHCP server end.

---

### Post by kenji-san on 2007-09-16
Thank you for the reply.
> **noob12 said:**
> The lease time is usually configured on the DHCP server end.
That is what I thought but I don't understand what is crashing my system.

---

### Post by noob12 on 2007-09-16
If you can solve your IRQ conflict, I think your troubles will be resolved.

---

### Post by kenji-san on 2007-09-21
Several days without any instability or freezes.  It seems that the pci=noacpi option fixed it.  :)

Thanks for your help.

---

### Post by irolav on 2007-10-08
Hi,
I have the same problem with my MSI M670 notebook.
I don't know how to check if I have an IRQ conflict: if I type cat /proc/interrupts I get this:
```

           CPU0       
  0:    1282649    XT-PIC-XT        timer
  1:        965    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:        801    XT-PIC-XT        HDA Intel
  7:      26043    XT-PIC-XT        ohci_hcd:usb1
  8:          3    XT-PIC-XT        rtc
  9:       3302    XT-PIC-XT        acpi
 10:     868541    XT-PIC-XT        libata, ohci1394, eth0, sdhci:slot0, nvidia
 11:     113582    XT-PIC-XT        libata, ra1
 12:        140    XT-PIC-XT        i8042
 14:          2    XT-PIC-XT        ehci_hcd:usb2
 15:      45950    XT-PIC-XT        ide1
NMI:          0 
LOC:    1282531 
ERR:          1
MIS:          0
```

but I'm not able to find if something is wrong :confused:
I also tried the solution pci=noacpi but it doesn't work:
```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1c11f6e8-3135-49a4-9554-5c6f39ce23f8 ro quiet splash pci=noacpi noapic nolapic
```
(is it correct?)
At last I uninstalled Network Manager and installed Wicd but I still have the same problem...
If I use a fix IP I have no problems at all but if I try to connect with a network with Dhcp the system freezes after a few minutes.
Can you pleas help me? I don't want to put back windows...! :(

---

