---
title: "Whole PC slows Down..."
date: 2010-11-05
forum: New to Ubuntu
---

### Post by D3SI on 2010-11-05
whole PC slow down when extracting files and by slowing down i mean, for example, when opening firefox it takes longer than usual then again opening bookmarks takes even longer. and as soon as extracting is done everything is normal.

when extracting load goes up to 20-35 (check on Gnome Dock)

System Specs:
Quad Core 2.3
6GB RAM
over 300GB Empty Space in HDD

software for extracting...

its called "rar"  and i use Extract Here option by right clicking.

---

### Post by tkoco on 2010-11-05
> **D3SI said:**
> whole PC slow down when extracting files and by slowing down i mean, for example, when opening firefox it takes longer than usual then again opening bookmarks takes even longer. and as soon as extracting is done everything is normal.

when extracting load goes up to 20-35 (check on Gnome Dock)

System Specs:
Quad Core 2.3
6GB RAM
over 300GB Empty Space in HDD

software for extracting...

its called "rar"  and i use Extract Here option by right clicking.

It sounds like the hard drive (and/or it's interface) has hardware issues. "dmesg" might help. A harddrive which is dying adds lots of error messages.

---

### Post by Unhyper on 2010-11-05
I am having a similar issue. I've been copying data from one hard drive to another, and while that's going on everything just becomes sluggish. Even clicking a button on a webpage takes a couple of seconds to actually happen (delayed response). Thunderbird takes 10 seconds to launch instead of the usual 1-2. Everything lags.

Is this normal for Ubuntu?

---

### Post by tkoco on 2010-11-05
> **Unhyper said:**
> I am having a similar issue. I've been copying data from one hard drive to another, and while that's going on everything just becomes sluggish. Even clicking a button on a webpage takes a couple of seconds to actually happen (delayed response). Thunderbird takes 10 seconds to launch instead of the usual 1-2. Everything lags.

Is this normal for Ubuntu?

The only other time, that I have seen a slowdown in Ubuntu during disk access, is when the data is being written to a USB stick/ USB harddrive and the data size is huge. Webpages are written to a "cache" on the harddrive as they are downloaded. If the harddrive access is slow, then the webpage loading will be slow as well. That goes double for launching a new program.

---

### Post by D3SI on 2010-11-05
> **tkoco said:**
> It sounds like the hard drive (and/or it's interface) has hardware issues. "dmesg" might help. A harddrive which is dying adds lots of error messages.


done that  got line 100 lines output

what am i suppose to be looking for?

---

### Post by tkoco on 2010-11-05
> **D3SI said:**
> done that  got line 100 lines output

what am i suppose to be looking for?

Here is an example where an inserted USB is recognized, but not assigned a device driver. Hence, it is not mountable.

[79806.430133] usb 3-4: new high speed USB device using ehci_hcd and address 2
[79806.584255] usb 3-4: configuration #1 chosen from 1 choice
[79806.584829] scsi11 : SCSI emulation for USB Mass Storage devices
[79806.585016] usb-storage: device found at 2
[79806.585021] usb-storage: waiting for device to settle before scanning
[79811.580371] usb-storage: device scan complete
[79811.581585] scsi 11:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[79811.582561] sd 11:0:0:0: Attached scsi generic sg5 type 0
[79811.582561] sd 11:0:0:0: Embedded Enclosure Device
[79842.130115] usb 3-4: reset high speed USB device using ehci_hcd and address 2
[79873.160124] usb 3-4: reset high speed USB device using ehci_hcd and address 2
[79904.160118] usb 3-4: reset high speed USB device using ehci_hcd and address 2
[79935.160126] usb 3-4: reset high speed USB device using ehci_hcd and address 2
[79935.312537] sd 11:0:0:0: Failed to get diagnostic page 0x50000
[79935.312545] sd 11:0:0:0: Failed to bind enclosure -19

You will see words like "reset" and "Failed" and that is not normal for a harddrive (USB or otherwise)

Does this help?  BTW, the USB drive is going bad 8-)

---

### Post by D3SI on 2010-11-05
i get stuff like this...

> [  728.586077] [UFW BLOCK] IN=eth0 OUT= MAC=xxxxxxxxxxxxxxxxxx SRC=xxxxxxxxxx DST=192.168.x.x LEN=44 TOS=0x00 PREC=0x00 TTL=58 ID=62947 DF PROTO=TCP SPT=56825 DPT=22805 WINDOW=5840 RES=0x00 SYN URGP=0 

which i guess is related to the firewall  :|


am suppose to run that command in terminal right?

---

### Post by tkoco on 2010-11-05
> **D3SI said:**
> i get stuff like this...



which i guess is related to the firewall  :|


am suppose to run that command in terminal right?

Correct on both accounts. Do "dmesg | less"  and the "less" command will allow you to scroll and search the output of dmesg.

---

### Post by D3SI on 2010-11-05
this is the only thing i saw about HDD
> 
[    1.273078] ata1.00: ATA-8: WDC WD6400AAKS-00A7B0, 01.03B01, max UDMA/133
[    1.273081] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.289141] ata1.00: configured for UDMA/133
[    1.289256] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.289372] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.289400] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.289410] sd 0:0:0:0: [sda] Write Protect is off
[    1.289412] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.289429] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


---

### Post by D3SI on 2010-11-06
bump...

---

### Post by tkoco on 2010-11-07
> **D3SI said:**
> this is the only thing i saw about HDD

That looks like the normal messages. What sort of message do you see when you run the "free" command in a terminal?

---

### Post by D3SI on 2010-11-07
>              total       used       free     shared    buffers     cached
Mem:       6191740    6006320     185420          0      68232    5267840
-/+ buffers/cache:     670248    5521492
Swap:     11859960          0   11859960


thts what i get.......

---

### Post by tkoco on 2010-11-07
> **D3SI said:**
> thts what i get.......

That looks ok. Your system is not dipping into the harddrive swap. After reviewing this thread, it looks like the "rar" program must be doing a huge amount of reading/writing to the harddrive. Which in turn slows down other programs which read/write to the HD. You may want to upgrade the harddrive controller & harddrive. I noticed that your system uses the older PATA type harddrive. The newer SATA drives have much faster read/write capabilities. The older PATA hardrives will bog down if there is intense I/O occurring.

---

### Post by D3SI on 2010-11-07
Will do..

Thanks for info. :)

---

