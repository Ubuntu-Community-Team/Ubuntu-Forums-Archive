---
title: "Hardy crashed, won't boot, live CD won't boot either"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Newbie-Doo on 2009-07-01
I think I killed it this time, but what did I kill?
 
I have a Dell Inspiron 530N desktop that I got with Feisty preinstalled about a year and a half ago. Being a complete newbie, I have been scared of upgrades, but I went through Gutsy and then, a few weeks ago (after Gutsy expired), to Hardy. Hardy has worked fine, for the most part, but it has had a tendency to be glitchy at boot-up, with occasional hang-ups at the start of the GUI screen where the orange courser would just go back and forth on the black bar without making further progress. That seemed to be solved by going to the boot menu and selecting (again) the hard drive as the boot device. At least it did until it crashed last night.
 
Now nothing works. It won't boot, and I can't get it to boot from the live CD either. The various threads I've been able to find (I'm on an old PC now.) that sound similar tend to have fixes based on getting that live CD going, which I haven't been able to do.
 
I'm afraid I have a hardware failure of some sort, but how do I figure out what? If it is my hard drive, why doesn't the live CD boot? 
 
Any help appreciated by an old dog trying to learn some new tricks.
 
Newbie-Doo
 
Oh, yes: Intel dual core processor, 1.6 GH, 1 MB L2, 1 GB SDRAM, 250 GB SATA HD, 128 MB NVIDIA, Integrated audio, Integrated NIC

---

### Post by TeoBigusGeekus on 2009-07-01
Do you see anything on your screen after you boot (ram test for example, or bios preferences)?

---

### Post by wpshooter on 2009-07-01
Is the live CD that you are trying to boot to one that you have been able to successfully boot to before ?

And you do have your CD drive as the FIRST boot device in BIOS, correct ?

---

### Post by Newbie-Doo on 2009-07-01
> **TeoBigusGeekus said:**
> Do you see anything on your screen after you boot (ram test for example, or bios preferences)?
 
If you mean when I try to boot from the hd, the courser goes back and forth for a few minutes, then it kicks into a text screen (I think it's Busybox) that runs an unending series of lines with ominous-sounding stuff like "ata2.00: status: { DRDY }." There was also something at the beginning of that (sorry, didn't get it all copied) that was something like "ALERT /dev/disk ... does not exist"
 
If you mean when I try to boot the live CD, I get a language screen first, then it kicks into a text screen that doesn't do anything I can figure out. One of the posts I found earlier said to open a terminal, but I couldn't get it to open one.
 
Thanks.
 
N-D

---

### Post by Newbie-Doo on 2009-07-01
> **wpshooter said:**
> Is the live CD that you are trying to boot to one that you have been able to successfully boot to before ?
 
And you do have your CD drive as the FIRST boot device in BIOS, correct ?
 
I haven't ever booted into the live CD. I made it when I upgraded to Hardy, as a backup, but I did the upgrade through Symantic.
 
And I did go into the BIOS and make the CD drive the first boot device when I tried to boot it. (Good question, though; usually, that's probably one I would miss. ;-)
 
Thanks.
 
N-D

---

### Post by stuart.reinke on 2009-07-01
have you used the live cd before? It sounds like you might have a "special install" disk

---

### Post by Newbie-Doo on 2009-07-01
> **stuart.reinke said:**
> have you used the live cd before? It sounds like you might have a "special install" disk
 
I know I haven't used it before. I see that I didn't make it when I upgraded to Hardy, because I did that this year (after Gutsy expired).
 
The CD is labeled: HARDY HERON ISO 5-16-08 LIVE INSTALL IMAGE. (I think I made it when I upgraded from Feisty to Gutsy. Knowing me, I thought about forging ahead to Hardy but chickened out.)
 
Anyway, isn't an ISO the right thing?
 
Thanks.
 
N-D

---

### Post by stuart.reinke on 2009-07-01
You've got the right disk. After choosing the language, do you get a menu? First choice is "Try Ubuntu Without changing your computer" Select it and the live session will start.

---

### Post by Newbie-Doo on 2009-07-01
> **stuart.reinke said:**
> You've got the right disk. After choosing the language, do you get a menu? First choice is "Try Ubuntu Without changing your computer" Select it and the live session will start.
 
Here's what happens: After I select "Try Ubuntu Without changing your computer", it says "Loading Linux Kernel," and then the graphic screen with the orange courser on the black bar (What's the right term for that?) appears for a minute or so. Then it goes back to a text screen, the first line of which contains the term "BusyBox." Line 2 says something like Enter 'help' for a list of built-in commands. Line 3 looks kind of like a terminal prompt, but it says (initramfs).
 
Earlier today I entered "help" there, which got me a list of commands, none of which seemed to work. Just now I didn't do that, and in a few seconds the display became a page-wide line of stuff that began with "[96.563606] ata1.00: ... (didn't get it all copied - it was moving pretty fast) ... and ended with "revalidation failed (errno=5)." The second line was something else about ata1:00, and then it all went into the nonstop sequence of sets of three lines, all of them beginning with numbers in brackets and then listing ata2.00; the first of each 3 lines mentions "exception Emask ... frozen," the second line starts with "cmd," and the third line says "status: { DRDY }."

That just appears to go on forever; not the "live session" either of us had in mind, I think...
 
Thanks.
 
N-D

---

### Post by wpshooter on 2009-07-01
> **Newbie-Doo said:**
> I know I haven't used it before. I see that I didn't make it when I upgraded to Hardy, because I did that this year (after Gutsy expired).
 
The CD is labeled: HARDY HERON ISO 5-16-08 LIVE INSTALL IMAGE. (I think I made it when I upgraded from Feisty to Gutsy. Knowing me, I thought about forging ahead to Hardy but chickened out.)
 
Anyway, isn't an ISO the right thing?
 
Thanks.
 
N-D

It sounds like it is the right thing BUT did you **BURN** the ISO image to the CD ?  

It has to be **burned** not copied as data !!!

Ignore above, sounds like you do have it BURNED.

Did anyone ask if you have checked the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Also, do you have anything presently on this computer in the way of either O/Ss or programming and/or data that you need to preserve ?

If not, the get [www.killdisk.com](www.killdisk.com) and make a bootable CD of the killdisk program and use it to WIPE the hard drive completely clean and then try installing Ubuntu again, this time preferably from the ALTERNATE (text based) CD version of Ubuntu.

Good luck.

---

### Post by Newbie-Doo on 2009-07-01
>  
> **wpshooter said:**
> It sounds like it is the right thing BUT did you **BURN** the ISO image to the CD ? 
 
It has to be **burned** not copied as data !!!
 
Ignore above, sounds like you do have it BURNED.
 
Did anyone ask if you have checked the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

I tried that just now, and it shot me straight into the whole BusyBox routine...
 
[quote] 
Also, do you have anything presently on this computer in the way of either O/Ss or programming and/or data that you need to preserve ?
 
Depends on how you define "need," I guess; I just finished my first project in Gimp (2 days worth), and I sure don't want to do all that again... ;-)
 
>  
If not, the get [www.killdisk.com]("http://www.killdisk.com/") and make a bootable CD of the killdisk program and use it to WIPE the hard drive completely clean and then try installing Ubuntu again, this time preferably from the ALTERNATE (text based) CD version of Ubuntu.
 
I suppose it might come to that. A question first, though: If I were to buy a new hard drive and do a clean install on that, wouldn't I be able to retrieve what's on the old one? That's what I'm thinking, anyway, and why I would really like to know what the exact nature of my problem is.
 
>  
Good luck.
[/quote] 
Thanks.
 
N-D

---

### Post by Newbie-Doo on 2009-07-02
Bump.
 
Can someone smarter/more experienced than me answer one or both of two questions?
 
1. Does this seem like a hardware issue? (And if so, what hardware? OK, so it's three questions. ;-).
 
2. If I Escape-Key into Grub, I see 3 sets of kernels; do I have anything to lose (or gain) by trying to open one of the older ones?
 
Thanks.
 
Newbie-Doo

---

### Post by Newbie-Doo on 2009-07-03
Solved. Kinda ugly, but...

In the last entry in the thread at [http://ubuntuforums.org/showthread.php?t=771373](http://ubuntuforums.org/showthread.php?t=771373), foundbobby wrote "For me it was making sata mode from IDE -> "RAID" without actually creating a raid... seems to have worked." about a similar problem. I did that, and my machine is running again.

Thanks, foundbobby!

---

