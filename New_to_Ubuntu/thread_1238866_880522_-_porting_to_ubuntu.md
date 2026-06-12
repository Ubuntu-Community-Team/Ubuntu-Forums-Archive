---
title: "880522 - porting to ubuntu"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by hamidi on 2009-08-12
hi
i'm going to try immigrating from Windows platforms that i've been always familiar with to the Ubuntu platform. in this immigration, i've to port the followings:

1. i've a database of some files in flashget in its Default.jcd file. i need to be able to continue downloading them. note that another download manager may not be helpful while it may not understand the database file and import my suspending downloads.

2. i use eMule version 0.49c. i need to continue downloading part files too. only files located in temp folder may be enough and there's no need for importing a database file or recognizing it in this case.

3. in NTFS, i was taking advantage of its compression capability, especially for the eMule .part files. regardless of the volume of the downloaded files, they didn't use additional space while they were not yet downloaded. i decided to use ReiserFS when installing Ubuntu. does it also have such a benefit?

4. i need also to port Babylon online dictionary. it was really handy and i need to have it also in the Ubuntu environment.

5. i have a Technisat SkyStar 2 DVB Card installed in the box. where's the Ubuntu's Deivce Manager so that i may check whether it has detected it as a network card and may work with it without any problem?

6. how can i rotate display to portrait from landscape? when i found that in System/Preferences/Display i might select only Normal from the Rotation combobox, i decided to install NVIDIA accelerated graphics driver (version 180) by clicking on the Activate button in the Hardware Drivers dialog brought up by clicking on Hardware Drivers in System/Adminitration. but in the driver installed there's no selection for rotation and the old dialog still remained with the only Normal selection.

i will certainly come again with some other issues :D
but for now, it seems enough! lol
thanx

---

### Post by hamidi on 2009-08-14
:o really no idea?!

---

### Post by Bölvaður on 2009-08-15
> **hamidi said:**
> 
1. i've a database of some files in flashget in its Default.jcd file. i need to be able to continue downloading them. note that another download manager may not be helpful while it may not understand the database file and import my suspending downloads.

It should be somewhere in your home folder. Press ctrl+H to reveal the hidden files, it might be under .mozilla, possibly the exact same place as in Windy


> **hamidi said:**
> 
4. i need also to port Babylon online dictionary. it was really handy and i need to have it also in the Ubuntu environment.

 Applications &#8594; Accessories &#8594; Dictionary
You can add new dictionary servers, but I doubt they let you access theirs... and if they follow standards.

> **hamidi said:**
> 
5. i have a Technisat SkyStar 2 DVB Card installed in the box. where's the Ubuntu's Deivce Manager so that i may check whether it has detected it as a network card and may work with it without any problem?

Deivce Manager ? :confused:
You manage your devices with drivers... I guess you'll.. umm.. write your own driver?

but in the unlikely event of you asking for a list of hardware connected to your computer it can be used by a command that is named "list harsware" or lshw and lspci which is.. well it is self explanatory.

open the terminal (applications &#8594; accessories &#8594; terminal)
and type: lshw
or for more details : sudo lshw   (and _**blindly**_ type your password and hit enter)

This list is way more detailed than enough.


> **hamidi said:**
> 
6. how can i rotate display to portrait from landscape? when i found that in System/Preferences/Display i might select only Normal from the Rotation combobox, i decided to install NVIDIA accelerated graphics driver (version 180) by clicking on the Activate button in the Hardware Drivers dialog brought up by clicking on Hardware Drivers in System/Adminitration. but in the driver installed there's no selection for rotation and the old dialog still remained with the only Normal selection.

it is probably 1 line you need to add in the xorg.conf
you can try change it with the default "System &#8594; Preferences &#8594; Display", check out /etc/X11/xorg.conf and take a backup of it... oh god I dont know, posting a thread about it might be a good way to start. Sounds simple enough problem to solve tbh.


> **hamidi said:**
> 
i will certainly come again with some other issues :D
but for now, it seems enough! lol
thanx
please post 1 problem per thread, you will get the attention of the people skimming over the topic names for something they can solve, and therefore considerably fewer will answer your post.

and remember the topic name must be about the problem, otherwise the people knowing the solution, will not know they can help or not, so they begin helping someone else than you (not everyone click on randomly named threads).

---

