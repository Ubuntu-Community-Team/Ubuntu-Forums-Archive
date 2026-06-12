---
title: "Help with Grub Rescue"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by FormatSeize on 2011-04-19
What I have done may have been incredibly stupid, but I'll see if I can get some help anyway. 

I've been using Ubuntu for about two years now, and I recently installed Maverick Meerkat alongside Slackware on a computer that I recently built. I wanted to go back to 9.04, but all of a sudden the computer wouldn't boot from the live CD, but rather just kick into the grub splash screen. 

Thinking I was clever (I'm not), I ran a command from the terminal, which I will not post here (it's pretty bad) that would delete the entire filesystem. And now I'm stuck.

When the computer comes on, it's a screen that says "error: file not found grub rescue>_". I've Googled this a thousand times, but I couldn't find a situation like mine. The other situations I found all involved people that could either boot back into Windows (which I don't have), or they are able to run Ubuntu from the live CD, which doesn't happen for me. 

None of the familiar commands that I know are recognized, except for ls, which reveals the following:
```
ls
hd0 (hd0,msdos5) (hd0,msdos3) fd0
```
 
I also tried the set command, but it didn't reveal anything useful for me to get anywhere with my level of knowledge. So I came for help.

Any ideas and suggestions are welcome.
 
Thanks.

---

### Post by coffeecat on 2011-04-19
Let's check one thing for starters.

> **FormatSeize said:**
>  but all of a sudden the computer wouldn't boot from the live CD, but rather just kick into the grub splash screen. 

This sounds like a BIOS issue. Go into your computer's BIOS and check the boot order. In order to troubleshoot this problem you are going to need to boot either a live CD or a live USB. Does your BIOS support booting from USB?

Also...

> **FormatSeize said:**
>  I wanted to go back to 9.04,

Do you know that 9.04 is no longer supported?

---

### Post by FormatSeize on 2011-04-19
> **coffeecat said:**
> Let's check one thing for starters.
 
 
 
This sounds like a BIOS issue. Go into your computer's BIOS and check the boot order. In order to troubleshoot this problem you are going to need to boot either a live CD or a live USB. Does your BIOS support booting from USB?
I do have it set to boot first from the CD ROM. I think that it's possible to boot from a USB, but I haven't tried it yet. There's an option for it, but it's not on the same menu as the boot devices, which are the hard disk, CD ROM, and floppy drive. 
I've just started searching around about a live USB and how to make one. I can't use my computer at home, so I'm going to gather as much information as I can while here at work and throw everything I can at this problem (in a more responsible manner, of course).
 
 
> **coffeecat said:**
> Do you know that 9.04 is no longer supported?
I can't say that I knew that, but at the same time I'm not exactly sure what the even means. Supported by what? I've seen the phrase "no longer supported" here and there, but I figured it was for people running systems much more important than their home computer.

---

### Post by leviathan8 on 2011-04-19
Which filesystem have you exactly deleted? The Slackware's partition or Ubuntu? If you've deleted the Slackware's partition, there might be a hope for you. Assuming that you still have that Ubuntu installed on your system, boot off the LiveCD and follow some easy steps.

First, determine where your Ubuntu partition is, with the help of "sudo fdisk -l". According to your experience, I believe you know how to work around with these  tools.

Mount the partition containing the Ubuntu installation:

```
sudo mount /dev/sdXY /mnt
```
*the X is the device designation*
*the Y is the partition number*
[SIZE="1"]example: sound mount /dev/sd**a9** /mnt[/SIZE]

Then simply run:

```
sudo grub-install --root-directory=/mnt /dev/sdX
```
*yet again, the X is the device designation*
[SIZE="1"]example: sudo grub-install --root-directory=/mnt /dev/sd**a**[/SIZE]

Reboot, and once you're in Ubuntu (of course if you managed to fix it), run "sudo update-grub".

---

### Post by mikechant on 2011-04-19
> I've seen the phrase "no longer supported" here and there, but I figured it was for people running systems much more important than their home computer.

"Not supported" means no security updates, particularly to things like your browser. The longer you run unsupported the more vulnerable you become to exploits that could (e.g.) steal your credit card data, use your PC for spamming etc.

The risks are much lower for Linux than Windows for various reasons which are constantly argued about (Linux less popular = less of a target vs Linux inherently more secure etc.). But it's still a risk.

For many people who aren't bothered about constantly upgrading it's a good idea to get onto an 'LTS' (long term support) release of Ubuntu, e.g. 10.4 (Lucid) gets 3 years support instead of 18 months, same with 12.4 etc.

If you really want to stay on an old release (e.g. newer releases don't work on your hardware) it would be a good idea to at least manually upgrade to a current browser version and keep it up to date. This would probably cover most of the most likely exploits.

---

### Post by coffeecat on 2011-04-19
> **FormatSeize said:**
> I do have it set to boot first from the CD ROM. I think that it's possible to boot from a USB, but I haven't tried it yet. There's an option for it, but it's not on the same menu as the boot devices, which are the hard disk, CD ROM, and floppy drive. 
I've just started searching around about a live USB and how to make one. I can't use my computer at home, so I'm going to gather as much information as I can while here at work and throw everything I can at this problem (in a more responsible manner, of course).

If there is a setting for booting from USB, you might find this page useful:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The app usb-creator-gtk is "startup disk creator" in the System > Administration menu. There's one thing with this you need to be aware of - a bug. Because of syslinux incompatibilities between versions you need to use the 10.04/Lucid version of usb-creator-gtk to write a 10.04 ISO and the 10.10/Maverick version of usb-creator-gtk to write a 10.10 ISO.

If you want to use unetbootin you can install it from the repositories. Or there's the Windows app usb-creator.exe which you can find in the ISO if you mount it.

---

### Post by FormatSeize on 2011-04-20
> **leviathan8 said:**
> Which filesystem have you exactly deleted?
Apparently, neither. When I do the ls command on the partitions, I get the following.
```
ls (hd0,3)/
error: unknown filesystem
 
ls (hd0,5)
./ ../ var/ dev/ home/ proc/ sys/
```
> **leviathan8 said:**
> The Slackware's partition or Ubuntu? If you've deleted the Slackware's partition, there might be a hope for you.
I think that (hd0,3) is Slackware's partition, and I can see that the (hd0,5) partition is Ubuntu's. To my dismay, the /boot/ directory is not there to follow the instructions given elsewhere on this forum. I looked in the other directories for the /boot/grub directory, but it wasn't in any of thos either.
> **leviathan8 said:**
> Assuming that you still have that Ubuntu installed on your system, boot off the LiveCD and follow some easy steps.
I'm unable to boot from the LiveCD as well. It goes directly to the "error: file not found" and then goes into the grub rescue mode. Could it be that it can't boot anything because the /boot/grub files are missing?
 
 
EDIT: And what the heck is "ELF magic"? I was guessing at things and inputting commands hoping to stumble on something, and I got an error that contained that phrase. I know I'm not the most computer savvy person in the world, but it's rather jarring when I am stuck, in a command prompt with no graphical interface and the computer decides to start talking about elf magic.

---

### Post by leviathan8 on 2011-04-20
As suggested before, you could also try booting off a flash drive (implying that your BIOS supports it). Go to a friend, and use UNetbootin to write a Ubuntu .iso image corresponding to your installed version, then try reinstalling GRUB. 
If this still doesn't work, there may be an ultimate method, but I **strongly** suggest that you do not do it, unless there will be no other options to solve the problem. I am no expert in Linux, but I've encountered a lot of problems with GRUB, and hopefully solved them. 

First, burn a Puppy Linux ([download link]("http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-5.2.5/lupu-525.iso")) live image onto a CD, backup everything valuable on other partitions (but not Slackware's nor Ubuntu's). Then grab a copy of Hiren's Boot CD ([download link]("http://www.hirensbootcd.org/files/Hirens.BootCD.13.2.zip")), and yet again, burn it on a CD. Boot GParted from the Partitioning tools, and delete both Linux partitions. Then proceed reinstalling your favorite operating system.
[SIZE="3"]
But **please, DO NOT do this YET. ** As mentioned before, I'm no expert, therefore I cannot guarantee this will work. **PLEASE** let this be the ultimate method.[/SIZE] 

Until then, you can wait for some help from others, or consult the following pages:
[GRUB2 HowTo]("https://help.ubuntu.com/community/Grub2")
[GrubHowTo]("https://help.ubuntu.com/community/GrubHowto")
[GNU GRUB man]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall")
[SuperGrubDisk]("http://www.supergrubdisk.org/index.php?pid=12")

Oh, and, yes, Executable Linkable Format (ELF), as the name suggests, is the Linux file format of executables and object files (including the kernel and kernel modules). This also shows up when booting my Debian.

---

### Post by FormatSeize on 2011-04-20
> **leviathan8 said:**
>  
If this still doesn't work, there may be an ultimate method, but I **strongly** suggest that you do not do it, unless there will be no other options to solve the problem. I am no expert in Linux, but I've encountered a lot of problems with GRUB, and hopefully solved them. 
 
First, burn a Puppy Linux ([download link]("http://distro.ibiblio.org/pub/linux/distributions/puppylinux/puppy-5.2.5/lupu-525.iso")) live image onto a CD, backup everything valuable on other partitions (but not Slackware's nor Ubuntu's). Then grab a copy of Hiren's Boot CD ([download link]("http://www.hirensbootcd.org/files/Hirens.BootCD.13.2.zip")), and yet again, burn it on a CD. Boot GParted from the Partitioning tools, and delete both Linux partitions. Then proceed reinstalling your favorite operating system.
 
[SIZE=3]But **please, DO NOT do this YET. **As mentioned before, I'm no expert, therefore I cannot guarantee this will work. **PLEASE** let this be the ultimate method.[/SIZE] 

I'm not going to try this method quite yet, but I'm trying to download the CDs so that I have them. The Puppy Linux went over fine, but when I try to download Hiren's Boot CD, the links to download it all redirect elsewhere. Is there someplace else I could get it or something similar?
 
EDIT: I got it to download, but it is a zip file. Will it be recognized when I try to use it?

---

### Post by leviathan8 on 2011-04-20
> **FormatSeize said:**
> I'm not going to try this method quite yet, but I'm trying to download the CDs so that I have them. The Puppy Linux went over fine, but when I try to download Hiren's Boot CD, the links to download it all redirect elsewhere. Is there someplace else I could get it or something similar?
 
EDIT: I got it to download, but it is a zip file. Will it be recognized when I try to use it?

You have to unzip the file to obtain the .iso image. You can't just burn a zip on a CD. :P

---

### Post by FormatSeize on 2011-04-21
I've tried everything. Puppy Linux wouldn't boot, I just got the grub rescue prompt again. Hiren's Boot CD did the same thing.
 
I think all hope is lost now.

---

### Post by leviathan8 on 2011-04-21
That seems pretty horrible. Have you tried booting with a USB flash drive? Same result? Sadly my knowledge reaches only to this extent, so I am afraid I can no longer help you. Keep the thread bumped so others might help you. Good luck.:KS

---

### Post by FormatSeize on 2011-04-21
> **leviathan8 said:**
> That seems pretty horrible. Have you tried booting with a USB flash drive? Same result?
I haven't tried booting from the USB yet. I don't have admin rights here on my computer (and no, it's not because I am capable of destroying a system:D), so I can't install any software to make a bootable USB. I do have a couple laptops here at my desk that I can take home, so I *could* try to do the Try Ubuntu Without Installing option and make a bootable CD from the Gnome desktop, and boot from there. 
It's a little risky though, and I'm not sure whether or not you need admin rights for Windows to do the Try Ubuntu Without Installing Option. On one laptop, I can't log in without being plugged in (with a wire) to the network, and on the other I can do most things, but I'm not sure how far that goes as to getting to the gnome desktop to make a boot disk. 
 
But it's going to be the last feasible attempt that I have, so I'm not completely out of options. I am hoping for the best.

---

### Post by drs305 on 2011-04-21
From the grub rescue prompt, if you type the following do you see a lot of *.mod files. And if you run the second do you get a return for grub.cfg. And finally, for the third, do you see the kernel and initrd files?

```
ls (hd0,5)/boot/grub  # Lots of *.mod files?
ls (hd0,5)/boot/grub/grub.cfg # Does it find grub.cfg
ls (hd0,5)/boot # Do you see "vmlinuz..." and "initrd.img..." files?
```

---

### Post by FormatSeize on 2011-04-21
> **drs305 said:**
> From the grub rescue prompt, if you type the following do you see a lot of *.mod files. And if you run the second do you get a return for grub.cfg. And finally, for the third, do you see the kernel and initrd files?
 
The (hd0,5)/boot is not on there at all. There is only
```
./ ../ var/ home/ proc/ sys/
```
 
The /boot directory got missing somehow.

---

### Post by drs305 on 2011-04-21
> **FormatSeize said:**
> The (hd0,5)/boot is not on there at all. There is only
```
./ ../ var/ home/ proc/ sys/
```
 
The /boot directory got missing somehow.

Ah, I didn't realize from the previous post that those were the *only* directories you had.

The only restoration solution I can offer would be if you could find some way to boot the LiveCD, chroot into your Ubuntu partition, and then install the kernel and grub-pc. Even then I'm not sure it would produce all the necessary files.

The other option, if you could find a way to boot the LiveCD or a rescue CD such as SystemRescue CD, would be to mount your sda5 and copy the /home or /home data files and reinstall the OS.

---

### Post by rosencrantz on 2011-04-21
Are you sure your LiveCD is working, e.g. did you ever try it on a different system?
Sometimes people just burn the ISO file on a CD, which results in a non-bootable data CD containing a single .iso file and not a file system.
Make sure you *open* the .iso image with a burning app and then burn it.

---

### Post by FormatSeize on 2011-04-21
> **rosencrantz said:**
> Are you sure your LiveCD is working, e.g. did you ever try it on a different system?
Sometimes people just burn the ISO file on a CD, which results in a non-bootable data CD containing a single .iso file and not a file system.
Make sure you *open* the .iso image with a burning app and then burn it.
The LiveCD is how I got it installed in the first place. But just in case (I've had LiveCDs stop working in the past), I burned a new one and tried that, to no avail. 
 
I've even gone as far as to try to reinstall different Linux OSes that I have (Fedora, Solaris, and Slackware) and none of those want to work either. It's like it has a mind of it's own (to my knowledge, on Excel has a mind of it's own) and all it wants me to do is rescue grub.
 
But there is no code for 
```
/boot/grub=dead. move on.
```

---

### Post by drs305 on 2011-04-21
Can you run *any* kind of self-booting CD from the drive? (Game, Audio, etc)  At least you would know that the BIOS boot order is set correctly if you can get a CD to run.

---

### Post by FormatSeize on 2011-04-23
First, I would like to say thanks to everyone for all their help and support. My machine is up and running now, but the source of the problem, as I have found, is much different than I thought it was.
 
> **drs305 said:**
> Can you run *any* kind of self-booting CD from the drive? (Game, Audio, etc) At least you would know that the BIOS boot order is set correctly if you can get a CD to run.
No. It's wierd, though.
 
I built this computer and the drive came with no OS at all, and it has a DVD ROM drive and a CD ROM drive. For whatever reason, Live CDs would only boot on the DVD ROM drive. Okay. So I installed Slackware, and Ubuntu 10.04. Then I upgraded to Ubuntu 10.10, and that's when (I know this now, and I didn't know this when I started this thread) my DVD drive stopped working. It wasn't being recognized anymore at all. 
 
So that means that any of the bootable CD options put forth in this thread would have worked, but I didn't know that my DVD drive, the only one that would boot anything outside of the USB drive, wasn't working. I ended up creating a bootable USB using a LiveCD at work, and it worked just fine. Then, upon installing 10.10, the DVD drive is not working.
 
When I use lshw - c disk, it shows up there. It also shows up when I do udisk --dump. It shows up in Nautilus, too. But I can't get it to work otherwise, and that's why I had this problem for longer than I should have had it. 
 
I've done search after search after search, but I can't find any command that works. The only thing I ever get is 
```
/dev/sr0: unknown device
```
 
I know this is another topic for another thread, but why is it that every part of the system knows that it's there up until I try to mount it or use it?

---

### Post by leviathan8 on 2011-04-27
I'm very glad that you solved the problem. :D
Regarding the DVD ROM issue, this looks like rather a hardware problem to me. But I might be wrong, so please try booting off of a LiveCD with your USB drive at check whether the DVD ROM is being recognized and working well. You can also make use of "palimpsest" (run it in a terminal) and acquire data about your DVD and CD ROM for further information. Have a nice day. :KS

---

