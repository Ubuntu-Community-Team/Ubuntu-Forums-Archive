---
title: "USB slow speed fixed yet?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-12-27
My USB transfer rates suck. I've tried disabling legacy usb support, "pci=routeirq" in menu.lst, "mount -o remount,async /dev/sdb1" all with no luck.

I'm just wondering if I'm the only one experiencing this? Did they fix this problem and I'm the only sucker without hi-speed USB on my Ubuntu?

---

### Post by QLee on 2009-12-27
[QUOTE=Cuco3]My USB transfer rates suck. I've tried disabling legacy usb support, "pci=routeirc" in menu.lst, "mount -o remount,async /dev/sdb1" all with no luck.[/QUOTE]

I'm don't think that pci=routeirc is doing what you expect, where did you find that advice? Disabling legacy USB support is something that is usually done in the BIOS. However, disabling that isn't going to automagically make your system have a faster transfer rate.

 
[QUOTE=Cuco3]I'm just wondering if I'm the only one experiencing this? Did they fix this problem and I'm the only sucker without hi-speed USB on my Ubuntu?[/QUOTE]

Well, high speed USB (I assume you mean USB2 here) is dependent on the capabilities of both pieces of hardware. Have you confirmed that both your computer and whatever hardware you are trying to use is capable of high speed?

---

### Post by Cuco3 on 2009-12-27
> **QLee said:**
> I'm don't think that pci=routeirc is doing what you expect, where did you find that advice? Disabling legacy USB support is something that is usually done in the BIOS. However, disabling that isn't going to automagically make your system have a faster transfer rate.I meant to type "pci=routeirq". I'm not sure what it does either, but it's often suggested in the sites pertaining to this issue.

 


> **QLee said:**
> Well, high speed USB (I assume you mean USB2 here) is dependent on the capabilities of both pieces of hardware. Have you confirmed that both your computer and whatever hardware you are trying to use is capable of high speed?Yes sir. [Intel D845PESV]("http://www.intel.com/support/motherboards/desktop/d845pesv/sb/CS-008879.htm") w/ latest BIOS and Seagate Free Agent 1TB.

Anyway, how does USB 2.0 perform for you?

---

### Post by QLee on 2009-12-27
[QUOTE=Cuco3]Anyway, how does USB 2.0 perform for you?[/QUOTE]

More to the point, explain what you are seeing. What kind of sustained transfer rate are you getting and under what conditions? What is it that you are expecting and not getting?

---

### Post by Cuco3 on 2009-12-27
> **QLee said:**
> More to the point, explain what you are seeing. What kind of sustained transfer rate are you getting and under what conditions? What is it that you are expecting and not getting?Moving files anywhere from 300 MB to 1.4 GB from my hard disk on to a USB 1TB drive. I'm averaging 5.8 MB/s when theoretically USB 2.0 is capable of 60 MB/s (even though it's not likely for a couple reasons. To be honest, I'd be happy with half that).

I should add that the USB 1TB drive has its own power supply and that I've also tried using a powered USB hub with no luck.

---

### Post by mutex023 on 2009-12-27
I've the same problem as Cuco3.
Transferring files anywhere greater than 1Gb in size is a pain. Transfer rate starts at around 9Mbps and then crawls to 1-2 Mbps. 
There is no problem if I transfer the files in windows.
I've searched the net and also the forums, and I see that this is a recurring problem for many users. Bug reports have also been raised, but it still is to be fixed so far...

---

### Post by kerry_s on 2009-12-27
how are the drives formatted? ntfs or fat

---

### Post by mutex023 on 2009-12-27
formatted with FAT

---

### Post by Cuco3 on 2009-12-27
Mines is formatted using Ext3.

Mutex023: yeah, unfortunately, the only work around is to put it the drive on a Windows machine to facilitate the transfer. :(

---

### Post by falconindy on 2009-12-27
ntfs transfer rates will be better. No reason to use fat if the flash drive will support ntfs.

---

### Post by warfacegod on 2009-12-27
> Moving files anywhere from 300 MB to 1.4 GB from my hard disk on to a USB 1TB drive. I'm averaging 5.8 MB/s when theoretically USB 2.0 is capable of 60 MB/s (even though it's not likely for a couple reasons. To be honest, I'd be happy with half that).


Are you moving that much info as one file or lots of little files in one folder? Lot's of little ones seem to go faster (for me anyway).

USB2 will *theoretically* run at 60 MB/s but that is under ideal conditions and it won't stay that fast, ever. Transfer speeds depend on a number of factors, including: each drives' buffer size, each drives' RPM, your motherboards' throughput speed, file size, number of files, number of transfers, filesystem each drive has, total system load, number of usb channels, etc. etc.

Your equipment simply may not be able to give you the speeds you want. I'm running some fairly high-end stuff and only once did I get 28 MB/s. Sometimes, I get 18 - 24 but usually I'm around 12 - 15. I'm happy if I get 10 MB/s and these number are *way* better than I got in Windows using the same and *faster* hardware.

And yes, 10 MB/s is USB 1.1 speed. USB2 has been one of the biggest con jobs pulled on the computing public in years. We all should have bought Firewire.

---

### Post by Cuco3 on 2009-12-27
> **warfacegod said:**
> Are you moving that much info as one file or lots of little files in one folder? Lot's of little ones seem to go faster (for me anyway).

USB2 will *theoretically* run at 60 MB/s but that is under ideal conditions and it won't stay that fast, ever. Transfer speeds depend on a number of factors, including: each drives' buffer size, each drives' RPM, your motherboards' throughput speed, file size, number of files, number of transfers, filesystem each drive has, total system load, number of usb channels, etc. etc. the files are anywhere from 300 MB to 1.4 GB each.

> **warfacegod said:**
> Your equipment simply may not be able to give you the speeds you want. I'm running some fairly high-end stuff and only once did I get 28 MB/s. Sometimes, I get 18 - 24 but usually I'm around 12 - 15. I'm happy if I get 10 MB/s and these number are *way* better than I got in Windows using the same and *faster* hardware.I've also tried transfering on my machine using my XP install via FSDriver, and the times are much more improved than in Ubuntu.

> **warfacegod said:**
>  And yes, 10 MB/s is USB 1.1 speed. USB2 has been one of the biggest con jobs pulled on the computing public in years. We all should have bought Firewire.Actually, USB 1.1 speed is 12Mbits/s (1.5 MB/s), not 10 MB/s

---

### Post by niteshifter on 2009-12-27
Hi,

This has been a long-running problem in Linux because it's a complicated issue with many variables: kernel, hardware mix, desktop environment. Not everybody has it, and those that do have it for different reasons, there's no universal fix for this.

I've had it since I upgraded to 8.04 on this Dell 1420n - but mine is GNOME related (gvfs bug). What works for me on big file transfers (300MB or larger) is to not drag-n-drop with Nautilus, I drop to a terminal and and just copy (via cp) instead. Transfer speed is then back to my "normal" of 25 - 28 mb/s.

---

### Post by Cuco3 on 2009-12-27
> **niteshifter said:**
> Hi,

This has been a long-running problem in Linux because it's a complicated issue with many variables: kernel, hardware mix, desktop environment. Not everybody has it, and those that do have it for different reasons, there's no universal fix for this.

I've had it since I upgraded to 8.04 on this Dell 1420n - but mine is GNOME related (gvfs bug). What works for me on big file transfers (300MB or larger) is to not drag-n-drop with Nautilus, I drop to a terminal and and just copy (via cp) instead. Transfer speed is then back to my "normal" of 25 - 28 mb/s.Dude, I think that works. Is there anyway to get a progress bar or transfer rate with CP?

---

### Post by warfacegod on 2009-12-28
> Actually, USB 1.1 speed is 12Mbits/s (1.5 MB/s), not 10 MB/s

For all practical uses, it's the same thing. I've seen little difference in my USB1.1 and USB2 drives when the 2 drive is running at around 10M.

---

### Post by mutex023 on 2009-12-28
> **niteshifter said:**
> 
What works for me on big file transfers (300MB or larger) is to not drag-n-drop with Nautilus, I drop to a terminal and and just copy (via cp) instead. Transfer speed is then back to my "normal" of 25 - 28 mb/s.

Copying files using cp does not seem to show any improvement for me :(

---

### Post by meindian523 on 2009-12-28
Well, USB wasn't designed for sustained high throughput. You should be expecting intermediate bursts of high speed, not 5 MB/s throughout a file. In my case, I do get 6MB/s+ when I transfer, but then my "large files" are usually folders with many small files in them.

---

### Post by lavinog on 2009-12-29
Post your dmesg.
also are you still using jaunty?
Is this a fresh install?

---

### Post by Cuco3 on 2009-12-29
> **lavinog said:**
> Post your dmesg.
also are you still using jaunty?
Is this a fresh install?dmesg is too long and I can't pipe grep to a text file to get the full dmesg. If you want me to include the dmesg that shows up just let me know.

I'm using Jaunty.

Fresh install.

---

### Post by Cuco3 on 2009-12-29
> **meindian523 said:**
> Well, USB wasn't designed for sustained high throughput. You should be expecting intermediate bursts of high speed, not 5 MB/s throughout a file. In my case, I do get 6MB/s+ when I transfer, but then my "large files" are usually folders with many small files in them.I completely understand not to expect 60 MB/s, but 5 MB/s is ridiculously low for USB 2.0 (exactly 1/12 of the max speed attainable). Getting 20 MB/s (1/3rd of USB 2.0) would be a god send and 4x as fast as my current throughoutput.

---

### Post by cascade9 on 2009-12-29
> **warfacegod said:**
> USB2 will *theoretically* run at 60 MB/s but that is under ideal conditions and it won't stay that fast, ever. Transfer speeds depend on a number of factors, including: each drives' buffer size, each drives' RPM, your motherboards' throughput speed, file size, number of files, number of transfers, filesystem each drive has, total system load, number of usb channels, etc. etc.

Your equipment simply may not be able to give you the speeds you want. I'm running some fairly high-end stuff and only once did I get 28 MB/s. Sometimes, I get 18 - 24 but usually I'm around 12 - 15. I'm happy if I get 10 MB/s and these number are *way* better than I got in Windows using the same and *faster* hardware.

I've _never_ seen USB 2.0 go over 35MB/sec continuous speed, on any OS and the 28-30 seems to be as fast as it goes. 

Agreed that fierewire is a better standard, even if it does have a lower theoretical speed, 400Mbit, 50MB/sec (it will run at 40MB/sec continuous IIRC). 

If you really want speed, ESATA is a much better choice. There are USB 2.0/ESATA enclosures around now, for the best of both worlds (USB for best compatibility, ESATA for speed if you have the support).

> **warfacegod said:**
> And yes, 10 MB/s is USB 1.1 speed. USB2 has been one of the biggest con jobs pulled on the computing public in years. We all should have bought Firewire.

USB 1.0 and USB 1.1 have teh same rated speed. All USB 1.1 was over 1.0 was a bugfix, no speed increase at all. Its more common because USB 1.1 was released in late 1998, when USB was nowhere near as common as today, and USB 1.1 was adopted pretty quicky. BTW USB 1 devices came in 'low-speed' (1.5Mbit/sec, 0.1875MB/sec) 'full-speed' (12Mbit/sec, 1.5MB/sec).

---

### Post by warfacegod on 2009-12-29
> If you really want speed, ESATA is a much better choice. There are USB 2.0/ESATA enclosures around now, for the best of both worlds (USB for best compatibility, ESATA for speed if you have the support).

I agree, however, USB3 is supposedly ridiculously faster than SATA/ESATA with sustained throughput and it should be widely available within the next year. I'm going with it assuming:

.01 It proves to be up to the speed claims

.02 Firewire2 doesn't turn out to be better

.03 It isn't stupidly expensive

---

### Post by cascade9 on 2009-12-29
Judging by USB promises vs delivery, I'm not holding out much hope for USB 3, but who knows till it gets out? 

I would guess that its going to be pretty expensive, to being with anyway. I could well be wrong on that, seeing how the 1st ESATA flash drives are out now. If its too expensive, people will just move to ESATA. 

[http://www.ocztechnology.com/products/flash_drives/ocz_throttle_esata_flash_drive](http://www.ocztechnology.com/products/flash_drives/ocz_throttle_esata_flash_drive)

Cute how its ESATA and USB 2 (via mini USB port).

---

### Post by warfacegod on 2009-12-29
> **cascade9 said:**
> Judging by USB promises vs delivery, I'm not holding out much hope for USB 3, but who knows till it gets out? 

I would guess that its going to be pretty expensive, to being with anyway. I could well be wrong on that, seeing how the 1st ESATA flash drives are out now. If its too expensive, people will just move to ESATA. 

[http://www.ocztechnology.com/products/flash_drives/ocz_throttle_esata_flash_drive](http://www.ocztechnology.com/products/flash_drives/ocz_throttle_esata_flash_drive)

Cute how its ESATA and USB 2 (via mini USB port).

Not too bad price wise. Still, ESATA isn't all that common of a connection although it is becoming more so. I think USB3 is going to be the winner in sales again. People don't like change even if it's an obvious improvement. Besides, whether we like it or not, Microsoft prefers USB not ESATA and certainly not Firewire. I'm going with whatever has the best performance, not the best hype. I hope (unlikely) everone else does too.

---

### Post by meindian523 on 2009-12-30
My bad, that was meant to be burst speed of **15** MB/s (not 5) and sustained around 8-9 MB/s for large files 700-800 MB odd. And it IS 5MB/s for big-transfer-many-files (each file around 2-3MB) sometimes slower than that.

---

### Post by lavinog on 2009-12-30
> **Cuco3 said:**
> dmesg is too long and I can't pipe grep to a text file to get the full dmesg. If you want me to include the dmesg that shows up just let me know.

I'm using Jaunty.

Fresh install.
```

dmesg >~/dmesg.txt
gzip dmesg.txt

```
upload dmesg.txt.gz

---

### Post by cascade9 on 2009-12-30
> **warfacegod said:**
> Not too bad price wise. Still, ESATA isn't all that common of a connection although it is becoming more so. I think USB3 is going to be the winner in sales again. People don't like change even if it's an obvious improvement. Besides, whether we like it or not, Microsoft prefers USB not ESATA and certainly not Firewire. I'm going with whatever has the best performance, not the best hype. I hope (unlikely) everone else does too.

Little known fact is that you can rig up ESATA, without to much trouble, for a desktop with a spare SATA port. 

The main issue I see with ESATA is that theres been way to many standards. USB at least has one standard plug, which has caused its own issues (how do I tell my USB 2 ports from USB 1). 

Firewire should have been huge, but AFAIK its cost that held it back. Pity really.....but if there is any issue holding back USB 3 (regardless of win/lose) its going to licensing fees.

Personally, I think that ESATA might be better, even if USB 3 'wins' (which I think is likely, Intel + Microsoft pushing something means that its almost a forgone conclusion that everything will get it).

---

### Post by warfacegod on 2009-12-30
I would like to see the computer industry pick a connection and stick with (I vote for telepathy, look Ma not wires). In fact, standardization would be a good idea in allot of computer areas hardware and software (Windows being compatible with *Windows* would be a good start).

Examples:

01. Stereo Equipment:

    RCA cables have been the standard connection for X decades. I can connect virtually any component and know it will work. Simple.

02. Television Equipment:

    Coaxial
    RCA
    S-Video
    Component
    Fiber Optic
    DVI and it's *3* iterations
    HDMI

    These are *all* still being used.


Most folks want to buy something, plug it in and use it, not screw around with "will this bit connect to my thingamabob, oh wait, what will they do to my doohicky.

Just pick a way to do something and if it has weaknesses in some areas; *fix it* don't replace it.

---

### Post by nhasian on 2010-01-12
yes its fixed, but not in the 2.6.31 kernel branch.  I experienced the same problem you described when trying to copy files from my internal hard disk to either a usb external hard disk or a usb thumbdrive.  the speed would start at about 30 MB/s then quickly drop down to 5 MB/s and sometimes get down to even 1.5 MB/s.  I thought it was pretty funny that i could download files from the Internet at 2.6 MB/s but couldnt even transfer them via usb that fast.  It also spiked my CPU and caused my wifi to hang and disconnect as well.

Last night I installed the Linux 2.6.33RC3 kernel from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc3/)

I ran some tests and found that my USB file transfers ran at full speed and did not drop like before.  I should point out that I am running the 64bit kernel so i dont know if this issue exists with the 32bit kernel or not.

---

### Post by Rat2000 on 2010-01-27
Still slow. I hate to see my eSATA drive crawl like this.

Oh well, I'm used to it, this problem has been fixed and come back with Ubuntu for a couple of years now.

---

### Post by nhasian on 2010-01-27
It affects eSATA as well?  have you tried a newer kernel as I suggested in the previous post?

> **Rat2000 said:**
> Still slow. I hate to see my eSATA drive crawl like this.

---

### Post by kmrdeva on 2010-04-13
Thanks for the tip, nhasian. 

I have upgraded my Lucid beta2 64 bit on my laptop to the latest [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) kernel. Will test usb transfer speeds when I get back home tonight.

Am thinking of updating my Karmic 64 bit on the home PC too.

---

### Post by kmrdeva on 2010-04-13
> **kmrdeva said:**
> Will test usb transfer speeds when I get back home tonight.

I am still seeing slowdowns to about 5MB/sec (from originally listed 30MB/sec) but at least the transfer speeds don't drop down to 1-ish MB/sec speeds with this new kernel.

Will need to monitor this very closely.

---

### Post by nuzeb on 2010-05-13
Hello. I'm another one affected by slow USB transfer rates and I've nearly given up hope on this.

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9291403&postcount=118](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9291403&postcount=118)

---

### Post by mantaor on 2010-05-15
Hi guys,
I have the same problem  with various pen drive (same situation with Karmic). It's really incredible. I think this bug is a huge stop to ubuntu diffusion. Thinks if win or Osx has a similar stupid problem....Developers, where are you?
Dual boot forever until this this problem will be solved, even I appreciate your work.

---

