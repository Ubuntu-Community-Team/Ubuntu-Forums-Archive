---
title: "whenever i put strain on my computer it crashes"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Velenjak on 2011-02-24
i have an old dell 8400, ubuntu 9.10


whenever i try to back up files (transfer multiple GBs at a time) the computer logs out and crashes, or skips logging out and craps out entirely.

also when i try to download large files through torrents the computer will crash if the download speed gets too high.

this is unusual behavior for my computer - is this a sign of hardware dying? 

are there corrupted files somewhere?

what sort of checks can i run? thanks in advance

---

### Post by thefasterblueone on 2011-02-24
Check your log files for errors. Run Disk Utility to check hdd integrity.

---

### Post by Velenjak on 2011-02-24
all the options are shaded out... what do i do?

---

### Post by uRock on 2011-02-24
It would be best to run the Disk Utility from a LiveCD.

How much RAM does your machine have? Do you have a SWAP partition?

If you watch System Monitor while transferring files, does the RAM move towards 100%?

---

### Post by sandyd on 2011-02-24
> **Velenjak said:**
> i have an old dell 8400, ubuntu 9.10


whenever i try to back up files (transfer multiple GBs at a time) the computer logs out and crashes, or skips logging out and craps out entirely.

also when i try to download large files through torrents the computer will crash if the download speed gets too high.

this is unusual behavior for my computer - is this a sign of hardware dying? 

are there corrupted files somewhere?

what sort of checks can i run? thanks in advance
computer should work fine, I used to use one of those as a DNS server.
check RAM (memtest) and SMART status of HD.

---

### Post by Velenjak on 2011-02-24
> **uRock said:**
> It would be best to run the Disk Utility from a LiveCD.

How much RAM does your machine have? Do you have a SWAP partition?

If you watch System Monitor while transferring files, does the RAM move towards 100%?

my cd drive is busted... i tried running it off a usb but for some reason the computer wouldnt boot into the ubuntu file

my cpu2 is sometimes hitting 100% doing very mundane things, when i transfer files it doesn't spike though - weird...  as i type this cpu2 is 100% with nothing else running

---

### Post by fabricator4 on 2011-02-24
> **Velenjak said:**
> what sort of checks can i run? thanks in advance

Definitely run a memory test, preferrably memtest86+

You'll need to leave it running for some time.  If you turn on badram reporting and it finds bad blocks, apparently you can use this data in badram in grub to tell the kernal to avoid using bad areas of RAM. (I haven't had to do this bit)

Chris

---

### Post by Velenjak on 2011-02-24
> **sandyd said:**
> computer should work fine, I used to use one of those as a DNS server.
check RAM (memtest) and SMART status of HD.

on my disk utility it says on my HD that SMART is not available...


im looking into memtest now

---

### Post by uRock on 2011-02-24
When you run the top command in a terminal what does it show as eating your CPU?```
top
```

---

### Post by Velenjak on 2011-02-28
i cant figure out how memtest works


i tried running check for file errors on the recovery cd, no errors found

i tried running check memory test - i got the error message 'can not load a ram disk with an old kernal image' what does this mean?

are there any other checks i can run to see the integrity of my memory?

---

### Post by Velenjak on 2011-02-28
> **uRock said:**
> When you run the top command in a terminal what does it show as eating your CPU?```
top
```

false alarm on that

even when im transferring files cpu usage doesn't get too high

it does seem however that when im around 1gb transfered (after moving small blocks at a time) the computer will lock up and crash

---

### Post by fabricator4 on 2011-02-28
> **Velenjak said:**
> i cant figure out how memtest works

Memtest should start checking the memory as soon as you start it.  To start it you have to invoke it either from the grub menu, or from a boot cd such as "The Ultimate Boot CD" which is a handy thing to have in your toolkit.

I'm not sure that 9.10 releases had memtest86+ incorporated now that I think of it.  If you don't have a working CD drive it will make things very awkward in this case.  Try running a cleaner in the drive - I've found it does help in some cases, however the drive may be at the end of its useful life.  Unfortunately they do become unreliable after they've been in the case for a few years.  Sometimes the best you can manage is to get it to read disks that where written in the same broken drive.  (If it won't even burn disks that it can read itself, it's time for a new drive, definitely.)

Booting off USB can be problematic on older machines, but see if there's a "USB drive" or "USB device" under boot priority in the BIOS.  Some BIOS's can also access a "boot menu" with a given keypress during post.  This is often <esc>, F1, F12 or similar.  You'll usually see a message flash up "Press <somekey> for boot menu which will then give you a list of found boot devices.  On some of my machine this is the _only_ way to boot off a USB memory stick.

Chris

---

### Post by Velenjak on 2011-02-28
> **fabricator4 said:**
> Memtest should start checking the memory as soon as you start it.  To start it you have to invoke it either from the grub menu, or from a boot cd such as "The Ultimate Boot CD" which is a handy thing to have in your toolkit.

I'm not sure that 9.10 releases had memtest86+ incorporated now that I think of it.  If you don't have a working CD drive it will make things very awkward in this case.  Try running a cleaner in the drive - I've found it does help in some cases, however the drive may be at the end of its useful life.  Unfortunately they do become unreliable after they've been in the case for a few years.  Sometimes the best you can manage is to get it to read disks that where written in the same broken drive.  (If it won't even burn disks that it can read itself, it's time for a new drive, definitely.)

Booting off USB can be problematic on older machines, but see if there's a "USB drive" or "USB device" under boot priority in the BIOS.  Some BIOS's can also access a "boot menu" with a given keypress during post.  This is often <esc>, F1, F12 or similar.  You'll usually see a message flash up "Press <somekey> for boot menu which will then give you a list of found boot devices.  On some of my machine this is the _only_ way to boot off a USB memory stick.

Chris

thanks for the info, i found the culprit to be one of the memory sticks after a bunch of guess & checking with memtest.

---

### Post by fabricator4 on 2011-02-28
> **Velenjak said:**
> thanks for the info, i found the culprit to be one of the memory sticks after a bunch of guess & checking with memtest.

Excellent  :P

You can mark the thread solved by clicking under "thread tools" drop down menu at the top.;-)

Chris.

---

