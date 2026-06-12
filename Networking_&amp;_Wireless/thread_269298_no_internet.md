---
title: "no internet"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by brien zee on 2006-10-01
i cannot connect to the internet. the live cd didn't connect either..
i have a kt4v motherboard wtih a built in via VT6103 lan controller.
i can't connect to my router through 192.168.1.1 either.
i can't figure out how to check if my lan card was even detected or figure out what is wrong..
any help would be apperciated.

thanks

---

### Post by mips on 2006-10-01
Post the output of **lspci -v**    &    **ifconfig -a** here.

---

### Post by brien zee on 2006-10-01
alright, i'll do that in a little bit..
right now i'm reinstalling windows so i can do a dual boot. then i'll reinstall ubuntu, then post it up.

also, knoppix has always booted up with internet working.. is there a way to get the settings from that and transfer then to ubuntu?

---

### Post by mips on 2006-10-01
Ok, i'm going to bed now but will have a look in the morning.

Just a tip, install the **ext2ifs** driver in windows, google to find it. It will allow you to read your Linux ext2/3 partitions. So when you capture the info just save it as a text file in your home directo. Boot into windows and access the info then post it here. Some people battle getting things from linux to windows.

---

### Post by brien zee on 2006-10-01
thanks for that info. i've used ext2ifs before..
i didn't even think of it though. i just copied everything to my usb flash drive...but here it is.

```

**lspci -v**


0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
        Subsystem: VIA Technologies, Inc.: Unknown device 0000
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: dfd00000-dfdfffff
        Prefetchable memory behind bridge: 9fc00000-dfbfffff
        Capabilities: <available only to root>

0000:00:06.0 Mass storage controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. SiI 3112 SATALink Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 169
        I/O ports at ec00 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e400 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at dc00 [size=16]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at dff00000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d000 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d400 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d800 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: VIA Technologies, Inc.: Unknown device 0000
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: bus master, medium devsel, latency 32, IRQ 255
        I/O ports at fc00 [size=16]
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7120
        Flags: medium devsel, IRQ 185
        I/O ports at cc00 [size=256]
        Capabilities: <available only to root>


```

```

**ifconfig -a**

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited: Unknown device 7c20
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 193
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at b800 [size=256]
        Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at dfdc0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
        Subsystem: PC Partner Limited: Unknown device 7c21
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Memory at dfde0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>



```

---

### Post by mips on 2006-10-01
lspci -v lists NO Ethernet Controllers at all ???
ifconfig -a output is weird, it should list the Ethernet interface configuration/status ?!?!

Is your LAN card onboard or a plug-in card ???

---

### Post by mips on 2006-10-01
Post the output of **sudo lshw -C network**

---

### Post by brien zee on 2006-10-01
it's onboard card.

i'll post it when i get home. i'm off to work.

---

### Post by mips on 2006-10-01
When you get the **boot:** prompt at the beginning try using the option [B]acpi=off

[/B]Do you know what via lan chipset is used ? VT6102 Rhine-II etc ?

---

### Post by brien zee on 2006-10-01
the msi website says VIA VT6103 LAN controller.. that's all i know...
i should put acpi=off right before i load ubuntu normally?
should i do that and then do get the sudo lshw -C network?
what is turning the acpi off going to do? what should i look for?


i'll post all that when i get back from work.
thanks

---

### Post by mips on 2006-10-01
[http://ubuntuforums.org/showthread.php?p=1537339](http://ubuntuforums.org/showthread.php?p=1537339)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/65526-networking-issues.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/65526-networking-issues.html)

---

### Post by brien zee on 2006-10-02
both of those links just confuse me... x.X

---

