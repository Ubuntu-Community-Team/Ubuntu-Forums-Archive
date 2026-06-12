---
title: "Virtual Machine ala Mac OSX"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Lrpbpb on 2010-03-29
I would like to know if there exists a program that can do what vmware/parallers (not really sure) does in osx: Display windows/other os's windows as if they were native, not viewing a "mini version" of the os inside a window. Also I want to know how much performance loss there would be, because if it is minimal I would like to finally drop windows!;) 

I know that there is wine, but have heard that many times it doesn't work properly, or is buggy. So I would also like to know if it would be better (performance and aesthetically wise) to have wine or this "integrated vm".

Thanks!

---

### Post by 3rdalbum on 2010-03-29
Virtualbox can do it, as can VMWare. Note that with a virtual machine, you still need a copy of Windows to be installed in the virtual machine.

---

### Post by asmoore82 on 2010-03-29
You are looking for Virtualbox.
It can operate with or without hardware based virtualization and
supports branching Snapshots. There is almost no loss in performance
for regular desktop software and support for 3D graphics is in the works.

---

### Post by prshah on 2010-03-29
> **Lrpbpb said:**
> Display windows/other os's windows as if they were native, not viewing a "mini version" of the os inside a window. 

Yes you can do this. In VirtualBox, when you have your guest OS running, click on Machine-Seamless mode.

If Seamless mode is greyed out, you will have to check for the reason by inspecting the properties of your virtual machine when it is turned off, from the main (selection) screen of VirtualBox.

Please post back if you need more information.

---

### Post by Lrpbpb on 2010-03-29
Thanks for the quick response (usually takes 2+ days for me to get answers). I do have a windows xp install disk. So I guess that virtual box would be better than wine? I would like to understand the pros cons of wine and virtualbox, because they way I see it virtualbox would be better as it is running from xp so no configuration, and wine would be useful if you don't have a copy of windows install disk.

---

### Post by Lrpbpb on 2010-04-07
Just tried it and "seamless mode" is greyed out, how do I change the settings to make it work?
:confused:

---

### Post by marshmallow1304 on 2010-04-08
> **Lrpbpb said:**
> Just tried it and "seamless mode" is greyed out, how do I change the settings to make it work?

You will need to install Guest Additions.  While your VBox session is running, choose Devices->Install Guest Additions.

---

### Post by Paqman on 2010-04-08
> **asmoore82 said:**
> There is almost no loss in performance


That's not quite true. Virtual Machines will consume a lot of resources. Generally you'll need to allocate them a large chunk of your RAM, and they'll consume as much of your processor as if they were running on the actual hardware. If you've got several GB of RAM and a multi-core machine, you might find they run fairly smoothly, if you don't then you'll struggle.

---

### Post by prshah on 2010-04-08
> **Lrpbpb said:**
> Just tried it and "seamless mode" is greyed out, how do I change the settings to make it work?
:confused:

Ensure:

a) Guest additions are installed: as advised, Devices-Install Guest additions

b) Ensure enough RAM memory allotted to Virtual Machine (Min 512MB for WinXP)

c) Ensure enough RAM memory allotted to virtual machine for Video RAM (Min 5MB for WinXP)

If seamless mode is still greyed out after these changes, please check the settings of the virtual machine for a reason (will be displayed in RED).

---

### Post by anewguy on 2010-04-08
Also, if you have downloaded VirtualBox, before you go very far you'll want to check to see if you installed the open-source edition (ose) - I think this is the default in the package manager.  If so, and if you want to be able to use USB devices (besides a keyboard and mouse), you should first download and install the PUEL version - it is not open source, but it is still free.  Only the PUEL version has USB support.

Dave ;)

---

### Post by prshah on 2010-04-08
> **Paqman said:**
> Virtual Machines will consume a lot of resources.

If you've got several GB of RAM and a multi-core machine, you might find they run fairly smoothly, if you don't then you'll struggle.

Not quite. I'm using VirtualBox-OSE on a Fujitu P5010/Single CPU 900Mhz Centrino/1GB RAM, and using it comfortably.

Even when simultaneously using 3~5 other applications such as Compiz, Firefox, OpenOffice, Evolution, Messaging, it remains usable, though response time is a little off.

I've also tweaked the virtualized XP to load with the program I need as the shell, rather than explorer.exe, which allows me to use it comfortably with just 192MB+1MB (vram) allocated to the virtual machine.

I used this same setup with 512MB RAM, but there was noticeable thrashing, which is why I upgraded to 1GB.

So you definitely don't need oodles of RAM or multi-core processors.

---

