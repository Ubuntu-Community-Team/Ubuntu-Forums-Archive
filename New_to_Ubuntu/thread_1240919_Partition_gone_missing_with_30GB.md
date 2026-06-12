---
title: "Partition gone missing with 30GB"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by andrewsutton on 2009-08-15
Hi there,

I am totally new to Ubuntu and hope someone can help me with this one please....

I installed Ubuntu on an Asus S6 with 100GB of hard disk. Before installing Ubuntu, I had two partitions set up, 70GB and 30GB, with Windows installed in the larger partition.

During the installation process I allowed Ubuntu to install over the whole disk (at the installation screen where you get to choose what proportion of the disk you give to Ubuntu vs. Windows).

Now, Ubuntu seems to be installed and working fine, but it only shows me 70GB hard disk space. I have used the Gparted utility to see what is going on, which shows me:
   /dev/sda1     70GB
   /dev/sda2   3GB 
   /dev/sda5   3GB

and no other partitions.

Does anyone know what is going on and how I can reclaim the other 30GB of my hard disk?

Thank you very much :)

Andrew

---

### Post by Liolikas on 2009-08-15
Strange...paste here output of:
```

fdisk -l

```

---

### Post by andrewsutton on 2009-08-15
fdisk -l doesn't give me anything, it simply gives me a command line again. Do I need to add some more parameters?

Thanks very much for your help, really appreciated.

---

### Post by Liolikas on 2009-08-15
upsie I think you need:
```

sudo fdisk -l

```

---

### Post by andrewsutton on 2009-08-15
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
andrew@andrew-laptop:~$ 
 .

---

### Post by Liolikas on 2009-08-15
> 
I installed Ubuntu on an Asus S6 with 100GB of hard disk.

You sure?? Check it again in Laptop info.
Disk /dev/sda: **80.0 GB**
Your swap may be too big too decrease it to something like 1Gb.

---

### Post by fela on 2009-08-15
From all the information that you've given us, the only explanation I can find is that your HDD is about 73GB in size (could be an 80GB disk). Are you absolutely certain there was an extra 30GB on this disk?

---

### Post by jrothwell97 on 2009-08-15
First of all, welcome to the Ubuntu forums.

That is *bizarre*. Your drive is 100gB but fdisk is reporting it as only being 80gB.

My initial instinct would be that this is due to the way disk sizes are calculated. Disk manufacturers would have you believe that 1gB is 1,000,000,000 (1000^3) bytes: in reality, practically every operating system on the market calculates it as 1,073,741,824 (1024^3) bytes. However, the figures don't match up, as Windows reports a gigabyte as being 1024^3 bytes as well.

When you start up your computer, does it list internal storage devices during the POST (power on self-test - this is just after startup when the computer counts the RAM and looks for hard drives) and if so, does it report the size of your internal hard drive?

---

### Post by andrewsutton on 2009-08-15
hi fela - I am 99% certain it is a 100GB drive. That is what I remember, and supporting evidence is that I can't fit the contents of my backup external drive onto the laptop now, but that contents came straight from the laptop before I installed Windows. I will go and look for original documentation etc. though just to be certain.

jrothwell97 - how do I see POST? When I power up there is no text on screen, just the Ubuntu logo for a few seconds before login.

Thank you all.

---

### Post by andrewsutton on 2009-08-15
Hi Liolikas - how do I check Laptop info please? Is it a command?

---

### Post by Liolikas on 2009-08-15
Commands already show 80Gb hdd, other way is look into BIOS. 
When computer starts press something (like F2 or del) to enter BIOS.

---

### Post by andrewsutton on 2009-08-15
The original documentation I have doesn't state the HDD size, so I cannot confirm it was 100GB that way. But, I have more than 80GB of files on my external hard drive which is only a backup of the HDD, so it must have been more than 80GB.

---

### Post by jrothwell97 on 2009-08-15
Usually, computers will beep to indicate the POST was successful (the only exceptions are Macintosh computers, which chime when they've completed their POST.) You have a laptop, so things might be slightly different.

When you turn on the computer, you should see the manufacturer's logo. There will be instructions that say "press <a key> to enter SETUP or <a key> to show POST". The terminology varies (some machines call it "verbose mode", and some have to have it activated through BIOS setup).

On most computers, the power-on self test, once "quiet mode" is disabled or "verbose mode" is entered, looks something like [this](http://en.wikipedia.org/wiki/File:POST_P5KPL.jpg).

**edit**: OK, this is a bit of a long shot, but do you have any idea whether your old Windows installation was compressed?

---

### Post by fela on 2009-08-15
Partition table could be corrupt - try testdisk or a low level format (will wipe all data so beware).

---

### Post by andrewsutton on 2009-08-15
Hi there - I entered BIOS by pressing F2 but the partitions are not listed there. I did get to a screen which allowed me to choose what my machine booted from (sorry I can't be more specific, I am not exactly sure what it was) there were five options listed, all had numbers and Ubuntu in the title, with two of them followed with (Safe Mode).

I couldn't find verbose mode (the text scrolling up the screen on startup), and there is nothing on the Asus startup screen to tell me what to press.

I don't know whether Windows was compressed or not. Not intentionally.

Thanks for all your help - if there is not much more we can try, I think I will just get used to my new 80GB disk.

fela - how do I do a testdisk and is it dangerous?

---

### Post by fela on 2009-08-15
> **andrewsutton said:**
> fela - how do I do a testdisk and is it dangerous?

I've actually never done one, just heard about it so I can't really give any info on how to use it other than that you can find it in the system rescue cd (google that for a great rescue liveCD based on gentoo Linux).

I think it's more for actually recovering corrupt partition tables, so dangerous-ness doesn't really come into that (as the files are already potentially garbled anyway in that situation :P). But of course whenever doing anything to do with your disk I recommend backing up your data. Actually I recommend backing up your data anyway as you never know what can happen. Recently I had a massive harddrive failure caused by a head crash (it was a dud unit). Luckily I had all my photographs and music backed up.

---

### Post by andrewsutton on 2009-08-15
Thank you - but I think I will just get used to 80GB.

I am still happily exploring Ubuntu so I'm hesitant to embark on a day-long odyssey to sort this one out. That's what I am trying to escape from!

Thank you all for your help.

---

### Post by fela on 2009-08-15
It sounds more like a hardware error than a software error.

---

### Post by louieb on 2009-08-15
If your curious install **smartmontools **

Shows all kind of stuff straight from the drives firmware. 

```
sudo smartctl --all /dev/sda
```

---

### Post by jrothwell97 on 2009-08-15
> **andrewsutton said:**
> Hi there - I entered BIOS by pressing F2 but the partitions are not listed there. I did get to a screen which allowed me to choose what my machine booted from (sorry I can't be more specific, I am not exactly sure what it was) there were five options listed, all had numbers and Ubuntu in the title, with two of them followed with (Safe Mode).

That is not the BIOS screen - this is called GRUB, and that is the bootloader (the piece of software that lives at the front of your hard drive and starts Ubuntu.) The POST happens before this.

Just for your information.

Good luck getting used to your "new" 80G hard drive and enjoy Ubuntu!

---

### Post by LewRockwell on 2009-08-15
> **andrewsutton said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 5 Extended
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris
andrew@andrew-laptop:~$

you definitely have an 80GB hard drive

also, someone commented earlier that you had "too much" swap

I'd take that with a grain of salt

all the machines and drives we set up get SWAP equal 1X MAXRAM

so if your equipment will support 4GB of ram, then we're going to give you a 4GB swap

since we don't know what the future holds, we should partition with the maximums in mind

in the future if you have 3.7GB of data in ram and your machine attempts to go into a safe reduced power mode where it writes the ram data to swap for safekeeping...I guess you can see how "only" having 3GB of swap might cause your operating system a little headache...

as always, your mileage may vary...

we now return you to your regularily scheduled programming...

.

---

