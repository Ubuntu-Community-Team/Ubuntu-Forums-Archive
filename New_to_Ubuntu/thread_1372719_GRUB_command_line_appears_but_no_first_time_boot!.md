---
title: "GRUB command line appears but no first time boot?!"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by cottager on 2010-01-04
I made an Ubuntu install CD for my dad's laptop and Ubuntu booted up flawlessly. Great - I know the CD's fine.

So I put this CD in my coworker's old Dell tower with WinNT or something, and I set the CD to boot first in the BIOS. But it wouldn't, it just booted Windows over and over. So I 'explored' the Ubuntu installation CD in Windows and clicked the 'install' file. And it told me boot from the CD - and a message said it could *help* me boot from the CD. So I clicked OK and after 20 minutes of working on something, it said it was done and I restarted. 

But now I have to press F1 and then I just get a command line that says GRUB

What did I do wrong? 

Thanks for your help!

---

### Post by cenzorrll on 2010-01-04
hmm, it sounds to me like it installed grub onto the MBR. Am I correct in guessing that windows doesn't boot either, just the grub thing? (i haven't ever used the ubuntu cd in windows so i don't know what it does)

this may be a hardware issue, something like this just happened to me on my desktop. my cd drive would spin up and try to read a disk, then boot from the hard drive.  I could read the disk in the OS, but it wouldn't boot.  luckily i had another optical drive lying around and i stuck that in and the cd booted just fine.

if it tries to read the cd for a while (flashing light, you can hear it spin up before anything else shows up) then after a few seconds gives you the grub command line then it's *probably* the cd drive.

if it's possible to boot from an external drive or usb you might try using a usb stick instead (unetbootin can make a bootable one, or if you have ubuntu on another computer nearby there is a utility in there also)

---

### Post by cottager on 2010-01-04
Thanks, you might be right!

The original internal CD drive never worked, so I swapped out another one nearby from an HP tower, and maybe it's not working right. I know little about hardware, either- maybe the CD drive needs to be configured or set up in some way to be used for booting...

Good idea, I'll bring in a USB CD drive and give that a shot.

Come to think of it I did create a bootable memory stick, and it wouldn't boot that either. I know I put the hard drive last on the boot list, and I had the Ubuntu CD *and* the Ubuntu memory stick in and neither would boot.

---

### Post by cenzorrll on 2010-01-04
could be it's an older board and bios, older bioses sometimes don't have an option to boot from usb.  (if you aren't given a "removable media", "USB drive", or "USB cdrom" or anything of the like, then it probably won't boot.

if nobody else can help, then you might try removing the hard drive and placing it in another computer for the initial install and putting it back in afterwards. (then again you could probably just "borrow" the other cd drive of course to check if that's the problem)

---

