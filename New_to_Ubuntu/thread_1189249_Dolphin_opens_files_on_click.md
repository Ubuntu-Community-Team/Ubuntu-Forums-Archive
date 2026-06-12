---
title: "Dolphin opens files on click?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by grenadier32 on 2009-06-16
Is there a way to get Dolphin to not open files when I click on them? I would prefer if it did that on a double-click, not a single click--it makes sense in column mode for directories, but I keep accidentally opening files I don't want to. It's the only thing keeping me from switching to Dolphin from Nautilus.

---

### Post by SuperSonic4 on 2009-06-16
You can press ctrl and click to select a file. That way sucks though, a better way is to open dolphin and go to

Settings -> Configure Dolphin -> Navigation

and select "Double click to open files" and then OK

---

### Post by grenadier32 on 2009-06-16
> **SuperSonic4 said:**
> You can press ctrl and click to select a file. That way sucks though, a better way is to open dolphin and go to

Settings -> Configure Dolphin -> Navigation

and select "Double click to open files" and then OK

I don't see the Navigation section, or anything called that. Are you using the version of Dolphin in Kubuntu 9.04?

---

### Post by SuperSonic4 on 2009-06-16
I'm using KDE 4.3 beta which is probably more to do with it, the version of dolphin I have is 1.2.80

Can you post a screenshot of your dolphin settings? under settings -> Configure dolphin

---

### Post by grenadier32 on 2009-06-16
Sure, here you go. It's version 1.2.1.

---

### Post by ajgreeny on 2009-06-16
I can not believe that they have left that possibility out of the configuration options, but I certainly can't find it!
I don't use KDE any more as it got too tiresome once I realised that gnome could do just about all that KDE can, but generally in a simpler manner.  However dolphin is a dependency of one of the few KDE apps that I do use, so is on my system.

---

### Post by grenadier32 on 2009-06-16
> **ajgreeny said:**
> I can not believe that they have left that possibility out of the configuration options, but I certainly can't find it!
I don't use KDE any more as it got too tiresome once I realised that gnome could do just about all that KDE can, but generally in a simpler manner.  However dolphin is a dependency of one of the few KDE apps that I do use, so is on my system.

From what SuperSonic4 tells me, they're adding it in a later version. It still seems like a dumb oversight though. Like it was only left out because of Not Invented Here syndrome.

---

### Post by SuperSonic4 on 2009-06-16
> **grenadier32 said:**
> From what SuperSonic4 tells me, they're adding it in a later version. It still seems like a dumb oversight though. Like it was only left out because of Not Invented Here syndrome.

I imagine it will be in KDE 4.3's dolphin. Here is my screenie:

[IMG]http://img.photobucket.com/albums/v365/SuperSonic4/Screenshots/dolphin.png[/IMG]


In your version of dolphin you may get single click via [code]System Settings -> Keyboard and Mouse -> Mouse... General: Icons: Double Click to open files and folders.[code]

This will be kde wide and assumes you have system settings installed too (may not be the case in ubuntu - if not my guess would be to check in mouse preferences wherever ubuntu keeps it)

---

### Post by grenadier32 on 2009-06-16
Oh, awesome--that did it. I had to do a bit of poking to find that KDE's system settings can be reached with the systemsettings command, but it worked. Thanks! :)

---

