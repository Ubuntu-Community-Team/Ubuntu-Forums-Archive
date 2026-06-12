---
title: "No possible way to use USB as Live disk...  among other things"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by drinkleadsoup on 2010-03-07
I am using an aspire one with ubuntu 9.10.

It all began when I was watching a youtube video.  Firefox and youtube crash my computer.  I try starting the terminal.  I try starting System Monitor.  I try ctrl alt del.  Nothing works, so I give her the ol' shut down by force.  I start her back up.  She makes it through grub, I see the ubuntu splash screen, i'm waitin'...........  black screen again.  Nothing.  Only ctrl alt del works to reboot.

Next, I try my live usb that I have used before to get the system that I am using now running.  Set up my BIOS to read the USB first.  Turn on my computer after inserting USB.  Everything starts normal, but I am only left with black screen and a blinking cursor.  

I tried going into grub.  The only thing I can get to is a recovery mode version of kernel 2.6.31-19 and a couple of others, and it takes me through some errors and an end product of an {initramfs} prompt.  One of the errors is "target filesyetem doesn't have /sbin/init."

I don't know.  Maybe I am dumb.


If anyone out there is smart enough to help me defeat this problem, you will soon benefit from many gracious wishes.

---

### Post by drinkleadsoup on 2010-03-07
Can anyone think of a way to help?

---

### Post by GameOverDood on 2010-03-07
If you don't mind losing your data then I think you should try running a program called DBAN, either through a CD via external CD drive, or if you can find a way to make a bootable USB out of it. DBAN will completely "reformat" your hard drive allowing you to reinstall Ubuntu. This is, of course, assuming that your issue is software-based.

If it's hardware, such as maybe the hard drive being defective, then that's probably something you should check out too if you can. There's a neat diagnostic tool out there called Hiren's Boot CD, but again, you'll need an external CD drive for it or somehow be able to make a bootable USB for it.

---

### Post by drinkleadsoup on 2010-03-07
Update...

I got the live USB to work.  Getting closer.

Next on the agenda:  Filesystem error.

I get this box when I click to view the file system:

Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


or this one:

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.



I am not sure if this is worse or better.  The file system is there.  I just need to be able to mount it.

Again, any help will be so appreciated.

---

### Post by mikewhatever on 2010-03-07
Sounds like a file system or hdd error. You might want to look in /var/log/dmesg for more.

---

### Post by drinkleadsoup on 2010-03-08
This is what I got from DMESG, and it is only the ending:



[ 2879.115318] ata1.00: status: { DRDY ERR }
[ 2879.115329] ata1.00: error: { UNC }
[ 2879.129418] ata1.00: configured for UDMA/133
[ 2879.129459] ata1: EH complete
[ 2882.097548] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2882.097566] ata1.00: BMDMA stat 0x4
[ 2882.097600] ata1.00: cmd c8/00:00:97:08:1d/00:00:00:00:00/e9 tag 0 dma 131072 in
[ 2882.097606]          res 51/40:00:ae:08:1d/00:00:00:00:00/e9 Emask 0x9 (media error)
[ 2882.097621] ata1.00: status: { DRDY ERR }
[ 2882.097631] ata1.00: error: { UNC }
[ 2882.121773] ata1.00: configured for UDMA/133
[ 2882.121814] ata1: EH complete
[ 2885.087833] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2885.087858] ata1.00: BMDMA stat 0x4
[ 2885.087903] ata1.00: cmd c8/00:00:97:08:1d/00:00:00:00:00/e9 tag 0 dma 131072 in
[ 2885.087913]          res 51/40:00:ae:08:1d/00:00:00:00:00/e9 Emask 0x9 (media error)
[ 2885.087934] ata1.00: status: { DRDY ERR }
[ 2885.087949] ata1.00: error: { UNC }
[ 2885.105018] ata1.00: configured for UDMA/133
[ 2885.105061] ata1: EH complete
[ 2888.068144] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2888.068163] ata1.00: BMDMA stat 0x4
[ 2888.068197] ata1.00: cmd c8/00:00:97:08:1d/00:00:00:00:00/e9 tag 0 dma 131072 in
[ 2888.068203]          res 51/40:00:ae:08:1d/00:00:00:00:00/e9 Emask 0x9 (media error)
[ 2888.068218] ata1.00: status: { DRDY ERR }
[ 2888.068228] ata1.00: error: { UNC }
[ 2888.093313] ata1.00: configured for UDMA/133
[ 2888.093381] sd 0:0:0:0: [sda] Unhandled sense code
[ 2888.093392] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2888.093407] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2888.093427] Descriptor sense data with sense descriptors (in hex):
[ 2888.093437]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2888.093480]         09 1d 08 ae 
[ 2888.093498] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2888.093520] end_request: I/O error, dev sda, sector 152897710
[ 2888.093589] ata1: EH complete
[ 2888.093702] JBD: Failed to read block at offset 7938
[ 2888.093730] JBD: recovery failed
[ 2888.093740] EXT3-fs: error loading journal.

---

### Post by mikechant on 2010-03-08
Looks like the forced shutdown has caused disc corruption on your root filesystem.

Have you tried running a file system check from the live USB?

```
sudo e2fsck -n -f -v /dev/sdxx
```

will do a dummy run and report what it finds, if it finds something fixable remove the -n if you want fsck to attempt to fix it, or post the output here if you want it looking at first.

sdxx should be replaced with the root partition name (e.g. sda1)

---

### Post by drinkleadsoup on 2010-03-08
Fsck did it.  Yeahhh.  

For the USB drive, I dunno.  I think UNetBootin may have a problem with the aspire one.  I used the linux live usb creator and did not have any problems.

From there, I ran fsck on the hdd, and everything is back to normal.

I gotta get an external hard drive.

Thanks for your help everyone.

---

### Post by drinkleadsoup on 2010-03-08
how do I mark it as solved?

---

### Post by mikechant on 2010-03-09
> how do I mark it as solved? 

There's a 'thread tools' link near the top right of the thread, click on that and one of the options is 'mark as solved'.

---

