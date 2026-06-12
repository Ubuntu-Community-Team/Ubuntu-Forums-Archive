---
title: "Help a newbie leave the Devil!"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Mazaman on 2011-05-13
Hey guys,

I have been working with computers all my life, and despite this, I know I am not as skilled as some people are.  

For about a two years, and I been trying to leave MS and a friend at work finally talked me into using Xubuntu before my next computer purchase, which is a new Commodore computer.   I have the perfect opportunity to now.  I have  blank 40GB hard drive  and works great, but for the life of me, I cannot get it to work.  I am  using a computer that currently runs XP.    I have two computers:  An Acer laptop with W7 which I am on right now, and the old Desktop with XP SP3 with 256GB (two HDs one C: with XP and one blank D: ), a DVD drive and CD drive.

This is what I did:

1. Downloaded the 11.04 ISO, then burned onto a DVD-R from my laptop
2.  While downloading and burning 11.04, I checked the other computer, seven year old desktop (has 256 GB RAM) and checked the DVD and clean HD drive to make sure it works.
3. Unplugged the C: drive in the Desktop.  Set the jumper to master on the clean HD, and plugged the primary IDE to the clean HD.  The other HD which has XP is unplugged.
4. Rebooted, and checked BIOS for boot sequence.  Everything looks fine.  Clean HD and DVD drive are detected.
5.  Get an error message "NTDLR is missing.  Press CTRL-ALT-DEL to reboot"

I have messed with the BIOS and still get the same error. I also put it back to the original config with the C: with XP and D: being the blank HD drive and everything works.  Set the clean HD to slave and secondary IDE and it is also detected when I reboot back to the original config.  Rebooted to XP and the C: drive is back to the original one, the D: drive is my clean HD (it is formatted to NTSF BTW), and the DVD drive is detected!

I have looked for an answer in the forum and online for an hour now, but I just cannot figure it out.  I know I am doing something stupid.  Help!

---

### Post by philinux on 2011-05-13
That seems to be a windows booting problem.

"NTDLR is missing. Press CTRL-ALT-DEL to reboot" Searching this produces a host of hits. [Hits]("http://www.google.com/search?client=ubuntu&channel=fs&q=NTDLR+is+missing.+Press+CTRL-ALT-DEL+to+reboot&ie=utf-8&oe=utf-8&gl=uk#q=NTLDR+is+missing.+Press+CTRL-ALT-DEL+to+reboot&hl=en&client=ubuntu&tbo=1&channel=fs&gl=uk&output=search&source=lnt&tbs=qdr:y&sa=X&ei=P3bNTbS0LZCDhQfQw9mFDQ&ved=0CAgQpwUoBQ&bav=on.2,or.r_gc.r_pw.&fp=6ba51508990fa4c8&biw=1277&bih=860")

---

### Post by Lazaruss on 2011-05-13
If you're getting that message, surely it means it's booting into windows, and not from the liveDVD?

Have you checked the disc?

---

### Post by rosencrantz on 2011-05-13
OK, just a few ideas: 
-You don't need to remove the XP drive to install Xubuntu if you don't mind having a dual boot setup. Xubuntu should figure out the details automatically.
-Which ISO did you get? The standard option is the LiveCD installer, which I'd recommend if you have a decent internet connection for downloading additional packages. You didn't by any chance burn that one to DVD, or, burn the .iso on a data disk (meaning, when you open the disk on another computer, is there a single .iso file on it or a full Xubuntu file system?)

I'd suggest trying to boot a live Xubuntu from a CD and installing from the live system. That also is a good way to see how well it runs on your computer before you install anything.

---

### Post by aphatak on 2011-05-13
When you try to boot with the Ubuntu 11.04 CD in the CD drive, does the PC allow you to choose where to boot from (i.e., local hard disk or CD)?  Did you try to set the computer to boot from CD before hard disk?
I am not familiar with the BIOS on Commodores.  Does the BIOS allow you to boot from CD in the first place?  I seem to remember an old computer (was it Kaypro?) that allowed you to boot from hard disk or floppy drives, but nothing else, I would check to see if the Coomodore BIOS is similar.

---

### Post by BertN45 on 2011-05-13
You  disk starts to load Windows that why it is looking for NTDLR. Normally it should boot from your DVD and use the grub boot loader of Ubuntu. My first thought is that you have to verify the boot sequence in your BIOS again. Check whether you can boot from another DVD or CD, e.g the Windows CD.

Are you sure that old computer has a DVD and not a CD? Try to read the content of the dvd using XP.

Another problem could be the DVD, maybe something went wrong during burning the disk, how did you burn that DVD? It could be that you created somehow a windows bootable DVD.

---

### Post by Mazaman on 2011-05-13
I think I know what i did wrong.  I burned the ISO to a DVD and did not use the proper software to make the ISO file to a "CD"

That was it!   I knew I did something stupid!


Thank you all.  The orblem was resolved.  Thank you and kudos to everyone.

I will be lurking! :)

---

### Post by philinux on 2011-05-13
> **Mazaman said:**
> I think I know what i did wrong.  I burned the ISO to a DVD and did not use the proper software to make the ISO file to a "CD"
Could be. It needs to be burned as an "Image File".

---

