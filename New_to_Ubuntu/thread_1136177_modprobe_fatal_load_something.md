---
title: "modprobe fatal load something"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by alexeyhurricane on 2009-04-24
modprobe: fatal loading or something like that shows up when i start system! i dont know why is that , and it actua;;y happened after i updated to 9

---

### Post by coffeeaddict22 on 2009-04-24
Hi,
modprobe loads all the modules and drivers that run your PC.  So something is likely to not be working as expected... Assuming that you're getting into Linux OK.
If you miss the information on what module isn't loading, it'll be in a system log. Open a terminal, (Applications/Accessories/Terminal), and type in ```
dmesg tail -n20
```
if that doesn't show what module isn't loading, try```
cat /var/log/messages | grep module
```
Paste that back here, but it'll be fairly long so use the icons at the top of the reply box to put it in a code box.
In case you wondered, dmesg is one of the system message files.  tail copies the last -n lines and sends them to a terminal. cat simply finds a file and types it into a terminal.  /var/log/messages is where the Linux kernel writes any messages it sends that you don't need to know about.  | is a pipe; it sends the output from one command to the next.  grep is an awesome trick; it searches line by line in whatever is sent to it, and selects whatever matches the pattern text immediately after.  So what this does is look through the message log for any info about modules being loaded.  It'll still be a long list, but until you know what is not loading, you can't fix it.

---

### Post by Michaelg14 on 2009-04-25
I am getting the same type of message on boot up but nothing is showing up when I try your commands.  The first thing I get is two messages about softresets failing on ata**** something.  I have looked for these messages in the log files with no luck.

My system is also experiencing random freezes.

Edit:  I mean that I can't locate the messages not that nothing shows up.

---

### Post by coffeeaddict22 on 2009-04-25
If it's outputting something to the screen, there should be something in /var/log/ somewhere.  You should see something in dmesg; if it's an ata message you're seeing initially try ```
dmesg | grep ata -C10
``` and see what you find.  Alternatively, just try ```
dmesg
``` and scroll through the whole lot looking for the problem...

---

### Post by Michaelg14 on 2009-04-25
OK That got me something:

 >    2.188288] ata1: softreset failed (device not ready)
[    2.188340] ata1: failed due to HW bug, retry pmp=0
[    2.352296] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.353406] ata1.00: ATA-8: WDC WD7501AALS-00J7B0, 05.00K05, max UDMA/133
[    2.353408] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.355480] ata1.00: configured for UDMA/133


Followed by:

> [    3.188280] ata3: softreset failed (device not ready)
[    3.188327] ata3: failed due to HW bug, retry pmp=0
[    3.352295] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.353421] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB02, max UDMA/100, ATAPI AN
[    3.354940] ata3.00: configured for UDMA/100



What do you make of that?

Those are my hard drive (SATA) and my CDROM also SATA they work fine and this message is not present in 8.10

---

### Post by Michaelg14 on 2009-04-25
Still getting the modprobe fatal messages but can't locate them in any log file.

---

### Post by coffeeaddict22 on 2009-04-25
dmesg outputs the contents of the /proc/kmesg file, so it will be in a log.

  There seems to be a bug in the kernel- [//https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392]("//https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285392") that's probably related.  
You could try the fix (which appears to work for some only), wait for the next kernel, or just grin and bear it.  Reading the bug report, trying the alternate iso might be worth a punt.

---

### Post by Michaelg14 on 2009-04-25
As far as I can tell it is not hurting anything.  I will probably wait for the next kernel or a fix to come along.  Thanks for the info.

---

### Post by alexeyhurricane on 2009-04-26
[HTML]alexey@alexeyhurricane:~$ cat /var/log/messages | grep module
Apr 24 20:04:39 alexeyhurricane kernel: Loaded 59981 symbols from 114 modules.
Apr 24 20:04:39 alexeyhurricane kernel: [    2.265859] brd: module loaded
Apr 24 20:04:39 alexeyhurricane kernel: [    2.266156] loop: module loaded
Apr 24 20:04:39 alexeyhurricane kernel: [   12.996713] wl: module license '' taints kernel.
Apr 24 20:04:39 alexeyhurricane kernel: [   13.730422] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 24 20:16:19 alexeyhurricane kernel: Loaded 59981 symbols from 114 modules.
Apr 24 20:16:19 alexeyhurricane kernel: [    2.269857] brd: module loaded
Apr 24 20:16:19 alexeyhurricane kernel: [    2.270154] loop: module loaded
Apr 24 20:16:19 alexeyhurricane kernel: [   13.148364] wl: module license '' taints kernel.
Apr 24 20:16:19 alexeyhurricane kernel: [   13.872877] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 25 00:02:39 alexeyhurricane kernel: Loaded 59981 symbols from 114 modules.
Apr 25 00:02:39 alexeyhurricane kernel: [    2.265339] brd: module loaded
Apr 25 00:02:39 alexeyhurricane kernel: [    2.265645] loop: module loaded
Apr 25 00:02:39 alexeyhurricane kernel: [   13.141827] wl: module license '' taints kernel.
Apr 25 00:02:39 alexeyhurricane kernel: [   13.888034] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 25 01:59:02 alexeyhurricane kernel: Loaded 59981 symbols from 114 modules.
Apr 25 01:59:02 alexeyhurricane kernel: [    2.265857] brd: module loaded
Apr 25 01:59:02 alexeyhurricane kernel: [    2.266154] loop: module loaded
Apr 25 01:59:02 alexeyhurricane kernel: [   13.246984] wl: module license '' taints kernel.
Apr 25 01:59:02 alexeyhurricane kernel: [   14.039785] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 25 02:18:47 alexeyhurricane kernel: [ 1203.026297] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Apr 25 10:31:22 alexeyhurricane kernel: Loaded 61374 symbols from 123 modules.
Apr 25 10:31:22 alexeyhurricane kernel: [    2.265340] brd: module loaded
Apr 25 10:31:22 alexeyhurricane kernel: [    2.265645] loop: module loaded
Apr 25 10:31:22 alexeyhurricane kernel: [   13.102641] wl: module license '' taints kernel.
Apr 25 10:31:22 alexeyhurricane kernel: [   14.017954] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 25 10:31:22 alexeyhurricane kernel: [   14.167792] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Apr 25 21:46:27 alexeyhurricane kernel: Loaded 61374 symbols from 123 modules.
Apr 25 21:46:27 alexeyhurricane kernel: [    2.265339] brd: module loaded
Apr 25 21:46:27 alexeyhurricane kernel: [    2.265645] loop: module loaded
Apr 25 21:46:27 alexeyhurricane kernel: [   13.447220] wl: module license '' taints kernel.
Apr 25 21:46:27 alexeyhurricane kernel: [   14.429877] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 25 21:46:27 alexeyhurricane kernel: [   14.527111] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Apr 26 15:13:28 alexeyhurricane kernel: Loaded 61374 symbols from 123 modules.
Apr 26 15:13:28 alexeyhurricane kernel: [    2.265338] brd: module loaded
Apr 26 15:13:28 alexeyhurricane kernel: [    2.265642] loop: module loaded
Apr 26 15:13:28 alexeyhurricane kernel: [   13.487289] wl: module license '' taints kernel.
Apr 26 15:13:28 alexeyhurricane kernel: [   14.575205] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
Apr 26 15:13:28 alexeyhurricane kernel: [   14.692241] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[/HTML]

---

### Post by alexeyhurricane on 2009-04-27
i know the problem to modprobe fatal load

i added line to the file [HTML] sudo gedit /etc/modprobe.d/alsa-base

add at the end of the file:

options snd-hda-intel model=laptop

reboot [/HTML] and after this fatal load is happening how to correct it if i delete line sound would go

---

### Post by alexeyhurricane on 2009-04-28
that's funny i didnt do anything , it stopped showing up!

---

