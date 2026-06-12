---
title: "whats wrong with my installation?"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by natman on 2009-06-21
Hi,
I have Kubuntu 904 installed and it works about 95% just perfect. But there are a three weird things.

1: When i press the on button, it tells me ""booting from (hda0,ext3) long number sequence.." this stays there for about 20sec, then i hear a noise ( very like the sound when a cd is in the drive even though its empty ) i also see the drive light flash - then the boot is normal and fast - why??

2: Every so often ( i cant find any pattern ) but when i get to the login screen the scree res. is wrong ( two black borders either side ) if i hit restart X server its back to normal

3: When i go to shut down, it sometimes stall at iterating IDE drive?

Can anyone help?

---

### Post by 3rdalbum on 2009-06-21
> **natman said:**
> 1: When i press the on button, it tells me ""booting from (hda0,ext3) long number sequence.." this stays there for about 20sec, then i hear a noise ( very like the sound when a cd is in the drive even though its empty ) i also see the drive light flash - then the boot is normal and fast - why??

I don't know about the other two problems, but I believe this is reasonably normal. The message you recieve is totally normal. I believe the length of its appearance may be linked to any overclocking you may be doing? I have the same symptom but it does not cause any problems.

The CD drive access is completely normal, everyone has that.

---

### Post by K.Y.A on 2009-06-21
Sometimes changing bios boot order will fix your third problem. You also may want to change your ACPI settings. 

As for screen resolution problem, switching to KDE 4.2 fixed it.

If you have 800mb of disc space to spare, open terminal and type:

```
sudo apt-get install kubuntu-desktop
```

Select GDM when asked. Then, log out and before you log back in, click options >> sessions >> KDE.

Good luck :)

---

### Post by Bucky Ball on 2009-06-21
1/ Have you gone to the BIOS and changed it to boot from your hard drive first again, not the CD, which it would have been set to for booting from the CD to install Ubuntu. :)

---

### Post by K.Y.A on 2009-06-21
Did my suggestion work?

---

