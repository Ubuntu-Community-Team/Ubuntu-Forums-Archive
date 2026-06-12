---
title: "Can't mount sd card in phone after upgrade to 8.10"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Tony Hanna on 2009-03-05
I have an LG Rumor cell phone and up until last week I was able to use a usb cable to transfer pics and music between the phone and my pc by putting the phone into mass storage mode. At that point Ubuntu 8.04 would mount the sd card in the phone automatically and all was fine.

Last week I upgraded to 8.10 and after the upgrade the phone is now detected as a mobile broadband device and I am unable to mount the sd card with the phone in mass storage mode.

If anybody could post a solution or a link to some information to help me get this sorted out, I'd really appreciate it.

Thanks,

Tony

---

### Post by stchman on 2009-03-05
> **Tony Hanna said:**
> I have an LG Rumor cell phone and up until last week I was able to use a usb cable to transfer pics and music between the phone and my pc by putting the phone into mass storage mode. At that point Ubuntu 8.04 would mount the sd card in the phone automatically and all was fine.

Last week I upgraded to 8.10 and after the upgrade the phone is now detected as a mobile broadband device and I am unable to mount the sd card with the phone in mass storage mode.

If anybody could post a solution or a link to some information to help me get this sorted out, I'd really appreciate it.

Thanks,

Tony

Did you upgrade from 8.04 to 8.10 via the upgrade route or do a clean install?

If you went via the upgrade route I believe that is part of your problem.  My LG Lotus works fine on my Intrepid box in mass storage mode.

I always recommend the clean install.  It is faster and less to screw up.

---

### Post by Tony Hanna on 2009-03-05
> **stchman said:**
> Did you upgrade from 8.04 to 8.10 via the upgrade route or do a clean install?

If you went via the upgrade route I believe that is part of your problem.  My LG Lotus works fine on my Intrepid box in mass storage mode.

I always recommend the clean install.  It is faster and less to screw up.

Thanks for the reply! I went via the upgrade route. I'm not sure that's the issue though as I'm having the same problem with my laptop and it was a clean install.

I did find that if I hit escape during boot up and select the next older kernel version in the grub menu, it will mount the sd card with no issues. I guess that's a passable work-around but it's a pain to reboot every time I want to transfer files plus that kernel version throws it into low graphics mode for some reason (maybe the new nvidia driver isn't compatible?). I'm hoping the fact that it works with the older kernel might help pinpoint the problem. Unfortunately, I don't know enough to troubleshoot this.

Thanks,

Tony

---

### Post by llamabr on 2009-03-05
plug it in, and post 

```
lspci
```

and the last couple lines of:

```
dmesg
```

---

### Post by Tony Hanna on 2009-03-06
> **llamabr said:**
> plug it in, and post 

```
lspci
```

and the last couple lines of:

```
dmesg
```

lspci:

```
tony@compaq:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:0f.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)



```

last few lines of dmesg:

```
[24527.639127] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[24527.639149] sd 2:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
[24527.639166] end_request: I/O error, dev sdb, sector 97
[24529.570863] sd 2:0:0:0: [sdb] 1984001 512-byte hardware sectors (1016 MB)
[24529.576810] sd 2:0:0:0: [sdb] Write Protect is off
[24529.576826] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[24529.576832] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[24529.591841] sd 2:0:0:0: [sdb] 1984001 512-byte hardware sectors (1016 MB)
[24529.704056] usb 2-2: reset full speed USB device using uhci_hcd and address 8



```

Thanks for the help!

Tony

---

