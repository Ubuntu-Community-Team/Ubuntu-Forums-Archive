---
title: "Tweaking Ubuntu :D"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by DarkDavil on 2009-10-03
I'm VERY used to using Windows, Currently im using a legit and 100% activated version of Windows 7 due to my MSDN membership... And usually on my laptop, i always dualboot, just for program;s to work on everything, and i then deleted my vista completly, and i now have Ubuntu 9.04 on a 40GB Partition(my Windows 7 is on a 100++GB one).

And i need some help tweaking my ubuntu...

1. My graphics card isnt supported or something - i tried to but the visual effects on the highest settings - and i get the messege saying that it cannot do that task... Why? My graphics card is : a Nvidia GeForce 8400 GS M ( its a laptop edition)

2. RAM Reconization --? I have 4GB of ram, and my system's processors are 64-bit, does Ubuntu 9.04 use all of this ram to my advantage or wut? :D 

3. Taking advantage of my Dual Core Processors - i have Intel Dual Core t800 @ 2.4 GHz 

4. Customization? I cannot understand where all of these tools and etc. ate located... Do i type everything into the CMD promp worthy program in Ubuntu - the Terminal? 

5. Where is my list of all programs located? In windows its the startbutton->all programs-> i can launch whatever i want, i really wanna use the KGeometry program that came with Ubuntu - but i cannot even find it!! I even used the file search searching all of my computer :D 

6. Performance - any Defragment software needed? In my W7 i'm using O&O Pro Defrag. 12, can this be used to monitor my Ubuntu as-well?

7. Themes, i would like to check out some cool looking - Ubuntu ~ish based themes.. How can i, and where can i get them? 

Thanks all ^^

Lol @ Me for asking you'll so many questions :)

But thanks for help beforehand ^^ !

(Any other questions needed about my system requirements jst post, ill edit this post/post another :) Thanks all! ))

---

### Post by credobyte on 2009-10-03
> **DarkDavil said:**
> 
6. Performance - any Defragment software needed? In my W7 i'm using O&O Pro Defrag. 12, can this be used to monitor my Ubuntu as-well?
No need to cleanup or defragment your hard drive.

> **DarkDavil said:**
> 7. Themes, i would like to check out some cool looking - Ubuntu ~ish based themes.. How can i, and where can i get them? 
Themes, icons, wallpapers, etc.: [Eyecandy for your GNOME-Desktop - GNOME-Look.org]("http://gnome-look.org/")

---

### Post by pedro3005 on 2009-10-03
1 - Go to System > Administration > Hardware Drivers and enable the propietary drivers.
2 - Yes, it will.
3 - Same.
4 - I don't understand your question. What exactly do you want to customize? You can do some basic stuff with the options under System > Preferences.
5 - Generally a program will be under the Applications menu, but some don't create an entry there. Then you'll launch it via ALT + F2 and typing it's name. KGeometry should be under the Applications > Office menu.
6 - Linux uses a different filesystem than windows, so no defragging is necessary. That is a windows issue.
7 - If you use GNOME: [http://gnome-look.org/](http://gnome-look.org/) If you use KDE: [http://www.kde-look.org/](http://www.kde-look.org/)

---

### Post by sigurnjak on 2009-10-03
1. My graphics card isnt supported or something - i tried to but the visual effects on the highest settings - and i get the messege saying that it cannot do that task... Why? My graphics card is : a Nvidia GeForce 8400 GS M ( its a laptop edition)

A: You may need restricted drivers for ubuntu . Google it , you will find lots of info .

2. RAM Reconization --? I have 4GB of ram, and my system's processors are 64-bit, does Ubuntu 9.04 use all of this ram to my advantage or wut?

A: Are you using 64 bit ubuntu , 32 bit does not see 4 gigs

3. Taking advantage of my Dual Core Processors - i have Intel Dual Core t800 @ 2.4 GHz

A: Already done , nothing to tweak .

4. Customization? I cannot understand where all of these tools and etc. ate located... Do i type everything into the CMD promp worthy program in Ubuntu - the Terminal?

A : See themes .

5. Where is my list of all programs located? In windows its the startbutton->all programs-> i can launch whatever i want, i really wanna use the KGeometry program that came with Ubuntu - but i cannot even find it!! I even used the file search searching all of my computer

A: Application menu  is your start menu .Kgeometry is KDE , you need to get it from synaptic . 

6. Performance - any Defragment software needed? In my W7 i'm using O&O Pro Defrag. 12, can this be used to monitor my Ubuntu as-well?

A: No defragin is needed in linux .

7. Themes, i would like to check out some cool looking - Ubuntu ~ish based themes.. How can i, and where can i get them?

A : [http://www.gnome-look.org/](http://www.gnome-look.org/)

All this and more here :
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Enjoy  Ubuntu and do not be afraid to ask anything ! :)

---

### Post by cariboo on 2009-10-03
> 1. My graphics card isnt supported or something - i tried to but the visual effects on the highest settings - and i get the messege saying that it cannot do that task... Why? My graphics card is : a Nvidia GeForce 8400 GS M ( its a laptop edition)

Your graphics caed is well supported, go to System-->Administration-->Hardware Drivers and installed the restricted graphics drivers

> 2. RAM Reconization --? I have 4GB of ram, and my system's processors are 64-bit, does Ubuntu 9.04 use all of this ram to my advantage or wut?

If you are using the 64-bit version Ubuntu supports 2^48 Gb ram. To see ram usages go to System-->Administration-->System Monitor, be aware that the system monitor has it's own overhead. If you are running a 32-bit version it will only see 3.2Gb.

> 3. Taking advantage of my Dual Core Processors - i have Intel Dual Core t800 @ 2.4 GHz 

Dual core support is compiled into both the 32-bit and 64-bit kernel.

> 4. Customization? I cannot understand where all of these tools and etc. ate located... Do i type everything into the CMD promp worthy program in Ubuntu - the Terminal?

Right click on the desktop and go to Change Desktop Background.

> 5. Where is my list of all programs located? In windows its the startbutton->all programs-> i can launch whatever i want, i really wanna use the KGeometry program that came with Ubuntu - but i cannot even find it!! I even used the file search searching all of my computer

All the programs that are installed by default are located in the Applications Menu. To install new programs go to Applicataions-->Add/Remove Applications or System-->Administration-->Sysnaptic Package Manager

> 6. Performance - any Defragment software needed? In my W7 i'm using O&O Pro Defrag. 12, can this be used to monitor my Ubuntu as-well? 

Fortunately Linux file systems are not as sloppy as Microsoft file system, I never had to defrag a Linux file system, I've been using a Linux distribution of one sort or another since 1998.

You also don't need an av scanner. A firewall isn't needed if you haven't installed any extra services.

---

### Post by anonymous_user on 2009-10-03
Question 1, Make sure you install the restricted drivers. Go to System > Administration > Hardware Drivers > install the driver for your graphics card (if available)

Question 2, Yes. Linux (in general) will use your memory as a cache.

Question 3, Yes Linux can take advantage of dual-cores.

Question 5, Have you checked the Applications menu?

Question 6, Defragmenting is not really needed.

---

### Post by DarkDavil on 2009-10-03
Thanks - but how do i "implement" a theme... in WIndows i would have had to go into my core sys. files and edit my .dll extensions... i hear its easier in Ubuntu? :D

---

### Post by 3rdalbum on 2009-10-03
Good, some easy questions :-)

> **DarkDavil said:**
> And i need some help tweaking my ubuntu...

1. My graphics card isnt supported or something - i tried to but the visual effects on the highest settings - and i get the messege saying that it cannot do that task... Why? My graphics card is : a Nvidia GeForce 8400 GS M ( its a laptop edition)

You need to install the driver for your graphics card. Go into Synaptic Package Manager and click the Reload button, and then search for and install the nvidia-glx-180 package. Reboot and you'll have accelerated 3D.

> 2. RAM Reconization --? I have 4GB of ram, and my system's processors are 64-bit, does Ubuntu 9.04 use all of this ram to my advantage or wut? :D 

You need the 64-bit edition of Ubuntu to use the 64-bit features of your CPU, including the ability to address more than 4GB total memory. Ubuntu always uses as much RAM as it can for cache, but obviously if you're not doing anything especially RAM-intensive then Ubuntu is not going to fill your RAM with random junk from the hard disk in the hope that it can get used.

> 3. Taking advantage of my Dual Core Processors - i have Intel Dual Core t800 @ 2.4 GHz

Already happening. Different processes and threads are being allocated to different cores on your computer as we speak. 

> 4. Customization? I cannot understand where all of these tools and etc. ate located... Do i type everything into the CMD promp worthy program in Ubuntu - the Terminal? 

That depends what you want to do.

> 5. Where is my list of all programs located? In windows its the startbutton->all programs-> i can launch whatever i want, i really wanna use the KGeometry program that came with Ubuntu - but i cannot even find it!! I even used the file search searching all of my computer :D 

KGeometry does not come with Ubuntu, you need to install it from Add/Remove Applications or Synaptic Package Manager. It should appear in your Applications menu once you have installed it.

If any program doesn't show up in your Applications menu when it's installed, then you can follow the screencast in my signature to find it and add it; but usually when this happens it means that the program is a command-line utility.

> 6. Performance - any Defragment software needed? In my W7 i'm using O&O Pro Defrag. 12, can this be used to monitor my Ubuntu as-well?

No, there are not really any defragmentation programs for Ext3 filesystems. They are not needed anyway unless your filesystem is VERY full - the Ext filesystems are fragmentation-resistant.

> 7. Themes, i would like to check out some cool looking - Ubuntu ~ish based themes.. How can i, and where can i get them? 

[www.gnome-look.org](www.gnome-look.org), they are available for download. Some of them may depend on theme engines that you can download from Synaptic. A handful of them might depend on "Murrine SVN" or "Aurora" which are not in the Ubuntu repositories but can be compiled from source code.

Also, the Ubuntu repositories have some themes, but they're not flashy.

To install a theme from gnome-look or similar websites you can either drag the .tar.gz package onto the Appearance window and then click the "Customise" button, or you can put the contents of the package into /usr/share/themes (you need to open a file browser as root, remember, because that location is outside your home directory).

---

### Post by pedro3005 on 2009-10-04
Right click on your desktop, Change Desktop Background. On the Theme tab you have some themes ready for you. If you want something different, just download the .tar.gz , click Install Theme and find it. A list of themes (the .tar.gz's) are found here: [http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/](http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/)
I highly recommend the Dust theme.

---

### Post by lukeccby on 2009-10-04
> **DarkDavil said:**
> Thanks - but how do i "implement" a theme... in WIndows i would have had to go into my core sys. files and edit my .dll extensions... i hear its easier in Ubuntu? :D


To add a theme, right click on the desktop (or goto System>Preferences>Appearance), after you have one downloaded from gnome-look.org (or wherever), just drag and drop into the Themes folder.  :)

---

### Post by DarkDavil on 2009-10-04
YES!!!! So easy on Ubuntu!!! Thanks :D Very awsomeee!! XD

---

### Post by DarkDavil on 2009-10-04
Okay.... my graphics card wont work on this.... i went into System>Administration>HardWare Drivers 
and i activated the one on the top ( the  version 180 of my Nvidia accelerated driver) and it still wont let me activate the extreme graphics or anything :(

---

### Post by credobyte on 2009-10-04
> **DarkDavil said:**
> Okay.... my graphics card wont work on this.... i went into System>Administration>HardWare Drivers 
and i activated the one on the top ( the  version 180 of my Nvidia accelerated driver) and it still wont let me activate the extreme graphics or anything :(

Did you restarted your computer ?

---

### Post by pedro3005 on 2009-10-04
Did you restart*

---

