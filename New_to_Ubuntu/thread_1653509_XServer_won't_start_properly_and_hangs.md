---
title: "XServer won't start properly and hangs"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2010-12-27
Hi everyone!

I'm using Meerkat on an old desktop machine. Occassionally Xserver hangs but I just used to press the reset button, and after a few bootups it functions normally.

This time, it really won't work anymore.

To describe my problem more clearly, I am dropped onto the Ubuntu desktop, I can see the toolbars and move my mouse. But the theme isn't loaded. On the system tray the sound icon appears muted and the network device shows it's unconnected. And the whole desktop does not respond to my clicks. Pressing Ctrl+Alt+<F1-F7> works so I can exit to gdm using killall5, but logging back in still the same problem.

I'm suspecting it might be a hardware problem, but I have no idea how to test. Any ideas or help would be greatly appreciated.

P.S. I'm typing this on a laptop.

---

### Post by punong_bisyonaryo on 2010-12-27
LSPCI output, copied manually:

Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)

Network controller: RaLink RT2561/RT61 rev B 802.11g

Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by ryadav on 2010-12-27
look at your start-up message log, at the terminal type:

dmesg | less

look for any hardware / software error messages, 
make sure you're using the latest video driver for your card

---

### Post by punong_bisyonaryo on 2010-12-27
> **ryadav said:**
> look at your start-up message log, at the terminal type:

dmesg | less

look for any hardware / software error messages, 
make sure you're using the latest video driver for your card

The last two lines of dmesg output:

EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
EXT4-fs (sda6): re-mounted. Opts: commit=0

I also found:
BAR 0: error updating (0xfde00000 != 0xffff8000)

and

phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset 0x00002100, value=0xffffffff
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset 0x00002100, value=0xffffffff
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset 0x00002100, value=0xffffffff
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset 0x00002100, value=0xffffffff
phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset 0x00002100, value=0xffffffff
phy0 -> rt61pci_wait_bpp_ready: Error - BPP register access failed, aborting.
phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).

My PCI wireless card must be busted?

---

### Post by punong_bisyonaryo on 2010-12-27
@Ryanav

Well, thanks to you, we were able to diagnose that it was probably the RaLink RT61 Wireless card that was causing the hang.

I removed it from the motherboard and now it works again.

Now I just need to figure out if the card is physically broken or there's an issue in Meerkat with my latest software upgrade.

---

