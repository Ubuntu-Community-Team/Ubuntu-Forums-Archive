---
title: "3Com Vortex/Boomeran (3c59x) &quot;dies&quot; after a few hours."
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by wisekki on 2007-11-30
Hello,

I'm using 3Com Vortex/Boomerang nic and for some reason after booting or rebooting
the computer, 3Com stops working after a while. (About 1h - 6h).

This is what it says on the logs:

[23833.415671] NETDEV WATCHDOG: eth2: transmit timed out
[23833.415680] eth2: transmit timed out, tx_status 00 status e601.
[23833.415688]   diagnostics: net 0cfa media 8880 dma 0000003a fifo 0000
[23833.415693] eth2: Interrupt posted but not delivered -- IRQ blocked by another device?
[23833.415729]   Flags; bus-master 1, dirty 48(0) current 48(0)
[23833.415733]   Transmit list 00000000 vs. ffff81008cfd7200.
[23833.415737]   0: @ffff81008cfd7200  length 8000006e status 0c01006e
[23833.415741]   1: @ffff81008cfd72a0  length 8000006e status 0c01006e
[23833.415744]   2: @ffff81008cfd7340  length 8000006e status 0c01006e
[23833.415747]   3: @ffff81008cfd73e0  length 8000006e status 0c01006e
[23833.415750]   4: @ffff81008cfd7480  length 800000e7 status 0c0100e7
[23833.415754]   5: @ffff81008cfd7520  length 800000e7 status 0c0100e7
[23833.415759]   6: @ffff81008cfd75c0  length 800000e7 status 0c0100e7
[23833.415763]   7: @ffff81008cfd7660  length 800000e7 status 0c0100e7
[23833.415766]   8: @ffff81008cfd7700  length 800000e7 status 0c0100e7
[23833.415769]   9: @ffff81008cfd77a0  length 8000006e status 0c01006e
[23833.415772]   10: @ffff81008cfd7840  length 8000006e status 0c01006e
[23833.415776]   11: @ffff81008cfd78e0  length 8000006e status 0c01006e
[23833.415779]   12: @ffff81008cfd7980  length 8000006e status 0c01006e
[23833.415782]   13: @ffff81008cfd7a20  length 8000006e status 0c01006e
[23833.415785]   14: @ffff81008cfd7ac0  length 8000006e status 8c01006e
[23833.415788]   15: @ffff81008cfd7b60  length 8000006e status 8c01006e
[23833.415793] eth2: Resetting the Tx ring pointer.

this is the output of my irq's:

           CPU0       CPU1       
  0:    6009213          0   IO-APIC-edge      timer
  1:      30473          0   IO-APIC-edge      i8042
  8:          0          0   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:     559662          0   IO-APIC-edge      i8042
 16:    2763425          0   IO-APIC-fasteoi   nvidia
 17:    9520636          0   IO-APIC-fasteoi   uhci_hcd:usb2, libata, eth0
 18:     853567          0   IO-APIC-fasteoi   uhci_hcd:usb3, libata
 19:     426195          0   IO-APIC-fasteoi   uhci_hcd:usb4, libata, HDA Intel
 20:    1502100          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 22:     232768          0   IO-APIC-fasteoi   eth2
NMI:          0          0 
LOC:    5988827    6007580 
ERR:          0

vortex-tool with -aem says:

Index #1: Found a 3c920 Series NIC adapter at 0xb800.
 Station address 00:04:76:1b:c2:15.
  Receive mode is 0x07: Normal unicast and all multicast.
The Vortex chip may be active, so FIFO registers will not be read.
To see all register values use the '-f' flag.
Initial window 7, registers values by window:
  Window 0: 0000 0000 d93f 0000 e3e3 00bf ffff 0401.
  Window 1: FIFO FIFO 0700 003c 0000 007f 0000 2401.
  Window 2: 0400 1b76 15c2 0000 0000 0000 0052 4401.
  Window 3: 0000 0180 05ee 0020 000a 01c0 0800 6401.
  Window 4: 0000 0000 0000 0cfa 0001 8880 0000 8401.
  Window 5: 1ffc 0000 0000 0600 0807 06ce 06c6 a401.
  Window 6: 0000 0000 0000 0000 0000 0000 0000 c401.
  Window 7: 0000 0000 8100 0000 0000 0000 0000 e401.
Vortex chip registers at 0xb800
  0xB810: **FIFO** 00000000 00000000 *STATUS*
  0xB820: 00000028 00000000 00080000 00000004
  0xB830: 0000a000 0b07f4f9 8cfd7150 00080004
  0xB840: 00a9e599 00000000 000000b7 00000000
  0xB850: 00000000 00000000 00000000 00000000
  0xB860: 00000000 00000000 00000000 00000000
  0xB870: 00009040 00000000 00200000 00000000
  DMA control register is 00000028.
   Tx list starts at 00000000.
   Tx FIFO thresholds: min. burst 256 bytes, priority with 128 bytes to empty.
   Rx FIFO thresholds: min. burst 256 bytes, priority with 128 bytes to full.
   Poll period Tx 00 ns.,  Rx 0 ns.
   Maximum burst recorded Tx 0,  Rx 32.
 Indication enable is 06c6, interrupt enable is 06ce.
 Interrupt sources are pending.
   Interrupt latch indication.
   Upload Complete indication.
 Transceiver/media interfaces available:  100baseTx 10baseT.
Transceiver type in use:  Autonegotiate.
 MAC settings: full-duplex.
Maximum packet size is 1518.
 Station address set to 00:04:76:1b:c2:15.
 Configuration options 0052.
Saved EEPROM settings of a 3Com Vortex/Boomerang:
 3Com Node Address 00:04:76:1B:C2:15 (used as a unique ID only).
 OEM Station address 00:04:76:1B:C2:15 (used as the ethernet address).
  Device ID 9200,  Manufacturer ID 6d50.
  Manufacture date (MM/DD/YYYY) 1/27/2001, division H, product MW.
  A BIOS ROM of size 0Kx8 is expected.
 Transceiver selection: Autonegotiate.
   Options: negotiated duplex, link beat required.
   PCI bus requested settings --  minimum grant 10, maximum latency 10 (250ns units).
 PCI Subsystem IDs: Vendor 10b7 Device 1000.
 100baseTx 10baseT.
  Vortex format checksum is incorrect (4e vs. 10b7).
  Cyclone format checksum is incorrect (0xde vs. 0xd8).
  Hurricane format checksum is incorrect (0xf7 vs. 0xd8).
 MII PHY found at address 24, status 782d.
 MII PHY 0 at #24 transceiver registers:
   1000 782d 0040 6176 05e1 cde1 000b 0000
   0000 0000 0000 0000 0000 0000 0000 0000
   1000 0300 0000 0000 0000 0175 0200 0000
   003b 8d3e 0f00 ff40 002b 0000 80a0 000b

I've tried mii-tool, removing/reloading 3c59x module but nothing works except rebooting.
This is my main server so I really hate to boot it every other hour :)

Sorry for the long message, but I really want to get it working. I've been fighting with it
for a week now and google doesn't seem to know this problem at all.

Oh yea.. and this problem started when I installed 7.10 :)
Everything worked perfecty with 7.04... but I don't want to downgrade...

I have 5 3Com nics and they all do the same...


Cheers, 

 Antti

---

### Post by wisekki on 2007-12-01
Could this be an ACPI problem? I'm considering compiling the kernel from the scratch because this is getting really annoying.. 
I have to reboot my computer 10 times a day ](*,)

---

### Post by wisekki on 2007-12-02
Well it seems that the solution for this problem is beyond me so I bought a new nic.
Hopefully that one works better than crappy 3Com :)
Let me know if you have this and it works with Ubuntu 7.10
 - D-Link DGE-528T 1Gbit NIC

Cheers, 

 Antti

---

### Post by Kajaste on 2008-01-14
This is (and has been for years) an APIC problem and kernel parameter noapic can be used as a workaround.
AFAIK this does not cause a performance hit at least not on single core single processor machines.

To do this open up /boot/grub/menu.lst in your favorite editor (as root or with sudo)
sudo nano -w /boot/grub/menu.lst

then find a line that looks something like this
# kopt=root=UUID=62aea229-c61a-479b-9546-86c28fe27ff5 ro

now add the parameter noapic, the line should look something like this
# kopt=root=UUID=62aea229-c61a-479b-9546-86c28fe27ff5 ro noapic
(no, you are not supposed to "uncomment" the line)

then run update-grub to update the boot menu entries
sudo update-grub

then save your work and reboot to make the kernel parameter take effect

check that APIC interrupts are not used
grep APIC /proc/interrupts
If it prints nothing, then things are fine.

In case someone is interested, I'm running 64-bit Gutsy on an AMD64 CPU, nForce3 MB and the NIC is a 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24). This bug(?) is very annoying so it would be cool if someone could fix it. I googled around for a while and it seems no one has a solution, not even the driver developer.

---

### Post by joesmith1234 on 2008-02-01
> **Kajaste said:**
> This is (and has been for years) an APIC problem and kernel parameter noapic can be used as a workaround.
AFAIK this does not cause a performance hit at least not on single core single processor machines.

To do this open up /boot/grub/menu.lst in your favorite editor (as root or with sudo)
sudo nano -w /boot/grub/menu.lst

then find a line that looks something like this
# kopt=root=UUID=62aea229-c61a-479b-9546-86c28fe27ff5 ro

now add the parameter noapic, the line should look something like this
# kopt=root=UUID=62aea229-c61a-479b-9546-86c28fe27ff5 ro noapic
(no, you are not supposed to "uncomment" the line)

then run update-grub to update the boot menu entries
sudo update-grub

then save your work and reboot to make the kernel parameter take effect

check that APIC interrupts are not used
grep APIC /proc/interrupts
If it prints nothing, then things are fine.

In case someone is interested, I'm running 64-bit Gutsy on an AMD64 CPU, nForce3 MB and the NIC is a 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24). This bug(?) is very annoying so it would be cool if someone could fix it. I googled around for a while and it seems no one has a solution, not even the driver developer.

I was having this same problem... whenever I tried to copy a large file or a large amount of data, the network stuff would stop working and the copy would fail.  This also happened for torrents...  the torrent would download but eventually the network services would just go away.

Anyways, I added the line to the menu.lst file, grub update, and reboot, and now everything is working fine.  I also have the 3c905B card, but previously was having the same issue on a different 3com card (older).

Espoolainen voittaa aina!  Turku on perseestä.

---

