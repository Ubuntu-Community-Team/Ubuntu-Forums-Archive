---
title: "HOW-TO : Install &quot;file.application&quot; (ClickOnce, Microsoft)"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by emisoundsmachine on 2011-01-20
How do I install a windows program that is using ClickOnce installation? 
[http://en.wikipedia.org/wiki/ClickOnce](http://en.wikipedia.org/wiki/ClickOnce)

I can't use wine because the file extension ended with ".application".

---

### Post by TechWiz2100 on 2011-01-20
Maybe if you install the app on a windows machine and pull the files into your wine directory and set it up that way, it might work. You might also be able to have Firefox in Ubuntu run the wine app with a little more tweaking.

---

### Post by emisoundsmachine on 2011-01-20
I've tried to but, the application itself didn't install .exe on c:\program files, its hidden somewhere which i was unable to locate on my c drive.

It's a small midi application.

[http://midifilemapper.codeplex.com/releases/view/55757](http://midifilemapper.codeplex.com/releases/view/55757)

---

### Post by TechWiz2100 on 2011-01-21
The Application file is actually an XML document

The file you are looking for is called "MidiFileMapper.exe" so you can probably search for that on your computer. Its supposed to be in a directory that ends with "Application Files\MidiFileMapper_0_4_34_0\" or whatever version you are using. Try looking around in your AppData folder if you have Vista or higher or Application Data in WinXP and earlier.

---

