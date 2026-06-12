---
title: "Massive problems with system"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Pikachuu on 2010-09-14
After updating my system today, I restarted my machine as prompted, and once I was in again, I was prompted with updates for my browsers (Firefox and Opera) so I proceeded to update those as well. After that I shut the lid of my laptop, sending it into standby and heading home. Up until this point my system had no problems whatsoever. However as soon as I got home and opened up the lid of my laptop, I was met with trouble.

First of all my laptop failed to recover out of standby, presenting me with a black screen for a long time before grub2 suddenly appeared. Thinking nothing of it I proceeded to enter Ubuntu. The boot took much longer than usual, and then I was presented with a massive string of I/O errors and a single error saying that it was unable to access the "shp10 chip" or something like that. The splash screen still appears after that, and everything still seems fine, except for the crash log icon in the notification tray and the fact that my processor is constantly running at maximum capacity even during moments when it should be idle, with no programs running. I cannot access the crash log at all; after clicking on it and entering my password into the prompt, nothing happens. The icon keeps reappearing in the notifications tray, but it disappears when I mouse over it.

After a while my machine seizes up and starts to move at a snail's pace, which gets so bad that the only way to turn it off is to force a power-off by holding the power button down.

I have no idea where to start searching for the problem or what log to post even. Any help would be greatly appreciated.

---

### Post by Rubi1200 on 2010-09-14
Hi,
you could maybe start by looking for errors in the dmesg log.

```
less /var/log/dmesg
```

Also, are you able to choose other kernels in GRUB? If you only have Ubuntu installed press Shift as the computer boots to bring up the GRUB menu and try booting into an older kernel.

---

### Post by oldfred on 2010-09-14
What size is your swap and how much memory do you have?

Hibernation (suspend-to-disk) The  hibernation feature (suspend-to-disk) writes out the contents of RAM to  the swap partition before turning off the machine. Therefore, your swap  partition should be at least as big as your RAM size. The hibernation  implementation currently used in Ubuntu, swsusp, needs a swap or suspend  partition. It cannot use a swap file on an active file system.

---

### Post by endotherm on 2010-09-14
well, try to do a 
```
sudo apt-get update
``` and see if it works. then try
```
sudo apt-get upgrade
```
hopefully that will complete the install of the updates that got interrupted by the hibernation.

---

### Post by Pikachuu on 2010-09-14
> **oldfred said:**
> What size is your swap and how much memory do you have?

Hibernation (suspend-to-disk) The  hibernation feature (suspend-to-disk) writes out the contents of RAM to  the swap partition before turning off the machine. Therefore, your swap  partition should be at least as big as your RAM size. The hibernation  implementation currently used in Ubuntu, swsusp, needs a swap or suspend  partition. It cannot use a swap file on an active file system.
I'm detected as having 3.5GB RAM but the swap partition assigned to me is 2.2GB only.

I booted into a previous kernel and met with the same I/O errors + cannot reserve MM10 region error (I managed to catch it this time) at boot before the splash screen. The processor speed is still fluctuating erratically. I suspect the error log application has been the one shoving the processor use skyhigh and locking things up, but my processor shouldn't be spiking erratically when all I'm running is compiz with its cube effects, window animations, a widget layer with a few widgets, coupled with Firefox.

I typed the command rubi provided into a terminal and got this monstrosity that I have no idea how to search for errors in as well...

I'm going to go try to get the error log to show up now to see if my system locks up again.

EDIT: Going to update again first as endotherm suggested.

EDIT2: ```
The following packages will be upgraded:
  libsmbclient libwbclient0 samba-common samba-common-bin smbclient winbind

```

EDIT3: After trying to open the crash log, it refused to open again, however the load on my cores ranged from almost 100% to not less than 80%, much better than what I initially got when I posted the thread with the load on my cores refusing to go below even 95%. Going back to my latest kernel, everything seems to be working as before the update except with the pile of errors at boot. I think I've found where the errors are in the log file.

```
[   29.124986] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.124999] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.125008] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   29.125020] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   29.125035] end_request: I/O error, dev sr0, sector 0
[   29.125195] Buffer I/O error on device sr0, logical block 0
[   29.126156] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.126163] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.126170] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   29.126177] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   29.126189] end_request: I/O error, dev sr0, sector 0
[   29.126263] Buffer I/O error on device sr0, logical block 0
[   29.127370] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.127376] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.127383] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   29.127391] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   29.127403] end_request: I/O error, dev sr0, sector 0
[   29.127476] Buffer I/O error on device sr0, logical block 0
[   29.131439] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.131446] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.131452] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   29.131460] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   29.131472] end_request: I/O error, dev sr0, sector 0
[   29.131545] Buffer I/O error on device sr0, logical block 0
[   29.132647] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.132654] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.132660] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   29.132668] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   29.132680] end_request: I/O error, dev sr0, sector 0
[   29.132753] Buffer I/O error on device sr0, logical block 0
[   29.133750] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.133757] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.133764] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range
[   29.133771] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[   29.133783] end_request: I/O error, dev sr0, sector 0
[   29.133856] Buffer I/O error on device sr0, logical block 0
[   29.134860] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   29.134867] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   29.134873] sr 3:0:0:0: [sr0] Add. Sense: Logical block address out of range

```

This one is for the string of I/O errors I was seeing. It repeats over and over again for quite long, which is probably why my boottime was badly affected.

```
[   31.206737] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   31.207084] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   31.207397] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

```

This is the other strange error that I get while booting, which I can't make heads or tails of.

Also, I would like to thank everyone for their valuable input for me to get to this point.

---

