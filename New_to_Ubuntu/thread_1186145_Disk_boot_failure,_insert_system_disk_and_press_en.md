---
title: "Disk boot failure, insert system disk and press enter ..."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Uubnewb on 2009-06-13
Disc boot failure
Hi,

I just installed Ubuntu 9.04 64-bit. When I restarted after the installation process Ubuntu wouldn't load up; instead I got a "Disc boot failure" message asking me to put in the boot disk.

At first it was the Windows installation I have on another partition that is causing the problem, so I deleted the Windows partition and re-installed Ubuntu. Unfortunately that did nothing to fix the problem. I still get the same message even though I now only have one operating system, namely Ubuntu 9.04, on my computer.

I am currently using the install disc as a live CD (thank goodness for that option), but I'm sure you'll agree that I cannot continue using this method indefinitely.

Your help will be greatly appreciated.

PS: I posted the same question in another part of the forums.  I know I shouldn't post the same question more than once, but I can't find an answer and this is a rather urgent matter for me.  I hope you will understand.

---

### Post by keplerspeed on 2009-06-13
Sounds like your BIOS is set to only boot from cd-rom drive.

So restart, just as the computer starts up, start BIOS menu by pressuing the required key (f10, delete or something). Then find boot options, and make sure that booting from hard disk is set as number 2, with cd-rom set as 1.

As you have explained, I would assume that you have the boot option only set for cd drive. This means that when you restart your computer, BIOS ONLY looks for cd's in the cd drive.

---

### Post by Uubnewb on 2009-06-13
That was my first thought as well, but when I checked the boot priorities I found nothing wrong.

I am going to try a different install option (something other than manual install), and when I restart, I'll check the BIOS again (just to make sure) and then I'll report back.  In the meantime, If you can think of anything else that might help, please let me know.

---

### Post by Uubnewb on 2009-06-13
Please see my latest reply [here]("http://ubuntuforums.org/showthread.php?p=7449091#post7449091").

Thank you.

---

