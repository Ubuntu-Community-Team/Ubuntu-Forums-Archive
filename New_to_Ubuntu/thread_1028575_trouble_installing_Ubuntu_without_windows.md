---
title: "trouble installing Ubuntu without windows"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by killbydemons on 2009-01-02
I just want to do a clean install of Ubuntu on a pc at home.  I formatted the hard drive using the windows install disk, to take off the windows installation, then deleted the partition.  I burned the Ubuntu 8.10 iso to a dvd, and i'm trying to boot from it but i can't.  Any suggestions? I have flash drives large enough to hold ubuntu; can i boot from that maybe?

---

### Post by ibizatunes on 2009-01-02
Have you check that your BOIS is set to boot to cd? When your burnt your CD did you burn a ISO image file?

---

### Post by handydan918 on 2009-01-02
> **killbydemons said:**
> I just want to do a clean install of Ubuntu on a pc at home.  I formatted the hard drive using the windows install disk, to take off the windows installation, then deleted the partition.  I burned the Ubuntu 8.10 iso to a dvd, and i'm trying to boot from it but i can't.  Any suggestions? I have flash drives large enough to hold ubuntu; can i boot from that maybe?

TRy burning to a cd-r. Not a dvd, or a cd-rw. That should take care of it. If not, a thumbdrive can be made to work with unetbootin.

---

### Post by donkyhotay on 2009-01-02
I would check your BIOS first, I have a computer with a really lame bios that will automatically recognize and boot from a windows install CD but won't boot from any other CD unless I hold down the 'c' key during POST (it's a toshiba satellite laptop BTW). It's possible you might have something similar as well.

---

### Post by -kg- on 2009-01-02
> **donkyhotay said:**
> I would check your BIOS first, I have a computer with a really lame bios that will automatically recognize and boot from a windows install CD but won't boot from any other CD unless I hold down the 'c' key during POST (it's a toshiba satellite laptop BTW). It's possible you might have something similar as well.

Wow, you must have an old one!  I have a Toshiba Satellite and have no such problems (I am presented the option to press F-12 at posting time to select the boot device, otherwise it boots to the first hard drive).

It *might* be that your problem is that you need to install the Live CD version to a CD rather than a DVD, unless you downloaded the DVD version for the language pack support.  I don't know if the DVD version is a bootable Live CD, though.  I know the Alternative Install version isn't.

> I formatted the hard drive using the windows install disk, to take off the windows installation, then deleted the partition.

You really didn't have to do all that.  You could have just deleted the Windows partition and it would have done the same.

---

### Post by donkyhotay on 2009-01-02
yes my laptop is really old (about 7-8 years now). It's a pretty good laptop but I (obviously) don't like how the BIOS works. It isn't really a problem, just the way it's designed, but it's a pretty stupid design having to push certain keys during POST to make a single (one-time) modification to the BIOS rather then just accessing the CMOS menu and configuring it the way I want to permanently.

---

### Post by killbydemons on 2009-01-02
Well it's not a problem with the boot priority or BIOS..the computer is a couple years old, and it was my mine until recently, so i know it works.

I guess it makes sense that the Live CD version of Ubuntu would work best if burned to a cd; i'll try that.

---

### Post by ajgreeny on 2009-01-02
I have used a DVD-RW for a ubuntu live CD before now without a problem, except for the difficulty of getting it to burn the correct way.  Brassero does not appear to offer the option of burning a CD image to a DVD, but k3b does, and that has been my choice of cd burner for a long time now, though gnome is my chosen desktop.

---

### Post by egalvan on 2009-01-02
> **donkyhotay said:**
> yes my laptop is really old (about 7-8 years now). It's a pretty good laptop but I (obviously) don't like how the BIOS works....

Have you checked to see if an update is available?

---

### Post by donkyhotay on 2009-01-02
> **egalvan said:**
> Have you checked to see if an update is available?

Yes, there is an update but it doesn't give me a CMOS menu. This is getting a little off-topic from the original issue though and I seriously don't care about fixing it, I'm just going to be more careful if I ever buy another laptop. The only reason I mentioned it is as a possible cause of killbydemons original posted problem.

---

### Post by amaroKer on 2009-01-02
You can burn to whatever media you wish using this method.

1) Browse to image file (*.iso) you wish to burn in Nautilus (default file browser in GNOME).

2) Right-click and select "Write to Disc..."

3) Select appropriate options and click "Write" button.

I have successfully booted CD ISO's on DVD's multiple times with this method.

---

### Post by killbydemons on 2009-01-03
Yeah it's all good. Turns out i was just *copying* the .iso to the boot media, but I used ImgBurn to burn the .iso to a cd, it's installing as I write this :)

problem solved.

---

### Post by 3ventic on 2009-05-20
I have this problem now. I'm trying to install ubuntu from a DVD-R which has ubuntu-9.04-desktop-i386.iso in it + a few ET (Wolfenstein: Enemy Territory) files.

I'm thinking is it possible to boot it from DVD-R? It doesn't fit to my CDs.

---

### Post by halitech on 2009-05-20
if you have the iso files on the dvd it won't boot. The iso needs to be burned as an image so you get multiple files on the disk, not just a big iso file

---

