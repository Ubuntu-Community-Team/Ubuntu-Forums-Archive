---
title: "Blinking caps lock freeze"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by 416inversed on 2010-02-09
Twice now in two days, my dual-boot (karmic & xp) Acer Aspire One D250 has randomly frozen to a black screen with only an underscore & mouse arrow visible, and the caps lock indicator blinking.

A quick google search turns up that this is "Kernel Panic," but what does that actually mean?

I'm assuming it's probably being cause by my recent kernel upgrade to 2.6.31-19-generic.

So how to I go about resolving this or should I revert to 2.6.31-17?

---

### Post by x33a on 2010-02-09
It is indeed a kernel panic.

You should first see if the previous kernel works. if it does, then you can stick with it for a while (until more updates come). 

otherwise if you have time to spare, then you should try fixing the problem.

---

### Post by 416inversed on 2010-02-10
Yeah, I haven't had any issues since booting back into 2.6.31-17, so I guess I'll make that my default kernel until the next one comes around.

So am I correct in assuming that "Kernel Panic" is basically the Linux equivalent of the infamous "Blue Screen of Death...?" Should I phrase it "The Blinking Caps-lock of Panic?"

Just out of curiosity, how would I go about trying to debug 2.6.31-19 on my netbook? Is it even a bug? If so, should I report it to Launchpad? How would I go about doing that?

---

### Post by x33a on 2010-02-10
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by DarkNovaNick on 2010-02-11
My computer may have been hit by the same problem. Yesterday my computer went down 3 times with kernel 2.6.31-19-generic. I was only at the console for one of those times, but the num lock light started flashing and then the machine rebooted. I ran memtest overnight and it didn't find any problems. This is a machine that has been up 24/7 for almost a year, except for occasional reboots for things like installing kernels, and has never rebooted in this fashion before. 3 in one day seems kind of strange. I should note that it was doing quite a bit of disk I/O at the time, but heavy disk I/O is common for this machine. I went back to 2.6.31-17-generic this morning.

---

### Post by oyvinst on 2010-02-13
I seem to having freezing problems in 2.6.31-19 and 2.6.31-20 on a 64bit Intel quad-core machine (Ubuntu 9.10). Strange and complete system freeze just 1 minute after logging in. Checked temperatures, etc, and find nothing wrong. Machine has been running stable for a long time.. I think I need to go back to an older kernel.

---

### Post by oyvinst on 2010-02-13
> **oyvinst said:**
> I seem to having freezing problems in 2.6.31-19 and 2.6.31-20 on a 64bit Intel quad-core machine (Ubuntu 9.10). Strange and complete system freeze just 1 minute after logging in. Checked temperatures, etc, and find nothing wrong. Machine has been running stable for a long time.. I think I need to go back to an older kernel.

Same freeze for me with 2.6.31-17, so not the kernel in my case. Probably just bad hardware.

---

### Post by emeraldgirl08 on 2010-02-14
I'm also having problems in my 2.6.31-19 Kernel also. I turned on my laptop this morning and as soon as the desktop environment loaded it froze. I noticed the Caps lock symbol was flashing. I knew this was a "kernel panic" but did not know what to do. 

I just got back on to check mail and decided to try a different kernel. I am using 2.6.31.17 and it is not locking up. 

Hope this gets fixed with the next update!

---

### Post by sdpkelkar on 2010-03-05
Likewise. I'm using a Dell inspiron 1525. In my case however, the problem arose when I changed my wireless router. I read in some other thread that  installing the backports ( sudo apt-get install linux-backports-modules-intrepid ) does the trick. Has anyone tried this in Ubuntu 9.10?

---

### Post by CodeRage on 2010-03-06
I started having this issue on a new Toshiba X505-Q870 using Ubuntu 9.10 Karmic Koala (x64) with kernel version 2.6.31-20.57. I have resorted to using kernel version 2.6.31-14.48 which has thus far proven to be pretty stable. 

To give a little more information on my setup: 

I am in a dual boot situation with Windows 7. This machine came with 3 partitions out of the box. Windows 7, and 2 Recovery/Primary partitions, which I believe hold proprietary recovery type stuff that would be a superbad idea to wipe. With that, I have set up Ubuntu 9.10 without a swap partition, and instead set up a swap file within my Ubuntu 9.10 partition.

During the course of chasing down nVidia drivers for my GeForce 360M, I have settled on driver 195.36.08, despite warnings of possible fan control issues. 

My two biggest battles have been with regard to drivers for wireless connectivity via a Realtek 8172 wifi card, and hibernation failing. The wifi thus far works via the 8192se driver, but the connectivity value reported by the network-manager fluctuates a lot, sometimes to the point of where my (chromium) browser responds to clicked links with "resolving host..." for a couple long minutes or so. The hibernation issue I believe is related specifically to the swap file, since research indicates that hibernation looks for swap partitions rather than files within a non-swap partition.

Beyond my battles, everything else (including suspending rather than hibernating) has worked out of the box. Even the slick touch-panel on the left of the machine works with regard to volume controls, which is all i've been able to test thus far. 

So if I were to get blindsided with more kernel panics from this point forward, i'll be looking more into the realtek driver and the swap file thing for my particular case. All my research has basically pointed to these two things really.

I hope others find what helps them with their particular kernel panics without having to go through too much hell and back.

CodeRage

---

### Post by CodeRage on 2010-03-06
Well well! I hit a kernel panic while in 2.6.31-14.48. I specifically recall doing something with network manager via the icon in the top panel. So I am guessing this matter is centered around either the realtek driver I have, or the network manager itself. I'll plow on with reseaching both as the day goes on. 

CodeRage

---

### Post by jaminbw on 2010-03-07
I have this same thing on Acer Aspire one running ubuntu 9.10 seems to happen when on wireless and just started as of the latest kernal update. I have had this happen 2 times seams like I was doing something with network manager icon both times.

---

### Post by CodeRage on 2010-03-08
> **jaminbw said:**
> I have this same thing on Acer Aspire one running ubuntu 9.10 seems to happen when on wireless and just started as of the latest kernal update. I have had this happen 2 times seams like I was doing something with network manager icon both times.

Yeah I just figured out the realtek 8192se driver used on an 8172 card was causing the kernel panics, which occur shortly after doing something via the network manager icon. I plucked this from my /var/log/syslog.1:

```

Mar  7 08:08:00 coderage kernel: [  428.332522] DMA: Out of SW-IOMMU space for 9100 bytes at device 0000:0a:00.0
Mar  7 08:08:00 coderage kernel: [  428.333567] DMA: Out of SW-IOMMU space for 9100 bytes at device 0000:0a:00.0
Mar  7 08:08:00 coderage kernel: [  428.434819] DMA: Out of SW-IOMMU space for 9100 bytes at device 0000:0a:00.0
Mar  7 08:08:00 coderage kernel: [  428.454512] ====================>haha:IPSEnter()
Mar  7 08:08:00 coderage kernel: [  428.454517] =========>NicIFDisableNIC()
Mar  7 08:08:00 coderage kernel: [  428.454525] PHY_SetRtl8192seRfHalt save BB/RF
Mar  7 08:08:01 coderage NetworkManager: <debug> [1267978081.007095] periodic_update(): Roamed from BSSID 00:18:F8:D1:74:EE (CodeRage) to (none) ((none))
Mar  7 08:09:43 coderage kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Mar  7 08:09:43 coderage rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="908" x-info="http://www.rsyslog.com"] (re)start
Mar  7 08:09:43 coderage rsyslogd: rsyslogd's groupid changed to 102
Mar  7 08:09:43 coderage rsyslogd: rsyslogd's userid changed to 101
Mar  7 08:09:43 coderage rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar  7 08:09:43 coderage avahi-daemon[954]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Mar  7 08:09:43 coderage avahi-daemon[954]: Successfully dropped root privileges.
Mar  7 08:09:43 coderage kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar  7 08:09:43 coderage avahi-daemon[954]: avahi-daemon 0.6.25 starting up.
Mar  7 08:09:43 coderage kernel: [    0.000000] Initializing cgroup subsys cpu
Mar  7 08:09:43 coderage NetworkManager: <info>  starting...
Mar  7 08:09:43 coderage kernel: [    0.000000] Linux version 2.6.31-20-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 (Ubuntu 2.6.31-20.57-generic)

```

The out of SW-IOMMU space line repeated (exaggerating a bit) approximately a trillion times prior to what I posted, and then the rest of the snippit continues on the hard-reboot process. 

At the same time as this issue, I'm also wrestling with drivers that properly suport an nVidia GeForce GTS 360M. The latest drivers have been pulled due to possible fan control issues that can lead to fried cards. Beyond that, the only other matter for me to iron out is having hibernate mesh well with using a manually created swap file stored within the active ubuntu partition, rather than a partition of its own as I am unable to do that on this machine.

---

### Post by dianemeeks on 2010-04-01
I am having the same problem, and using an older kernel does not help.  However, I don't think it's hardware since I can run fine from the Live CD.  I also installed a clean Karmic on another partition, and it is working fine.  Any suggestions?

---

