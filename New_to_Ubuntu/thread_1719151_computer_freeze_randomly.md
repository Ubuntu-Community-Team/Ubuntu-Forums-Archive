---
title: "computer freeze randomly"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by acazosa on 2011-04-01
Hello i m using ubuntu 10.10 on dell laptop studio. I m using an intel i7 processor and an ati graphic board. It happend very often that the computer freeze totaly for apparently no reason. It seems that the problem it s not related to flash or compiz. I tried also to reinstall the driver of the graphic board and to disabled the hyperthreading of the processor but i still have this problem. Any guess would be appraciate. Thank you in advance

---

### Post by sanguinoso on 2011-04-01
Next time it happens post the results of this command ```
tail -n 100 /var/log/messages
```. All it does is to print the last 100 messages from the system log so we can see if any error messages were posted to help track down this error.

---

### Post by acazosa on 2011-04-02
OK in fact i did in the past but in the log file for what i could understand there was no information about any error maybe because the sistem freeze totaly and has no time to write stuff in the kernel log. What do you think? can be an answer?

---

### Post by leviathan8 on 2011-04-02
Did you set your visual effects to none in Appearance preferences?

---

### Post by acazosa on 2011-04-02
It s set to normal. In fact i was thinking that the freezing was related to compiz  so  i  remove  it. When i did half of the screen was black, so i reinstall it. Now if i set the apparence to none half of my screen becomes black again i really don t know why.

---

### Post by acazosa on 2011-04-03
Apr  3 12:16:59 Hal9000 kernel: [ 7216.010555] firewire_core: skipped bus generations, destroying all nodes
Apr  3 12:16:59 Hal9000 kernel: [ 7216.074686] PM: resume of drv:wl dev:0000:04:00.0 complete after 120.351 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.080220] [fglrx] Resuming fglrx in kernel completed.
Apr  3 12:16:59 Hal9000 kernel: [ 7216.081195] [fglrx] IRQ 55 Enabled
Apr  3 12:16:59 Hal9000 kernel: [ 7216.081200] PM: resume of drv:fglrx_pci dev:0000:02:00.0 complete after 126.908 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.158259] PM: resume of drv:usb dev:1-1 complete after 202.278 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.158408] PM: resume of drv:hub dev:1-1:1.0 complete after 202.415 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.158434] PM: resume of drv: dev:ep_81 complete after 141.159 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.238569] usb 1-1.4: reset high speed USB device using ehci_hcd and address 3
Apr  3 12:16:59 Hal9000 kernel: [ 7216.318330] ata5: SATA link down (SStatus 0 SControl 300)
Apr  3 12:16:59 Hal9000 kernel: [ 7216.318334] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  3 12:16:59 Hal9000 kernel: [ 7216.330006] ata2.00: configured for UDMA/100
Apr  3 12:16:59 Hal9000 kernel: [ 7216.464294] PM: resume of drv:usb dev:1-1.4 complete after 508.438 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.464345] PM: resume of drv:uvcvideo dev:1-1.4:1.0 complete after 508.488 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.464388] PM: resume of drv:uvcvideo dev:1-1.4:1.1 complete after 508.512 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7216.508680] firewire_core: rediscovered device fw0
Apr  3 12:16:59 Hal9000 kernel: [ 7217.916663] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 12:16:59 Hal9000 kernel: [ 7217.920519] ata1.00: configured for UDMA/133
Apr  3 12:16:59 Hal9000 kernel: [ 7218.192753] PM: resume of drv:sd dev:0:0:0:0 complete after 2238.537 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7218.192849] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2036.234 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7218.192858] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2238.606 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7218.210087] PM: resume of devices complete after 2258.050 msecs
Apr  3 12:16:59 Hal9000 kernel: [ 7218.210205] PM: resume devices took 2.260 seconds
Apr  3 12:16:59 Hal9000 kernel: [ 7218.210241] Restarting tasks ... done.
Apr  3 12:17:00 Hal9000 kernel: [ 7218.617357] r8169 0000:09:00.0: eth0: link down
Apr  3 12:17:00 Hal9000 kernel: [ 7218.617774] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  3 12:17:01 Hal9000 kernel: [ 7220.418773] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
Apr  3 12:25:14 Hal9000 kernel: [ 7711.805283] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600


That s the var/log

---

### Post by Naggobot on 2011-04-04
Are you sure that this "tail" is taken after you suffered a system freeze?

I admit that above cryptic messages do not tell much to me but I would hazard a guess that the above log tells that your system has just come out of suspend?

I also have been suffering from random temporary freezes and this thread prompted me to start a [new one for my problem]("http://ubuntuforums.org/showthread.php?t=1720375"). In my case there was a clear error in /var/log/messages. 

So try outputting the "tail" just after freeze to see if it changes and prompts for some sort of error.

---

### Post by acazosa on 2011-04-04
When the sistem freeze the keyboard it s totaly block. I can t do anything just shout down the pc with the bottom shot down. Anyway when i reboot thats the log/messages. I cut all the boot information

---

### Post by sanguinoso on 2011-04-05
Are there any strange errors present? I agree with naggobot in that it seems fairly normal.

---

### Post by sanguinoso on 2011-04-05
> **acazosa said:**
> It s set to normal. In fact i was thinking that the freezing was related to compiz  so  i  remove  it. When i did half of the screen was black, so i reinstall it. Now if i set the apparence to none half of my screen becomes black again i really don t know why. What kind of video card do you have? And what drivers are you using for it?

---

### Post by Jetro on 2011-04-05
I'm just wondering how Ubuntu freezes.

I get random freezes sometimes (Dell i9400), where all the windows turn grey and the mouse starts to "lag", where all I can do is hold down the Power button. I don't mean to hijack your topic, I just want to know exactly *how* your system freezes.

---

### Post by mörgæs on 2011-04-05
Here is some good general information on freezing. It says Kubuntu, but it applies to Ubuntu as well.

[https://wiki.kubuntu.org/X/Troubleshooting/Freeze](https://wiki.kubuntu.org/X/Troubleshooting/Freeze)

---

