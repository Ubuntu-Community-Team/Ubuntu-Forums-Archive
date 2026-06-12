---
title: "Can't boot off Live CD"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by kev72491 on 2008-12-04
I downloaded the ISO for ubuntu and then burnt it to a DVD. The problem I am facing is that I can not get it to boot on my computer. I know the disc works because I tried it on another computer in the house, this computer didn't have a problem with it at all. Does anyone know why this is?

---

### Post by iaculallad on 2008-12-04
> **kev72491 said:**
> I downloaded the ISO for ubuntu and then burnt it to a DVD. The problem I am facing is that I can not get it to boot on my computer. I know the disc works because I tried it on another computer in the house, this computer didn't have a problem with it at all. Does anyone know why this is?

It works in another computer in your house? By booting from it or simply inserting it on your optical drive while booted on an OS? And how did you burn the ISO file? As a File or as an Image?

---

### Post by Shwefty on 2008-12-04
What exactly is happening when you are trying to boot from it?

---

### Post by handydan918 on 2008-12-04
AND...
Try burning it to a cd instead...and not a cd-rw, either.

---

### Post by sambarusty on 2008-12-04
I have to agree, "It doesn't work".  is hard to trouble shoot.  Are you sure you have the bios on this computer set to boot from the CD drive, when you say you didn't have a problem on  another machine, does that mean you went through the installation, or the machine booted from the disk. If one machine is booting from the disk and the other is not, it would seem that it is a configuration thing. (meaning bios setting.)  This obviously is omiting any sort of pertinent errors you are receiving that were not reported in the original post.

---

### Post by kev72491 on 2008-12-04
I used PowerISO to burn the files to a DVD-RW and on the other computer I have actually booted Ubuntu(used it as the operating system)

---

### Post by Shwefty on 2008-12-04
And if it is a cd/dvd drive issue and not a BIOS setup issue, check out [unetbootin]("http://unetbootin.sourceforge.net/") if you have a 1GB+ USB 2.0 sitting around which you don't mind formatting.  You can boot off of it just like the LiveCD, may be faster too \\:D/ 

Unetbootin has a Windows version too...same website.

---

### Post by Shwefty on 2008-12-04
Okay, so, when you turn on the computer you're trying to setup...  You put the DVD in the tray, turn on the computer:

Do you hit F12 (or F11 or whatever the Boot Settings key is) and select boot from CD/DVD drive?  Or were you thinking that it should boot from the DVD first anyway?  If you haven't tried changing the boot order in the BIOS, that's problem #1.  Problem #2, you computer can't physically read DVDs.  Problem #3, the DVD doesn't have time to spin up before the computer stops trying to recognize a disc in the slot.

---

### Post by kev72491 on 2008-12-04
[ 126.864035] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 126.864094] ata4.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 126.864096]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 126.864201] ata4.00: status: {DRDY}

~~~~~The above code is repeated about 6 times with the numbers in the brackets changing every time. They also change each time I boot. On top of that every so often the "ata4.00" will be "ata2.00" instead. There is more to what is displayed if you need it the beginning is shown below but it is too hard for me to keep up with it.

[ 370.800230] ata4.00: status: {DRDY}
[ 371.292156} end_request: I/O error, dev sdb, sector 0

---

### Post by kev72491 on 2008-12-04
it is definitely reading the DVD...it makes it to the menu where it asks if i want to continue without changing anything, install, check cd for errors... then i select continue without changing anything and it comes up with the ubuntu loading screen then it comes up with a bunch of code. I posted what i could of it in my last post.

---

### Post by maheshjr2000 on 2008-12-04
Ya oh, dont think thats a BIOS problem. Might be but I think its a problem with your drive. Rationalization: It booted and then broke.

---

### Post by kev72491 on 2008-12-04
Hmm, I really don't know what is going on now...I just got done trying it again and after about 10minutes it booted up in ubuntu.

---

### Post by falcon61102 on 2008-12-04
Your computer/BIOS/drive may be having a hard time with the DVD-RW formatting being used as a boot disc.  If you have one handy, try burning the .iso onto a CD-R and see if that helps.

---

### Post by handydan918 on 2008-12-04
> **falcon61102 said:**
> Your computer/BIOS/drive may be having a hard time with the DVD-RW formatting being used as a boot disc.  If you have one handy, try burning the .iso onto a CD-R and see if that helps.

Sounds like a great idea, born of experience. Wish I'd thought of it....


):P

---

### Post by Shuberace on 2008-12-04
> **falcon61102 said:**
> Your computer/BIOS/drive may be having a hard time with the DVD-RW formatting being used as a boot disc.  If you have one handy, try burning the .iso onto a CD-R and see if that helps.

For what it's worth, I burned the .iso onto a quality CD-R, and I'm having a similar problem. No error code or cryptic messages, it just quits doing ANYTHING after I select one of the boot-up options.

And here I was hoping I could try it out... :(

---

### Post by theozzlives on 2008-12-04
> **kev72491 said:**
> [ 126.864035] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 126.864094] ata4.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 126.864096]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 126.864201] ata4.00: status: {DRDY}

~~~~~The above code is repeated about 6 times with the numbers in the brackets changing every time. They also change each time I boot. On top of that every so often the "ata4.00" will be "ata2.00" instead. There is more to what is displayed if you need it the beginning is shown below but it is too hard for me to keep up with it.

[ 370.800230] ata4.00: status: {DRDY}
[ 371.292156} end_request: I/O error, dev sdb, sector 0

I got errors like that when my dvd/r was going bad

---

### Post by falcon61102 on 2008-12-04
Shuberace,

When you get to the Ubuntu Boot menu, try pressing F4 and selecting one of the alternate boot methods.  You may have some better luck with that.

kev72491,

You may want to try the same thing and see if that improves things.  It shouldn't take 10 minutes to load up and something is causing it to hang.  If you boot into the Recovery Mode, a lot less drivers will be loaded and that may speed things up.

---

### Post by kev72491 on 2008-12-04
I have 2 DVD drives on this computer and they both act the same way and one of them is only 3months old. I would also like to add the information that it has now started booting about 90% of the time but it take about 10-20minutes...i have a 2.2GHz dual core processor with 4GBs RAM and windows starts within 30seconds so I don't think its a problem with my computer just being slow.

---

