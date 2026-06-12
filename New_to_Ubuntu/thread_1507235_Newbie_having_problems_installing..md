---
title: "Newbie having problems installing."
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Blarki on 2010-06-11
Firstly, you should know that this is the first time I've ever attempted to use anything other than Windows, so bear with me if I say anything really stupid.

My old computer died on me a few months ago, and I'm trying to get it going again with the latest Ubuntu. It used to have Windows XP on it, but when I booted it up it had pretty much imploded - The hard drive isn't even formatted |:

Anyway, I downloaded and burnt the .iso to a disc, and put it in my old computer .. Got it to the install screen, and tried clicking 'Try Ubuntu without installing' .. The screen goes black, and all I can see is a blinking cursor at the top left until I reboot. The same thing happens if I click 'Install Ubuntu'. 

I tried doing this:

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

.. But none of them worked.

After looking around for a bit, and only finding solutions that are basically variations on "backspace 'quiet splash' and type _________", none of which are working for me .. I figured I should just ask for some direct help.

Thanks in advance for any help.

- Brad

---

### Post by baddnady23 on 2010-06-11
How long did you wait before rebooting?  When booting off the live CD, it can take several minutes for it to fully load up... Especially on an older machine.

---

### Post by rcayea on 2010-06-11
I agree with waiting. I think I have a fairly speedy machine and sometimes it can take at least three minutes to boot off a cd.

Wait about 5-10 minutes, seriously.

---

### Post by Blarki on 2010-06-11
I cannot even begin to fathom that all it took was a little patience. 

Thanks for all of your help - I've begun the install.

- Humiliated.

---

### Post by takisan on 2010-06-11
Yes, I hate to promote redundancy, but yes, waiting is your best option. I managed to successfully booted and installed Lucid on a computer that's probably designed for NT4.0 Server, so you should be able to boot it on an XP.

---

### Post by Blarki on 2010-06-11
Uh, okay .. So I finished the install without a hitch .. It asked me to restart my computer, so I clicked OK.

When the computer rebooted, it come up with the following error:

Gave up waiting for root device. Common problems:
- Root Args (cat /proc/cmdline)
- check rootdelay = (did the system wait long enough?)
- check root= (did the system wait for the right device??)
- Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/167aa185-9a1c-490f-8887-310c18a6b21b does not exist. Dr
opping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ububtu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.


Does anyone know what's going on? |:

- Brad

---

### Post by -kg- on 2010-06-11
> **Blarki said:**
> Uh, okay .. So I finished the install without a hitch .. It asked me to restart my computer, so I clicked OK.

When the computer rebooted, it come up with the following error:

Gave up waiting for root device. Common problems:
- Root Args (cat /proc/cmdline)
- check rootdelay = (did the system wait long enough?)
- check root= (did the system wait for the right device??)
- Missing modules (cat /proc/modules; Is /dev)
[COLOR="Red"]ALERT! /dev/disk/by-uuid/167aa185-9a1c-490f-8887-310c18a6b21b does not exist. Dr
opping to a shell![/COLOR]

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ububtu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.


Does anyone know what's going on? |:

- Brad

It sounds like you might have a bad hard drive.  Boot back to the Live CD, launch GPartEd (System/Administration/GPartEd) and check whether the hard drive has the requisite partitions on it.  It should have an ext4 "/" (root) partition and a swap partition, unless you created more manually.

Alternatively (and probably more easily done) you could launch the terminal (Applications/Accessories/Terminal) and issue the command:

```
sudo fdisk -l
```

and post the results here in the thread.

A link to a good tutorial on partitioning operations is in my signature block.

---

### Post by Blarki on 2010-06-11
Okay, so I went with the alternative, and this is what came up:

Disk /dev/sda: 80.0 GB 80026361856 Bytes
255 heads, 63 sectors/tracks, 9729 cylinders
Units = cylinders of 16065 = 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Device boot ............          Start ..........          End ..........          Blocks ...............               Id ..........          System              
/dev/sda1 ..............             1               ................ 9568 .........         76848128 .......         83          ........... Linux
/dev/sda2              .............. 9568 ..........          9730..........         1300481...........           5 ............           Extended
/dev/sda5 ..............              9568 ..........          9730 .........         1300480 .........           82 ..........          Linux swap / Solaris

Thanks so much.

---

### Post by -kg- on 2010-06-11
This kind of makes no sense to me.  The partitions obviously exist, and the installer created them and (ostensibly) installed into them.  What the GRUB message says to me is that the root partition (with the rest of GRUB in the /boot directory) is not being detected by the partition UUID number that the installer originally put into the MBR resident GRUB segment.  (I'm sure you just *completely* know what I'm talking about here, but someone else might! :p )

It may still be a hard drive problem.  ***_Something_*** caused your XP installation to give up the ghost! Perhaps the hard drive is getting ready to go and will work sometimes, and not work others.  How long has it been in operation?

Did you try and boot into the installation more than once?  It might have been a little "blip" in operation.  Sometimes, if you try several times, the boot-up will finally progress as normal.

Other than that, I'm not quite sure what to tell you.  Hopefully someone with more knowledge than I will come along and be able to help you further.

---

### Post by ktp on 2010-06-12
> **Blarki said:**
> Uh, okay .. So I finished the install without a hitch .. It asked me to restart my computer, so I clicked OK.

When the computer rebooted, it come up with the following error:

Gave up waiting for root device. Common problems:
- Root Args (cat /proc/cmdline)
- check rootdelay = (did the system wait long enough?)
- check root= (did the system wait for the right device??)
- Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/167aa185-9a1c-490f-8887-310c18a6b21b does not exist. Dr
opping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ububtu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.


Does anyone know what's going on? |:

- Brad

Try adding rootdelay=90 to the boot line.

---

