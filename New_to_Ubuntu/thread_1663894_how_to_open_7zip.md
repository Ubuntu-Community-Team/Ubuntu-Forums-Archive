---
title: "how to open 7zip"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by suryak on 2011-01-10
I installed 7Zip from Ubuntu Software Center
How do I open it / How do I run compressed files in it .. 
I have a .rar file and how do i open it with 7zip..  It is not found in the 'other applications' .. and neither i don't know the command that has to be typed so that i can run the file.. 

Please do guide and also give me a general method for doing this type of works.. 
Things are very different here in ubuntu compared to Windows XP !!

---

### Post by Synthetic Sam on 2011-01-10
Archive Manager should now open 7zip archives (double click the archive).

Alternatively, from command line:

```

man 7z

```
That will tell you how to use it (press q to quit the manual).

```

7z x archive.7z

```

To extract in current directory

```

7z x archive.7z -o path

```
to specify a path to extract to.

---

### Post by Frogs Hair on 2011-01-10
7zip on Ubuntu does not have a GUI like the Windows version. I first used 7zip on Windows so I was confused as well. To compress with 7zip right click the package/folder and select compress and choose package type an location from the menus in the dialog box.

---

### Post by cgroza on 2011-01-10
File Roller (the default archive manager) should do it all for you.

---

### Post by harun3d on 2012-04-27
No graphical user interface!
extracting with very special secret codes in the terminal makes it unusable.

it is like guessing someones password.

I typed

```
 7z x MyRarFile.rar
```

no output. not even the reason of the problem.

I typed

```
 7z x MyRarFile.rar -o path
```

no output


That is why ubuntu will never be number one operating system in the world.

---

### Post by 3rdalbum on 2012-04-27
> **harun3d said:**
> No graphical user interface!
extracting with very special secret codes in the terminal makes it unusable.

You're making things too difficult for yourself. The post before yours said to simply use File Roller (Ubuntu's default archive manager program) which will do it all for you with a nice easy GUI.

---

### Post by Synthetic Sam on 2012-04-27
> **3rdalbum said:**
> You're making things too difficult for yourself. The post before yours said to simply use File Roller (Ubuntu's default archive manager program) which will do it all for you with a nice easy GUI.
I also stated that Archive Manager would do it, I only suggested the command line options to be helpful if it was ever needed in the future.

---

### Post by cromat on 2012-04-27
"That is why ubuntu will never be number one operating system in the world."

Why because the current tools don't all have GUI's?  As more people move to it, those things will be built, if you build it all now and expect people to come you are wasting time. The OS needs to evolve with its user base. Plus with 6 month release cycles and 2 year LTS cycles you will always have a more up to date os that reflects the needs of your user base before M$ can put out a new OS every 4 years that is 2 LTS versions.

Ubuntu is growing and my grandparents use it and don't have problems with it, it is all about perception and an open mind. Giving up because you don't have a GUI. In windows a long time ago, you needed to use the command line to zip and unzip.

---

### Post by oldos2er on 2012-04-27
Old thread closed.

---

