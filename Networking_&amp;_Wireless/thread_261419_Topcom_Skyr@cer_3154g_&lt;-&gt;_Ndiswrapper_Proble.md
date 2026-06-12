---
title: "Topcom Skyr@cer 3154g &lt;-&gt; Ndiswrapper Problem :("
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by Merlin_KA on 2006-09-20
Hi

I'm a bloody rookie in Linux and I have a problem with my SKyr@cer 3154g PCMCIA-Card.
All I found out about it with:
```
lspci
```

"0000:06:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)"

After reading some forums in the internet i figured out that I need the Ndiswrapper to get my Wireless-PC-Card working.
And so, after some tries I got the Ndiswrapper installed for my Kernel and all this stuff. ( I resigned after some hours and finally a friend of mine did all the work for me )
Hurra! One step closer at least.

Next step: searching for my driver.
I found my driver for the PC-Card, downloaded it and installed the WinXP-driver into Ndiswrapper with
```
ndiswrapper -i 
```

next i saw was:
```
Installing mrv8k51
Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg
Parse error in inf. Unable to find section W8100PCI.zerocfg

```

:confused: 

ok, obviously some errors. So I tried the driver for Win2k
no errors until now? --> fine! :D 

checked ndiswrapper:
```
ndiswrapper -l
Installed drivers:
mrv8k51         driver installed, hardware present

```
thank god, it really works! :razz: 

next to do was 
```
modprobe ndiswrapper
```

no errors, so I thought: Yes! :KS 

so i followed the instructions on the ndiswrapper-page on typed
```
dmesg
```
to look after the log-files and was hit with this:
```

[ 1089.422206] pccard: card ejected from slot 1
[ 1093.203672] pccard: CardBus card inserted into slot 1
[ 1093.204327] mrv8k: mrv8k_init_one: enter
[ 1093.204345] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[ 1093.204402] PCI: Setting latency timer of device 0000:06:00.0 to 64
[ 1093.205276] mrv8k: bar1 (0x36000000) relocated at 0xd8ea0000
[ 1093.205280] mrv8k: bar2 (0x36010000) relocated at 0xd9160000
[ 1093.209194] mrv8k: Firmware 'mrv8k-b.fw' not available or load failed.
[ 1093.209204] mrv8k: mrv8k_init_one: return -2
[ 1093.209210] mrv8k: Command SET_RADIO. len=12 state=off preamble=auto
[ 1093.209213] mrv8k: queue command (c84c2400)
[ 1093.209215] mrv8k: kickoff command (c84c2400)
[ 1094.233771] mrv8k: mrv8k_init_one: return -2
[ 1094.233780] mrv8k: probe of 0000:06:00.0 failed with error -2

```

ouch, smashed again :( 

I can't get any further, so can anybody help me please? 

Thank you all for help

Merlin

edit:
I tried the Win98-driver too a few minutes ago and I received another error. maybe it's easier with this one:
```
ndiswrapper version 1.23 loaded (preempt=yes,smp=no)
[17179614.952000] ndiswrapper: driver mrv8k51 (,12/21/2003,2.2.0.19) loaded
[17179614.952000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNK4] -> GSI 10 (level, low) -> IRQ 10
[17179614.952000] ndiswrapper: using irq 10
[17179614.968000] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[17179614.968000] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[17179614.968000] ndiswrapper (miniport_halt:327): device d3913260 is not initialized - not halting
[17179614.968000] ndiswrapper: device eth%d removed
[17179614.968000] unregister_netdevice: device eth%d/d3913000 never was registered
[17179614.968000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[17179614.968000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
```

edit2:
Hey! I finally got the Wlan-Card working!
Just follow the instructions mentioned in this post ( by DaveZ )
[http://ubuntuforums.org/showthread.php?t=190726&highlight=marvell+w8300+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=190726&highlight=marvell+w8300+ndiswrapper")
for deleting the bugged "mrv8k.ko" file wich is originally used by the kernel for this typ of Chipset, reboot, load the ndiswrapper again and all is fine :) 

good luck
Merlin

---

