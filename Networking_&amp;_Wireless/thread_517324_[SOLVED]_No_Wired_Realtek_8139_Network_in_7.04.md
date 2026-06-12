---
title: "[SOLVED] No Wired Realtek 8139 Network in 7.04"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by chantron on 2007-08-04
I just got a new Acer Aspire 5050 notebook pretty cheap and rather than using Vista I decided to slap Ubuntu onto it.

I popped in the LiveCD (it was hanging on "Loading ACPI modules" at first, I had to add acpi=off to the boot command) and everything that I expected to work did. I had no problems with X and I had no problems with my built in NIC. 

I installed Ubuntu 7.04 from the LiveCD and I couldn't get my wired NIC to work. Its detected by Ubuntu, it has a driver loaded for it and sometimes it works for a split second. 

For instance, if I ping my router (192.168.0.1), typically it won't get a response. BUT if I leave ping running for say, a hundred packets, maybe 4 or 5 will get a reply with a pretty high latency. 

I installed Ubuntu Studio thinking it might have been an issue with the initial Ubuntu install and in Studio, the wired NIC worked fine. There were some other issues with Studio (it not booting off of the low-latency kernel which by default it was set to [why?] and some things I messed up trying to get acer_acpi working :p) and I went back and installed Ubuntu. Again, the same thing is happening.

I've searched these forums and found one other thread ([http://ubuntuforums.org/showthread.php?t=437687](http://ubuntuforums.org/showthread.php?t=437687)) detailing a similar problem to mine. 

I tried setting the NIC to half duplex via ethtool and that didn't fix it. The settings don't seem to even change. 

I'd appreciate any help you can give me because I just don't know what to do.

Thanks a lot!

---

### Post by chantron on 2007-08-04
OK so I found a thread on linuxquestions ([http://www.linuxquestions.org/questions/showthread.php?t=571844&highlight=ubuntu+realtek+8139](http://www.linuxquestions.org/questions/showthread.php?t=571844&highlight=ubuntu+realtek+8139)) that provides some help.

The dude in that thread had the same issue that I'm having. He added noapic and acpi=off when booting and it seemed to work for him. It didn't work for me though. 

That might explain why the NIC worked on the livecd (I booted with acpi=off) but why its not helping me now, I don't know.

Another thing, in the thread on these forums that I linked to, a poster mentioned that he had 
```
Interrupt:22 Base address:0xe400
```
at the end eth0's section in ifconfig.

I personally have 
```
Interrupt:16 Base address:0xcc00
```

People have said it happens to them in other distros (the guy on linuxquestions is running FC6)... whats letting it work in Ubuntu Studio for me?

---

### Post by noob12 on 2007-08-04
How about some info?

```

lspci -nn

lshw -C network

ifconfig -a

dmesg

```

Not excerpts please.

---

### Post by chantron on 2007-08-04
> **noob12 said:**
> How about some info?

```

lspci -nn

lshw -C network

ifconfig -a

dmesg

```

Not excerpts please.

Here you are sir.

I've attached them because theres a lot of text in them.

Thanks a lot.

---

### Post by noob12 on 2007-08-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/124542](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/124542) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Try booting with **pci=assign-busses**.  I'm assuming since you mentioned using boot flags in your earlier message you know how to do this.  If you need further help though, please let me know. 

Why do I suggest this?

> 
[    0.064052] PCI: Transparent bridge - 0000:00:14.4
[    0.064134] PCI: Bus #09 (-#0c) is hidden behind transparent bridge #08 (-#09) (try 'pci=assign-busses')
[    0.064136] Please report the result to linux-kernel to fix this permanently
[    0.068623] PCI: Using IRQ router default [1002/4372] at 0000:00:14.0
[    0.068638] PCI->APIC IRQ transform: 0000:00:12.0[A] -> IRQ 22
[    0.068643] PCI->APIC IRQ transform: 0000:00:13.0[A] -> IRQ 19
[    0.068647] PCI->APIC IRQ transform: 0000:00:13.1[A] -> IRQ 19
[    0.068651] PCI->APIC IRQ transform: 0000:00:13.2[A] -> IRQ 19
[    0.068657] PCI->APIC IRQ transform: 0000:00:14.1[A] -> IRQ 16
[    0.068661] PCI->APIC IRQ transform: 0000:00:14.2[A] -> IRQ 16
[    0.068675] PCI: using PPB 0000:00:14.4[B] to get irq 16
[    0.068677] PCI->APIC IRQ transform: 0000:08:01.0[B] -> IRQ 16
[    0.068682] PCI: using PPB 0000:00:14.4[C] to get irq 16
[    0.068684] PCI->APIC IRQ transform: 0000:08:01.1[C] -> IRQ 16
[    0.068689] PCI: using PPB 0000:00:14.4[C] to get irq 16
[    0.068691] PCI->APIC IRQ transform: 0000:08:01.2[C] -> IRQ 16
[    0.068696] PCI: using PPB 0000:00:14.4[C] to get irq 16
[    0.068698] PCI->APIC IRQ transform: 0000:08:01.3[C] -> IRQ 16
[    0.068703] PCI: using PPB 0000:00:14.4[C] to get irq 16
[    0.068706] PCI->APIC IRQ transform: 0000:08:01.4[C] -> IRQ 16
[    0.068711] PCI: using PPB 0000:00:14.4[C] to get irq 16
[    0.068713] PCI->APIC IRQ transform: 0000:08:02.0[C] -> IRQ 16
[    0.068718] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[    0.068721] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[    0.068724] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[    0.068726] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[    0.068729] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[    0.068731] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0


And it is probably leading to this repeated behavior and the link being flaky.

> 
[   76.600000] NETDEV WATCHDOG: eth0: transmit timed out
[   79.600000] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[   79.600000] eth0: Tx queue start entry 32  dirty entry 28.
[   79.600000] eth0:  Tx descriptor 0 is 0008a062. (queue head)
[   79.600000] eth0:  Tx descriptor 1 is 0008a062.
[   79.600000] eth0:  Tx descriptor 2 is 0008a062.
[   79.600000] eth0:  Tx descriptor 3 is 0008a062.


Regarding your experience with Ubuntu Studio, if you want to look at that mystery, you would need to capture the **dmesg** output when you boot Ubuntu Studio; we expect it to be different.

---

### Post by chantron on 2007-08-04
Maybe I haven't been doing it right. 

I've been hitting esc when I see grub loading, then I've been 'e' on the kernel that I want it to boot. Then I've been adding the options after quiet.

Is that the right way to do it?

---

### Post by noob12 on 2007-08-04
Yes.  Hit ESC, then e then find the kernel command line and again hit e.  Append the option there.
This is a different option from acpi=off.  You had that.  (I'm not even sure you need that but ok.)
What you need to add is  **pci=assign-busses**

Running dmesg after you do this will show what the kernel command line options are and that will give us confirmation that you have the right option set

You were not using the option on the boot you showed me.  You were using
> 
Kernel command line: root=UUID=5a2cbea2-27fb-4a02-87a2-5614aa82cf85 ro quiet splash acpi=off


After you reboot, you'll see a line like this in dmesg with the new option if you have set it correctly.  Once you have it set correctly, if you still have problems, send the dmesg output again.

---

### Post by chantron on 2007-08-04
> **noob12 said:**
> Yes.  Hit ESC, then e then find the kernel command line and again hit e.  Append the option there.
This is a different option from acpi=off.  You had that.  (I'm not even sure you need that but ok.)
What you need to add is  **pci=assign-busses**

Running dmesg after you do this will show what the kernel command line options are and that will give us confirmation that you have the right option set

You were not using the option on the boot you showed me.  You were using


After you reboot, you'll see a line like this in dmesg with the new option if you have set it correctly.  Once you have it set correctly, if you still have problems, send the dmesg output again.

OKAY.

I feel very stupid right now.

I realized that I wasn't putting in the boot flags right.

I put in the boot flag noapic and now the NIC works.

When I take out the acpi=off ubuntu won't boot, it will hang when it gets to "Loading ACPI modules".

dmesg also reports that there is an error with my bios. The acer website has an update that requires windows... it flashes the bios from within windows. The error in dmesg suggests I add pnpbios=off.

Maybe updating the kernel will fix these issues?

I'm going to try a combination of different boot flags to see what happens :p

Thanks a lot.

---

### Post by noob12 on 2007-08-04
You may already know this, but once you figure out the options you can store them in /boot/grub/menu.lst

Let me know if you need more help.

---

### Post by chantron on 2007-08-04
> **noob12 said:**
> You may already know this, but once you figure out the options you can store them in /boot/grub/menu.lst

Let me know if you need more help.

Yeah as soon as I got it working I added it.

pci=assign-busses doesn't seem to do anything. 

I saw that dmesg was complaining about a bios error (the only updates on acer's website require vista to flash the bios from within windows) so i added pnpbios=off as it suggested. What does this disable?

With acpi=off am I going to be able to use my wireless nic?

thanks for all your help.

---

### Post by noob12 on 2007-08-04
pnpbios=off means that the kernel will treat your BIOS as not plug and play compatible.  Some BIOSs will have a setting that you have to tell them that the OS is a plug-and-play OS.  Check that.  Turn it on if you find it.

Your other options may have settled the bus assignment issue.  As long as you are not getting the errors in dmesg of the type I had pointed out and which were suggesting the pci=assign-busses option you don't need to add it.

ACPI is the event interface, mostly for power management.  I don't know whether turning it off will affect your wireless.  We'll have to see.

I can help you with that too, but you should start a new thread for the wireless.

---

### Post by noob12 on 2007-08-04
I forgot to say that yes if you have BIOS updates available that you can install from Windows, you should probably do that.  Note that updating the BIOS often results in resetting BIOS settings to factory defaults, so if you've set things up you may need to review them.

---

### Post by chantron on 2007-08-05
> **noob12 said:**
> I forgot to say that yes if you have BIOS updates available that you can install from Windows, you should probably do that.  Note that updating the BIOS often results in resetting BIOS settings to factory defaults, so if you've set things up you may need to review them.

I'll have to install windows to do that, not that its a big problem. I can't believe that they'd only offer a BIOS update via a windows only program. 

Another problem, updating to kernel 2.6.20-16 has caused my sound not to work. 

dmesg is flooded with these entires:
```

[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
[   24.520000] hda_codec: invalid dep_range_val 0:7fff
```

*sigh*
Booting in the previous kernel works fine.

---

### Post by noob12 on 2007-08-05
You might try starting a thread in one of the other forums for the sound card problem.  Don't know much about that.

---

### Post by chantron on 2007-08-05
> **noob12 said:**
> You might try starting a thread in one of the other forums for the sound card problem.  Don't know much about that.

Its not high on my priority list since booting into the older kernel makes it work but I will do that.

Next on my list is wireless... new thread incoming!

For those of you that might want a quick resolution if you're experiencing a similar problem without reading through the whole thread. **Add the noapic flag when you boot** it worked for me... just make sure you do it in the right spot!
:lolflag:

---

