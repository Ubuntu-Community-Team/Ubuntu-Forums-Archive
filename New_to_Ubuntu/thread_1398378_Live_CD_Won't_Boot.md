---
title: "Live CD Won't Boot"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by cwelch on 2010-02-04
Ok, forgive me if this is already somewhere else, but I haven't been able to solve my problem, so... HELP!!

What I have is this:

New HP dv4 with Intel Core i3 (2.13GHz) w/ Intel HD Graphics, 4GB DDR3, 500GB disk, Windows 7 H.P.

Windows admittedly works quite well, but I am anxious to see how well 9.10 runs on this thing!

My problem is that when I tell it to boot from the live cd to check it out, it won't boot! I get the message to pick a language and to try Ubuntu w/o changing anything, install, etc.. Hit enter on Try and it doesn't work. The CD spins and spins and has all sorts of activity, but the screen sits black with the backlight on. I am using the 64-bit version. I have the 32-bit that I use to get files off of infected PCs before reloads at my job and it takes a while to boot, but it DOES boot. This one is not. I saw in another thread where they recommend burning at a slower rate, but this hasn't effected the x86 version at all, and it is the same burner making the ISO disk. I haven't tried the x64 in another box, but I don't think it'll be the same result though. No other x64 to test it. Any ideas? I'm liking 7 so far, but IT IS STILL WINDOW$ and if 9.10 is kicking as much butt as it is on my 1.73 2GB single core, I can't wait to see it on this! :D

---

### Post by BT1 on 2010-02-04
One of the reasons I like using USBs.

They're right it looks like. If you're sure that your processor supports 64 bit software and that's as far is you get, it seems something past that point is corrupted, or perhaps you aren't waiting long enough for the info to come off the CD (CD is slower than USB drive).

You have to remember that just because one .iso burns fine, it doesn't mean the next won't burn the same. There may be a spec on the CD that corrupts a loading file, or the writer may burp and throws off the laser, lots of variables. Writing the disk at a very low rate often ensures it is not the Laser that is messing up. But also make sure the .iso is fine by doing an md5 checksum (there's free programs for windows that do this).

IF both of those are working fine, the CD should work fine. Get a thumb drive with at least 1 gig and "unetbootin" (google it) and burn the .iso to the thumb drive. It will also lag less than the CD and give you a closer experience to what it is like on the hard drive.

Hope it works out for you.

---

### Post by BT1 on 2010-02-04
P.S. for the "desktop" experience, 32 and 64 work mostly the same when it comes to speed of the desktop. I use both on a daily basis and the only real advantage you experience is when you unpack zipped folders and stuff that requires heavy data processing. For everything else (like clicking desktop icons and seeing it load faster) there is only a *slight* difference. That is usually lost on the average desktop user though. It's when you use KernelCheck and compile your own kernel (easier than it sounds) that your hair gets blown back by how fast it moves. Anyways...

Again, hope it works out for you :)

---

### Post by mesuhas_sit on 2010-02-04
I faced the same issue while booting from the USB.... Any body out there please help

Thanks

---

### Post by rajeev1204 on 2010-02-04
> **cwelch said:**
> Ok, forgive me if this is already somewhere else, but I haven't been able to solve my problem, so... HELP!!

What I have is this:

New HP dv4 with Intel Core i3 (2.13GHz) w/ Intel HD Graphics, 4GB DDR3, 500GB disk, Windows 7 H.P.

Windows admittedly works quite well, but I am anxious to see how well 9.10 runs on this thing!

My problem is that when I tell it to boot from the live cd to check it out, it won't boot! I get the message to pick a language and to try Ubuntu w/o changing anything, install, etc.. Hit enter on Try and it doesn't work. The CD spins and spins and has all sorts of activity, but the screen sits black with the backlight on. I am using the 64-bit version. I have the 32-bit that I use to get files off of infected PCs before reloads at my job and it takes a while to boot, but it DOES boot. This one is not. I saw in another thread where they recommend burning at a slower rate, but this hasn't effected the x86 version at all, and it is the same burner making the ISO disk. I haven't tried the x64 in another box, but I don't think it'll be the same result though. No other x64 to test it. Any ideas? I'm liking 7 so far, but IT IS STILL WINDOW$ and if 9.10 is kicking as much butt as it is on my 1.73 2GB single core, I can't wait to see it on this! :D

When the live cd comes to the boot options menu, press F6 and remove the quiet and splash words from the line you see.

Then press enter and wait.It will show you whats happening.Post that here.

---

### Post by BT1 on 2010-02-04
> **mesuhas_sit said:**
> I faced the same issue while booting from the USB.... Any body out there please help

Thanks

Then its the .iso, or it didn't write to the USB right. Those two possiblities are all that comes to mind in your case.

---

### Post by N00bDud3 on 2010-02-04
I am having a similar problem to this with the x86 9.10 LiveCD. I am trying to install 9.10 onto a Dell B110, and it won't boot, it just goes to a blinking cursor after I select Try Ubuntu. I know the CD is good because it installed on my Acer laptop no problem just a few minutes before, and after I waited 20mins for the Dell to boot I tried it in my laptop again and it booted the LiveCD. I'm posting this here because I'm not sure if it requires a new thread.

---

