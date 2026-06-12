---
title: "ath_hal, ath5k, ath_pci, once and for all, what are each of them?"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by eks on 2008-11-02
Hello,

I had Hardy with madwifi drivers working on a HP Pavilion DV6000. From "lspci -v" it has a:

```

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: fast devsel, IRQ 16
	Memory at f2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath5k, ath_pci

```

I've followed many suggestions [on this thread]("http://ubuntuforums.org/showthread.php?t=940048"), but still cannot get wifi to work. But with linux-backport-modules it has a ath5k, which did not had at first. I've searched on /etc/modprobe.d and it had many other files which blacklisted either ath_hal or ath_pci. I've commented all of them, but on boot it still is not able to start neither.

From a resumed "dmesg":

```

[   32.760704] ath_hal: module license 'Proprietary' taints kernel.
[   32.773391] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   32.801073] wlan: 0.9.4
[   32.824514] ath_pci: 0.9.4
[   32.824977] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
[   32.824989] ath_pci 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   32.825016] ath_pci 0000:03:00.0: setting latency timer to 64
[   32.850745] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   32.866829] ath_pci 0000:03:00.0: PCI INT A disabled
[   33.705535] ath5k_pci 0000:03:00.0: enabling device (0000 -> 0002)
[   33.705547] ath5k_pci 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   33.705558] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   33.706330] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   33.716292] ath5k phy0: failed to wakeup the MAC Chip
[   33.716421] ath5k_pci 0000:03:00.0: PCI INT A disabled
[   33.716433] ath5k_pci: probe of 0000:03:00.0 failed with error -5

```

If i just knew what the heck each of this modules were, and/or where they came from. For example, is any of them proprietary (I assume ath_hal is, right)? Which is the one with the new kernel? Which works with this card?

I've upgraded my wife's laptop to Intrepid so wifi would hopefully not break anymore on a new kernel update, but... sigh.....

Any help would be appreciated.


eks

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another way to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by eks on 2008-11-02
Well, I've made it working, somehow, by blacklisting ath_hal and ath_pci, leaving just ath5k. On Hardy I was using a manually installed madwifi driver, I think it might had left some residues on /etc/modprobe.d. There was a madwifi file where ath5k was being blacklisted.

So, if you are on Intrepid and still cannot use wifi with an Atheros card (I think you should be able to without manually installing any driver), you need to do two things, 1) install linux-backport-modules and 2) blacklist ath_pci and ath_hal.

To install the backport modules, just search for it on Synaptic or use apt-get, it's called ***linux-backports-modules-intrepid***. Then on System/Administration/Hardware Drivers make sure Atheros driver is activated.

To blacklist the old modules, do this:

```

gksudo gedit /etc/modprobe.d/blacklist

```

And add:

```

blacklist ath_hal
blacklist ath_pci

```

At the bottom of the file, and reboot.

**IF** after this steps you still cannot make it work, you probably have something left still blacklisting ath5k, thus making it not to load. You should search all the files on **/etc/modprobe.d** for all lines that had:

```

blacklist ath5k

```

And add a # before the start of the line, thus making it into a comment. If you, like me, is coming from a Hardy upgrade that had madwifi driver installed you will probably be on this situation.

The easier way to do this is have a Nautilus open as root and check for each file on that directory. You can do that with "gksudo nautilus" on alt+f2, but you should be **EXTREMELY CAREFULL** while doing this. If an admin doesn't like me saying this, please tell me and I will edit this post.

And while you are at it, or **anyone else, could please explain the differences between all ath_pci, ath_hal and ath5k modules?**

I really would like to understand what each of this modules are and where do they come from (ath5k comes from the backport-modules package, but where are the others??).

---

### Post by Arabiest on 2008-11-04
well this work for Ubuntu 8.10 too to get the wireless working?

---

### Post by eks on 2008-11-04
> **Arabiest said:**
> well this work for Ubuntu 8.10 too to get the wireless working?

I think it works ONLY on 8.10 (Intrepid Ibex). And only with Atheros wifi cards.

---

### Post by jgrabenbauer on 2008-11-04
Thank you so much. I have been surfing forums for a couple of months, and until now, I was never even close to having my wireless working! I am extremely thankful for this post.

Thanks!

Compaq Presario A900 with Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by ddennis69 on 2008-11-07
> **eks said:**
> Well, I've made it working, somehow, by blacklisting ath_hal and ath_pci, leaving just ath5k. On Hardy I was using a manually installed madwifi driver, I think it might had left some residues on /etc/modprobe.d. There was a madwifi file where ath5k was being blacklisted.

So, if you are on Intrepid and still cannot use wifi with an Atheros card (I think you should be able to without manually installing any driver), you need to do two things, 1) install linux-backport-modules and 2) blacklist ath_pci and ath_hal.

To install the backport modules, just search for it on Synaptic or use apt-get, it's called ***linux-backports-modules-intrepid***. Then on System/Administration/Hardware Drivers make sure Atheros driver is activated.

To blacklist the old modules, do this:

```

gksudo gedit /etc/modprobe.d/blacklist

```

And add:

```

blacklist ath_hal
blacklist ath_pci

```

At the bottom of the file, and reboot.

**IF** after this steps you still cannot make it work, you probably have something left still blacklisting ath5k, thus making it not to load. You should search all the files on **/etc/modprobe.d** for all lines that had:

```

blacklist ath5k

```

And add a # before the start of the line, thus making it into a comment. If you, like me, is coming from a Hardy upgrade that had madwifi driver installed you will probably be on this situation.

The easier way to do this is have a Nautilus open as root and check for each file on that directory. You can do that with "gksudo nautilus" on alt+f2, but you should be **EXTREMELY CAREFULL** while doing this. If an admin doesn't like me saying this, please tell me and I will edit this post.

And while you are at it, or **anyone else, could please explain the differences between all ath_pci, ath_hal and ath5k modules?**

I really would like to understand what each of this modules are and where do they come from (ath5k comes from the backport-modules package, but where are the others??).

when I check under system/hardware drivers it shows that the drivers are activated but not in use. is this normal, or how do i go about getting those drivers to be used?

---

### Post by xobo on 2008-11-10
Hello,

I am new to Linux. I installed Ubuntu 8.10 on Presario laptop. for  a while I have managed to make the wireless Atheros card work. But now it doesn't  work again. I need to know how I install the package linux-backport-modules. even after updating the software I still get the message:-

Couldn't find package linux-backport-modules.

Can anyone please tell me how to install it?/where can I get that?
thank you.

---

### Post by xobo on 2008-11-10
For some reasons after the recent automatic update of Ubunto, suddenly the wireless Athros works again. It could well be that the update supply  all the needed missing packages.

[COLOR="Red"][/COLOR]Thank you,:):popcorn::guitar:

---

### Post by cupevampe on 2008-11-11
thanks eks man, this worked for me

i got a fujitsusiemens amilo pi 2515 if it can be of help to anyone

thx again

:guitar:

---

### Post by seriously on 2008-12-24
I have installed linux-backports-modules-intrepid, but on System/Administration/Hardware Drivers Atheros was not be activated. I click to activate. And then i got in dmesg:
```
[  537.728784] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[  537.856335] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[  537.856362] ath_pci 0000:01:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
[  537.856387] ath_pci 0000:01:00.0: setting latency timer to 64
[  538.364509] MadWifi: ath_attach: Switching rfkill capability off.
[  538.411280] wifi0: Atheros AR2424 chip found (MAC 10.0, PHY SChip 6.1, Radio 10.2)
[  538.485783] ath_pci: wifi0: Atheros 5424/2424: mem=0xdfef0000, irq=19
[  538.518666] ath_pci 0000:01:00.0: PCI INT A disabled
[  538.519061] ath_pci 0000:01:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
[  538.519080] ath_pci 0000:01:00.0: setting latency timer to 64
[  539.027383] MadWifi: ath_attach: Switching rfkill capability off.
[  539.037855] wifi0: Atheros AR2424 chip found (MAC 10.0, PHY SChip 6.1, Radio 10.2)
[  539.049569] ath_pci: wifi0: Atheros 5424/2424: mem=0xdfef0000, irq=19

```
```
lsmod | grep ath
ath_rate_sample        21248  1 
ath_pci               216632  0 
wlan                  240624  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci

```
But i added ath_pci and ath_hal in blacklist-file and comment ath5k. ath_pci can see wifi-network, but i want to use ath5k. On second computer ath5k seems work.

Also i tried:
```
modprobe ath5k
FATAL: Module ath5k not found.
```

Who can help?

---

### Post by The Judderman on 2008-12-27
I've had a very similar problem on upgrading the kernel, and then unable to load ath5k.

Any ideas?

This is putting me off intrepid, and thinking of going back to hardy or changing to mandriva (where ath5k works out of the box).

But would love to stay with ubuntu if poss...

Help anyone?

---

### Post by kevdog on 2008-12-27
I believe ath5k is only included out of the box with Intrepid kernels and beyond (its a new FOSS driver).  For Hardy you need to add this.

---

### Post by The Judderman on 2009-01-01
> **seriously said:**
> I have installed linux-backports-modules-intrepid, but on System/Administration/Hardware Drivers Atheros was not be activated. I click to activate. And then i got in dmesg:
```
[  537.728784] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[  537.856335] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[  537.856362] ath_pci 0000:01:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
[  537.856387] ath_pci 0000:01:00.0: setting latency timer to 64
[  538.364509] MadWifi: ath_attach: Switching rfkill capability off.
[  538.411280] wifi0: Atheros AR2424 chip found (MAC 10.0, PHY SChip 6.1, Radio 10.2)
[  538.485783] ath_pci: wifi0: Atheros 5424/2424: mem=0xdfef0000, irq=19
[  538.518666] ath_pci 0000:01:00.0: PCI INT A disabled
[  538.519061] ath_pci 0000:01:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
[  538.519080] ath_pci 0000:01:00.0: setting latency timer to 64
[  539.027383] MadWifi: ath_attach: Switching rfkill capability off.
[  539.037855] wifi0: Atheros AR2424 chip found (MAC 10.0, PHY SChip 6.1, Radio 10.2)
[  539.049569] ath_pci: wifi0: Atheros 5424/2424: mem=0xdfef0000, irq=19

```
```
lsmod | grep ath
ath_rate_sample        21248  1 
ath_pci               216632  0 
wlan                  240624  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci

```
But i added ath_pci and ath_hal in blacklist-file and comment ath5k. ath_pci can see wifi-network, but i want to use ath5k. On second computer ath5k seems work.

Also i tried:
```
modprobe ath5k
FATAL: Module ath5k not found.
```

Who can help?

As you know I had a similar problem. I've resolved it by doing a clean install of Intrepid, installing all the updates with a wired connection, and then insalling linux-backports-modules-intrepid file. 
Now, I gather that the problem is that the module was compiled for the previous kernel, but with the kernel upgrade the module didn't work anymore. I thought that that could be resolved with just uninstalling linux-backports-*etc*, but no. Which is what led me to do a clean install.

Interestingly, when I installed the linux-backports-modules-intrepid stuff this time round, it also installed linux-backports-modules-linux-2.6.27-9-generic (or something very similar. Sorry, I can't remember what it was), which is my latest kernel. Maybe this has something to do with it. Have you tried booting with an earlier kernel (this normally appears in your grub menu) and see if ath5k works there?

Hope this is helpful.

The Judderman

---

### Post by tad_pole on 2009-01-02
Unfortunately, I cannot answer the original question, but I followed the instructions given here (install backports and blacklist) and was able to connect with my AR5212 (finally!!), but it disabled my graphics driver (Nvidia accelerated graphics driver) for my 9400GT graphics card.I can't enable it so I am stuck without visual effects. I suppose there is some fix, but I can't be bothered at this stage. Productivity is not helped with all these bugs.:(

---

### Post by RoundSparrow on 2009-01-03
> **eks said:**
>  Which is the one with the new kernel? Which works with this card?

In case you still care, I can answer one questoin.  ath_ahb is for AHB which is an alternate bus to PCI (or PCI Express).  your desktop computer won't use this, it is typically only used on routers and other embedded systems.

---

### Post by adinov on 2009-02-15
This thread did it!!! Its possibly the only one on the internet that clearly explains how to fix this massive problem. I bought a Thinkpad R50 for its Linux compatibility only to find that wireless didn't work !!

The thread that advised to install ath5k didn't quite work:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289014](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289014)
It fixed the wifi signal but I still could not connect to router after suspend and resume.

The problem was due to the conflict. By blacklisting ath_pci and ath_hal by sudo gedit /etc/modprobe.d/blacklist (as described in this thread) it worked!!!!

I suspect owners of other thinkpads such as R50p, R51, R52, etc will be having similar problems with ubuntu 8.10.
I hope the AR5212 chip is better supported in future ubuntu releases.

many thanks to all!!

---

### Post by wowiesy on 2009-06-18
> **eks said:**
> 
Then on System/Administration/Hardware Drivers make sure Atheros driver is activated.




How do I do this on a purely command line interface environment (i.e. server install )? I'm trying to set this up on Ubuntu 9.04 SERVER...

---

### Post by sawyannaing on 2009-08-23
Hi all,

I m new to this Ubuntu as well. My Wireless card name is Atheros AR5007G and it was working fine on my last kernal. After update my kernel and then I can't detect my wireless anymore.my current kernel name is kernel 2.6.28-15-generic. Can somebody fix that problem pls...:(

---

