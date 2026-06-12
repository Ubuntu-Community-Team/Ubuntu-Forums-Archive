---
title: "CD booting"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by mlempenau on 2011-04-16
I need to boot from a CD but for some reason I can't.  I made a boot cd that is supposed to work with windows and ubuntu but it will not work.  It works on my laptop with xp.  My computer is using the latest version of ubuntu with all upgrades.  My ubuntu load was done from a clean disk and then I added a windows partition.  I'm beginning to think my bios may be at fault.  When I boot using the boot menu it tries to boot from the cd but then stops and goes to the hd.  When I go into bios and disable all hardrives it give me an error ... boot disk failure, insert system disk and press enter.  I have used several different boot cds and they all work on my xp system but give me the same error on ubuntu.  I'm stumped.

---

### Post by Frogs Hair on 2011-04-16
In my bios there is an option to boot from disk and I set this as boot option when I built my computer in order to install the operating system. Once set it now boots automatically from disk.

Bios screens look very different from one computer to another but offer similar options . It won't hurt to take a look around just be careful .

---

### Post by richaoj on 2011-04-16
Do you hear the CD drive spinning up?  It could be a drive failure?  Perhaps you should try loading and booting from USB.  It's much faster anyways.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Antarctica32 on 2011-04-16
Sometimes I get a similar problem when I use a CD-RW on a really old drive.

---

### Post by Blasphemist on 2011-04-16
I agree with Antarctica32. Have you ever booted this machine from CD? If so, try that CD. If not and since the CD works on other machines, you may be best off to follow the advise to put your iso on USB and use that.

---

### Post by mlempenau on 2011-04-17
The cd is working.  My bios is set properly.  Downloading ubuntu is not what I need.  I need to boot paragon, a partition s/w program but it does not run in ubuntu.  It is windows based.  But my system will not boot either to a ubuntu formated boot disk or a windows formated boot disk.  It will boot to a windows install cd and a ubuntu install cd.  Have no idea why but this is the way it is.

---

### Post by Blasphemist on 2011-04-17
There are certain requirements for media that allow any system to that media as bootable. A windows or ubuntu cd meet these requirements as do many utility packages including those from paragon.

The ubuntu live cd includes gparted for partitioning. Windows has it's own utilities in its cd. I'd recommend you use one of them or better yet use this. It is a very good and often recommended package of utilities.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by mlempenau on 2011-04-20
When I make a boot disk in ubuntu (cd or usb) my computer boots fine to a command line.  But when I try to boot from a windows boot disk (cd or usb) it will not work.  Is there any way to get my ubuntu computer to boot to a windows command line?

---

### Post by Blasphemist on 2011-04-20
If I'm following everything right, windows is not yet installed right? If that is the case, the only windows command line you could boot to is using a windows boot or installation disk. 

I'm not sure what task you want to accomplish. When you boot to a cd or usb, you aren't running the boot processes on the hard disc. What is loaded from the cd or usb boot process are programs that determine what you'll see on the screen, command line or graphics, and what environment you get to execute programs. All of this happens whether or not anything is installed on the hard drive. I think you want to do something to the windows partition you created from your messages. If you boot to the system rescue cd, you'll have tools that can see and act on that windows partition. [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

If you'd like, please describe just what you want to do and we might be able to offer better help.

---

### Post by mlempenau on 2011-04-20
Thanks for helping.  I'm sure there is something here that I can learn.  I have a ubuntu load that is way to big to backup the normal way.  Even if I did it that way I would still not like it.  I want to make a copy of the partition.  Since I have a very good program that I paid money for and am familiar with I wanted to use this program.  The boot disk I made with this program under windows will not let me boot to it now with ubuntu installed.  This led me to the question why?  So I made several boot disks to experiment with which created more questions.  There are most likely other ways to do this, but I am now very interested to understand what is going on.  Possible close to obsession :)!!  Mike

---

### Post by LewRockwellFAN on 2011-04-21
> **mlempenau said:**
>  The boot disk I made with this program under windows will not let me boot to it now with ubuntu installed.  This led me to the question why?  So I made several boot disks to experiment with which created more questions.  There are most likely other ways to do this, but I am now very interested to understand what is going on.  Possible close to obsession :)!!  Mike

How you made the bootable CD or what software is on the HD isn't germane. What is germane is:
1-have you actually booted with it?
2-Have you booted the box you are trying to boot with it now with it in the past?
3-Have you verified the CD itself is in good shape? For instance, don't laugh or punch me out, have you cleaned it and looked for scratches? Have you tested it in another machine since you had this problem?

If you haven't shown otherwise it is quite possible this CD just won't boot this hardware even if it will boot other boxes.

Another possibility: Maybe it is like some problematic bootable CDs I have. To get them to boot I have to enter the bios setup as I boot up, wait a moment, and then exit, changing nothing, and allow it to boot. It I don't do that, they just hang. My theory is that for some reason those CDs are readable more slowly than most for some reason and this gives the bios a little longer to notice they are bootable whereas if I just boot when it doesn't find bootable code on the CD quickly it gives up and tries the HD. Sounds weird, I know, and I welcome a more explicit nuts and bolts explanation of the behaviour but that is how they work and it is consistent.

There are some comments above that sound a bit like you are talking about booting into windows from a CD. I'm assuming that is NOT what you are trying to do but to boot into an independent bootable utility CD. If you DO want to boot Windows from a CD you will need Bart's PE which you will need to look up.

---

### Post by Blasphemist on 2011-04-21
> **mlempenau said:**
> Thanks for helping.  I'm sure there is something here that I can learn.  I have a ubuntu load that is way to big to backup the normal way.  Even if I did it that way I would still not like it.  I want to make a copy of the partition.  Since I have a very good program that I paid money for and am familiar with I wanted to use this program.  The boot disk I made with this program under windows will not let me boot to it now with ubuntu installed.  This led me to the question why?  So I made several boot disks to experiment with which created more questions.  There are most likely other ways to do this, but I am now very interested to understand what is going on.  Possible close to obsession :)!!  Mike

Mike- This does help. You may have seen in these forums discussion of setting bios boot order. In the bios (the first small programs that any pc runs when turned on or reset) a boot order for the devices is set, as are many other things. Normal operation is often that the pc first looks for a bootable hard drive. The reason for this is just that if you want the fastest boot time and you are going to boot the hard drive, it might as well be the first thing tried. If you want to boot to a cd or usb instead of a hard drive, you have to tell the bios to check for a bootable cd or usb before it tries the hard drive.

BIOS is accessed by watching very closely at the very start of turning the pc on or reseting it and looking for the prompt on accessing the bios. It will for a very short time tell you to press F8, F10, F2 or some other key to access BIOS. It depends on what BIOS you have what key will access it. It will bring up a very simple graphics screen with options and instructions. There will be a menu option for boot options. In that menu you can set the order of devices checked for bootable media. Yours needs to be set to access the cd first. Usually at the bottom of the screen it tells you what to do to save changes you've made and exit the BIOS. When you do that it will restart again.

Is it possible that is what is happening to you? Does it seem to even try to boot from the cd? Having Ubuntu on the hard drive will make no difference if the pc is trying to boot to cd first and it finds a bootable cd.

---

