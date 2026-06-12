---
title: "Where are programs installed!?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-14
Hello everyone, I would like to know where the default programs that came with Ubuntu 11.04 are installed, and where are new programs installed by default (or in other words, where is the program files of windows located in Ubuntu), and whether or not I can change where they are installed, thanks in advance!

---

### Post by Insomnia64 on 2011-08-14
This was something that i first thought when i switched to linux, the actual answer is they are not contained in one specific folder like on windows, but generally you don't need to know where they are.

Most config files you might want to access are located in your home folder (if you can't see them in nautilus press Ctrl-H).

If you want a list of installed packages then you can view that through the synaptic package manager.

Edit: If you really want to know where a program executes from you can do ```
whereis <program_name>
``` in a terminal. This will show you the location of source files and any executables.

---

### Post by the-new-x on 2011-08-14
> **Insomnia64 said:**
> This was something that i first thought when i switched to linux, the actual answer is they are not contained in one specific folder like on windows, but generally you don't need to know where they are.

Most config files you might want to access are located in your home folder (if you can't see them in nautilus press Ctrl-H).

If you want a list of installed packages then you can view that through the synaptic package manager.
Yes but if you want to make a program start with Ubuntu, you need to know where it is found, and this is the main reason I have asked this question!
And you said something about nautilus, I'm still knew to Ubuntu, so can you please tell me what exactly nautilus is, thank you!!

---

### Post by Insomnia64 on 2011-08-14
> **the-new-x said:**
> I'm still knew to Ubuntu, so can you please tell me what exactly nautilus is, thank you!!

Nautilus is the GNOME GUI file manager (think windows explorer).

The location of executables for using in scripts should be able to be found with whereis that i edited in my first post. Can't say i've tried it though.

---

### Post by the-new-x on 2011-08-14
> Edit: If you really want to know where a program executes from you can do  	Code:
 	whereis <program_name> 
 in a terminal. This will show you the location of source files and any executables.

thanks a lot, really helpful!:P

---

### Post by the-new-x on 2011-08-14
So now I basically know what nautilus is, but I tried searching for it and did not find anything, how can I access it? (excuse me, but I'm still knew to the world of Ubuntu, been a windows user for my entire life.)

---

### Post by Foobarz on 2011-08-14
For the executable files, go to /usr/share/applications, find the application you want to boot on startup, and click properties. Inside you see a command field, and copy that command into startup applications. For example, the command for Libreoffice is simply libreoffice.

---

### Post by spiky001 on 2011-08-14
open home folder that is nautilus, or in terminal type ```
nautilus
```

---

### Post by the-new-x on 2011-08-14
> **spiky001 said:**
> open home folder that is nautilus, or in terminal type ```
nautilus
```
So you mean nautilus is the equivalent of windows explorer!?

---

### Post by the-new-x on 2011-08-14
> **Foobarz said:**
> For the executable files, go to /usr/share/applications, find the application you want to boot on startup, and click properties. Inside you see a command field, and copy that command into startup applications. For example, the command for Libreoffice is simply libreoffice.
This is exactly what I needed, thank you very much!

---

### Post by spiky001 on 2011-08-14
Yes. Your on a learning course today lol

---

### Post by Elfy on 2011-08-14
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

some links - I'd suggest getting the first one and wandering through the second (there's a lot in that thread)

---

### Post by the-new-x on 2011-08-14
> **spiky001 said:**
> Yes. Your on a learning course today lol
LOL, yes, thank you for your support, the community over here is really great, never thought I would learn that much about Ubuntu in 1 day, let alone the first day that I make threads over here, again, thanks!

---

### Post by the-new-x on 2011-08-14
> **forestpiskie said:**
> [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

some links - I'd suggest getting the first one and wandering through the second (there's a lot in that thread)
Always with the useful links, thanks man, downloading the pdf right now, and saving the thread in bookmarks, will check later, I'm a little bit tired at the moment!

---

### Post by Foobarz on 2011-08-14
That folder I gave you is where user installed applications appear. Unlike Windows, however, these are only the applications, and not the libraries that come with them. I know that in Windows, every application has its own folder in Program Files which has the application AND the dll libraries the application requires. The Linux model is that libraries are usually stored in the /bin folder and the applications share that folder, and user applications within the /usr folder. IMO, this does not cause any duplicate libraries, since all applications just access the libraries they need through /bin. In Windows, it is possible to have a library in an application's Program Files folder, AND a library in the general C:\WINDOWS folder, resulting in duplicates and sometimes chaos. One case of this problem under my own experience was the time Windows Defender accidentally deleted the mscvp60.dll from the general WINDOWS folder, and my Avast Antivirus needed it to work. Turns out, there was an mscvp60.dll inside the AVAST folder, but somehow it was not recognizing. I ended up copying the dll from my other Windows machine. Hope you have an understanding of Linux installations. And if you are still confused about the different folders on the root filesystem, here you go: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by the-new-x on 2011-08-15
> **Foobarz said:**
> That folder I gave you is where user installed applications appear. Unlike Windows, however, these are only the applications, and not the libraries that come with them. I know that in Windows, every application has its own folder in Program Files which has the application AND the dll libraries the application requires. The Linux model is that libraries are usually stored in the /bin folder and the applications share that folder, and user applications within the /usr folder. IMO, this does not cause any duplicate libraries, since all applications just access the libraries they need through /bin. In Windows, it is possible to have a library in an application's Program Files folder, AND a library in the general C:\WINDOWS folder, resulting in duplicates and sometimes chaos. One case of this problem under my own experience was the time Windows Defender accidentally deleted the mscvp60.dll from the general WINDOWS folder, and my Avast Antivirus needed it to work. Turns out, there was an mscvp60.dll inside the AVAST folder, but somehow it was not recognizing. I ended up copying the dll from my other Windows machine. Hope you have an understanding of Linux installations. And if you are still confused about the different folders on the root filesystem, here you go: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
Very helpful, it did clear up some more stuff about Linux, thanks again, but what do you mean by IMO!?

---

### Post by frncz on 2011-08-15
> **the-new-x said:**
> Very helpful, it did clear up some more stuff about Linux, thanks again, but what do you mean by IMO!?
In My Opinion

---

### Post by the-new-x on 2011-08-15
> **frncz said:**
> In My Opinion
Guess I need a new slang tutorial, been a long time since I've used one of those (and yes I am only 17 years old!)

---

