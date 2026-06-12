---
title: "Applying Compiz Fusion to the desktop"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Creed E356 on 2009-01-21
OK, so I figure this belongs in beginner talk. 

I have been using Ubuntu for a while now and I find that anything I have to do on it is pretty easy. I have run into a problem while trying to get the Compiz Fusion effects on my desktop. I have installed the software and have been playing around with the settings, but these settings appear to only apply to the CompizConfig manager. If I have flame effects set and I close the manager, then it will go up in flames like it's supposed to. But, if I open any window that's not Compiz manager, nothing happens and the normal Gnome effects are still there. I have read several pages on the internet to double check that I have installed Compiz correcly. Is there any apply button or anything that I've missed so that I can get my settings to run on all windows? I use the 8.10 version of Ubuntu and use the NVidia accelerated driver (117) if that's any help. If anybody can help me that would be awesome.

---

### Post by gettinoriginal on 2009-01-21
First, go to System, Preferences, Appearance, Visual Effects, and make sure that Extra or Custom is selected.  That shows that compiz is enabled.  After that, open a terminal and copy/paste the following:
```
compiz --replace
```
That should fix the problem.  :p

---

### Post by 2hot6ft2 on 2009-01-21
> **Creed E356 said:**
> If I have flame effects set and I close the manager, then it will go up in flames like it's supposed to. But, if I open any window that's not Compiz manager, nothing happens and the normal Gnome effects are still there.

You can set it for which windows it will work for. Highlight the burn effect and select edit then Where it says "Windows Match" click on the + sign at the end. Then click on the Grab button and it will give you crosshairs which you can click on the title bar of an app and it will fill in the value for you. Like the to of an open folder would make it apply to all folders and nautilus actions...like file transfers..etc..

---

### Post by Creed E356 on 2009-01-21
Sorry, tried the Terminal way and nothing happened. Came up with this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Creed E356 on 2009-01-21
Wait, do I need XGL?

---

### Post by stchman on 2009-01-21
> **Creed E356 said:**
> OK, so I figure this belongs in beginner talk. 

I have been using Ubuntu for a while now and I find that anything I have to do on it is pretty easy. I have run into a problem while trying to get the Compiz Fusion effects on my desktop. I have installed the software and have been playing around with the settings, but these settings appear to only apply to the CompizConfig manager. If I have flame effects set and I close the manager, then it will go up in flames like it's supposed to. But, if I open any window that's not Compiz manager, nothing happens and the normal Gnome effects are still there. I have read several pages on the internet to double check that I have installed Compiz correcly. Is there any apply button or anything that I've missed so that I can get my settings to run on all windows? I use the 8.10 version of Ubuntu and use the NVidia accelerated driver (117) if that's any help. If anybody can help me that would be awesome.

Compiz is installed and turned on by default since Hardy.  What kind of Nvidia card do you run?

If you enable the restricted driver Compiz will function as it should.

---

### Post by Creed E356 on 2009-01-21
I run a NVIDIA GeForce GE 6150

---

### Post by Creed E356 on 2009-01-21
I'm trying out 2Hot's suggestion.

---

### Post by Creed E356 on 2009-01-21
2 hot's window grab worked, thats all I had to do. But is there a way I can just apply to all windows?

---

### Post by Creed E356 on 2009-01-21
alright, figured it out. Thanks guys!

---

