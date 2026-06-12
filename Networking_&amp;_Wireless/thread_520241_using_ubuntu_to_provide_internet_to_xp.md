---
title: "using ubuntu to provide internet to xp"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by bradshoults on 2007-08-07
I cant (i am a newbe) seem to get the xp box to connect to the internet. I have cox internet and i ran firestarter as a post said but the xp box still cant connect to the inter net. I have two nic'c in the ubuntu box one in the xp box and a switch connecting them, the cox modem is connected to the ubuntu box.  How can I get the xp box to see the connection?  I can ping in both directions.:confused:

---

### Post by ruibernardo on 2007-08-08
Did you configured Firestarter. I mean, did you go to the Gnome menu in "System", "Administration" and clicked on "Firestarter"?

If you do it, on the first execution it will start to an "Assistant". While you set things in the Assistant it will ask you to set the "network sharing". You have to activate this.

---

### Post by bradshoults on 2007-08-12
I have been trying, with no luck, to get my network set up and have discovered that the two nic's in the dell are sharing the same IRQ.  How can I fix this?

brad@brad-home:~$ cat /proc/interrupts
           CPU0       
  0:    6542919   IO-APIC-edge      timer
  1:       1109   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          1   IO-APIC-fasteoi   acpi
 12:     251439   IO-APIC-edge      i8042
 14:      47228   IO-APIC-edge      libata
 15:     287495   IO-APIC-edge      libata
 16:   14703817   IO-APIC-fasteoi   uhci_hcd:usb1, i915@pci:0000:00:02.0
 17:         40   IO-APIC-fasteoi   uhci_hcd:usb2
 18:     118933   IO-APIC-fasteoi   uhci_hcd:usb3, eth0, eth1
 19:          2   IO-APIC-fasteoi   ehci_hcd:usb4
 20:        961   IO-APIC-fasteoi   Intel 82801DB-ICH4
NMI:          0 
LOC:    6543400 
ERR:          0
MIS:          0

---

### Post by bradshoults on 2007-08-12
I have been trying to get my two computers networked and have had no luck, I understand that you are all busy, but I still need some help.
I have a dell, this pc and an emachine and I cant get the two to see each other. I think the problem is with the dell as it has two nic's.  pleas help.

---

### Post by bradshoults on 2007-08-12
Because when we try to get help we get none: at least I haven't been able to. HELP!!!!!!!!!!!!

---

### Post by g2g591 on 2007-08-12
perhaps this would have better luck in the general help forum???

---

### Post by bradshoults on 2007-08-12
I can't seem to get help any any of the forms, this one , hardware, or net working. Why should general be any better?

---

### Post by mikelucasiscool on 2007-08-12
Hey, well i don't know how much help i can be, but firstly start off by telling everyone what operating system are you running, what version etc.

What problem are you having exactly? do you not know where to begin, or have you tried and it's giving you an error message? if so what? if not is it just not working? what are you trying?

Do you know the ips and other related network information on the computers? do they have firewalls? are they password protected? when you say you want to network them, what is your purpose are you trying to set up a shared folder between the two, or enable remote access or what?

you can pm me if you need help in windows, i will try to help you with linux, but to be honest i haven't done those things in linux yet so i probably can't be to much help, you might want to repost this post with a title that has more information, you may not attract to many people who can help you with such a vague title.

Hope those suggestion questions help :)

- T4ct1cs

ps that's odd something wrong with the scrolling in my browser i see now you posted more of the specifics please disregard above :S *looks confused*

---

### Post by aysiu on 2007-08-12
Please stop whining about getting help.

1. Everyone on here is a volunteer.

2. Everyone on here has limited knowledge. We are not omniscient. We are not able to solve **all** conceivable problems. Please consider that your problem may be beyond the scope of what people here know.

3. Someone responded to you and you didn't respond in turn with saying you tried that and what error message you got. Help others help you. It's a dialogue.

4. If you keep complaining about the help you are not getting or keep "bumping" your problem unnecessarily or creating extraneous threads or hijacking other threads, I will give you an infraction.

Be polite. Be patient. Keep in mind that people here are human (not all-knowing Ubuntu machines) and volunteers.

---

### Post by bradshoults on 2007-08-12
I was not trying to be rude, and I have very limited time frame, at most two hours a week to use my home computers, that is why i got impatient, forgive me.  Any way, my dell's ip is: 
th0      Link encap:Ethernet  HWaddr 00:50:BA:F7:08:8D  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fef7:88d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:125
          collisions:0 txqueuelen:1000 
          RX bytes:2765146 (2.6 MiB)  TX bytes:35093 (34.2 KiB)
          Interrupt:18 Base address:0xec80 

eth1      Link encap:Ethernet  HWaddr 00:0B:DB:63:82:58  
          inet addr:72.218.26.191  Bcast:72.218.27.255  Mask:255.255.252.0
          inet6 addr: fe80::20b:dbff:fe63:8258/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:52 txqueuelen:100 
          RX bytes:34351159 (32.7 MiB)  TX bytes:3056547 (2.9 MiB)
          Base address:0xec40 Memory:ff8c0000-ff8e0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:996 (996.0 b)  TX bytes:996 (996.0 b)
 and I have the emachine set up as 192.168.0.3
I got a huge dmesg file:
[12818.855662] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=14549 PROTO=UDP SPT=67 DPT=68 LEN=318 
[12827.163226] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=14629 PROTO=UDP SPT=67 DPT=68 LEN=318 
[12978.223917] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=15590 PROTO=UDP SPT=67 DPT=68 LEN=318 
[13098.564022] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=16358 PROTO=UDP SPT=67 DPT=68 LEN=318 
[13376.629963] Inbound IN=eth1 OUT= MAC= SRC=72.218.26.191 DST=72.218.27.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241 
[13376.630011] Inbound IN=eth1 OUT= MAC= SRC=72.218.26.191 DST=72.218.27.255 LEN=238 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=218 
[13450.744192] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=344 TOS=0x00 PREC=0x00 TTL=255 ID=18601 PROTO=UDP SPT=67 DPT=68 LEN=324 
[13450.754660] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=344 TOS=0x00 PREC=0x00 TTL=255 ID=18603 PROTO=UDP SPT=67 DPT=68 LEN=324 
[13603.772882] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=19560 PROTO=UDP SPT=67 DPT=68 LEN=318 
[13725.787130] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:54:ca:f5:05:08:00 SRC=10.2.112.1 DST=255.255.255.255 LEN=338 TOS=0x00 PREC=0x00 TTL=255 ID=20319 PROTO=UDP SPT=67 DPT=68 LEN=318 
I I tried firestarter and got the"unknown error" message

---

### Post by bradshoults on 2007-08-12
At first I tried to had only the ubuntu pc, the dell, then I added the xp, emachines, and at that point I tried to get them to connect using firestarter per a post in the networking fourm, that failed so i tried some of the other ideas in the same fourm - manual config and got nowhere.  It was then that i posted the first question and about an hour later my job called and I had to leave town for a few days, so tonight I tried to start it again,but this time I installed ubuntu on the emachine hoping that they would be able to see each other, no such luck.  I am thinking that the problem is with the two nics in the dell, one is a Dlink and the other is builtin intel gigabit nic.  If I lspci I get the following:
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 12)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

The system-administration-network for eto0 says:
static IP address
192.168.0.1
255.255.255.0
72.218.24.95
and for eth1:
automatic DHCP
this is probably the wrong setup for eth1?

---

