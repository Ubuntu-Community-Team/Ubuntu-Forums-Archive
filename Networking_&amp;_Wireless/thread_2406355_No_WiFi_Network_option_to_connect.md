---
title: "No WiFi Network option to connect"
date: 2018-11-19
forum: Networking &amp; Wireless
---

### Post by rarecaramels on 2018-11-19
Hi, i just installed Ubuntu Studio 18.04 in a Hp Compaq 6000 pro MT. 

The problem is that the option to wireless connection is not shown in the network manager. 

I read the rules before posting, and i try to run the wireless scrip to diagnose the problem, but I don't manage to work out in the Xfce environment... 

So i will post the results of

lspci -vvnn | grep -A 9 Network



00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection [8086:10de] (rev 02)

Subsystem: Hewlett-Packard Company 82567LM-3 Gigabit Network Connection [103c: 3048]

Control: I/0+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+

Status: Cap+ 66Mhz- UDF- FastB2B- ParErr- DEVSEL=fast <TAbort- <MAbort- >SERR- <PERR- INTx-

Latency: 0

Interrupt: pin B routed to IRQ 28

Region 0: Memory at f0500000 (32-bit, non-prefechable) [size=128k]

Region 1: Memory at f0525000 (32-bit, non-prefechable) [size=4k]

Region 2: I/0 ports at 1100 [size=32]

Capabilities: <access denied>

Kernel driver in use: e1000e

____________________________________________

I don't have access to cable or Ethernet, so i typed all to my cellphone, lol


Thank you in advance for the help &#128515;

---

