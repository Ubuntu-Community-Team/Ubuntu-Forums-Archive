---
title: "Quiet Audio (Audio Range Incorrect)"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Faenar on 2011-06-12
Hi all - I've recently moved off of Windows 7 x64 to Ubuntu 10.04 x64 and am having a bit of trouble with my audio.  I have poured over hours of google searches to no avail.  If I set my audio to 100% it is still quiet (about 60% of what it should be). 

 I have double checked in alsamixer and everything is set to 100% and not MM on any channel.  When I open up the gnome-volume-control panel I can see that on the volume slider bar 100% is not at the extreme right end of the slider (see screenshot)

[IMG]http://i1184.photobucket.com/albums/z340/JuggernautMkIV/Volume_Slider.png[/IMG]

When I slide it past the 100% mark it sounds fine, but as soon as I adjust the volume again it goes back down to that 100% mark which is quite annoying. 

I'm using an HP dv7-4165dx laptop.  Any help would be greatly appreciated!!  I can provide command outputs as needed.

---

### Post by ajgreeny on 2011-06-12
Have you checked volume levels on the apps where you have this problem?  They all have their own volume settings.

---

### Post by 3xp10r3r|X13 on 2011-06-12
To configure everything really detailed, open up your terminal and type:
```

$ alsamixer

```You should get a graphical interface within the terminal, which provides you with the ability to configure everything the way you want it to be.

Which means according to:

[QUOTE=Faenar]
I have double checked in alsamixer and everything is set to 100% and not  MM on any channel.  When I open up the gnome-volume-control panel I can  see that on the volume slider bar 100% is not at the extreme right end  of the slider (see screenshot)
[/QUOTE]

Have a look at (maybe) different sound cards set to different things.

I don't know your system, but I forget from time to time to apply the correct settings for different sound cards.

---

### Post by Faenar on 2011-06-12
> **ajgreeny said:**
> Have you checked volume levels on the apps where you have this problem?  They all have their own volume settings.

I have this issue with all applications including the OS itself (boot in, log off, erros).  The applications are all at max volume as well.

> **3xp10r3r|X13 said:**
> 
Have a look at (maybe) different sound cards set to different things.

I don't know your system, but I forget from time to time to apply the correct settings for different sound cards.

The 2 audio cards I have listed in alsamixer are my onboard sound (all at max) and my HDMI out (also maxed).

---

