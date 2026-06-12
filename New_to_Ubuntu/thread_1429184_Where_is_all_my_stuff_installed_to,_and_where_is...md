---
title: "Where is all my stuff installed to, and where is...well, everything else too?"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by NT2015 on 2010-03-13
Ok I thought this would be simple to figure out myself but apparently not. I have no clue how the directories are set up in ubuntu.  I know in windows you have "Program Files", "Program Files (x86)"(on 64-bit anyway), and Documents ans Settings which contains a hidden folder called "Application Settings" or something to that effect. Now ive been a windows user since 3.1 was "the S**t" so i know the directories almost by heart, "system32" and all that jazz. I dabbled with Mac OSX by running it on my pc, and i know that all of your programs are installed into a folder called "applications" yada yada yada. Anyway I have some questions that i would assume are basic.

1. Where are my programs installed to? (I know there are hidden folders in the Home folder, but not all my apps are there and furthermore the contents of the folders make absolutely no sense to me.) 
2. Where are my system files located? (Windows has "System" and "System 32", OSX has "Library" and "Extensions"  
3. What is considered to be a executable file on Ubuntu? (All i know is that packages are .deb. again we all know windows has ".exe" and most OSX apps are ".app". I know most of my apps are in the menus but what are the files called, and where can i find them? EX. on windows, Firefox puts entires in the start menu and on the desktop, but if you go to "C:/Program Files/Mozilla Firefox" there will be a file called "Firefox.exe")
4.How do i remove dead launchers from my menus?

I suppose thats it, I absolutely LOVE running Ubuntu. Im currently running Karmic 64-bit, and so-far so-good. :)

And heres one not so important question. I love how mounted drives come up on your desktop like in OSX, but how can I set it so all my drives go the the right side of my screen by default and not the left? Currently I just drag them over there and they stay put but when i insert something new, like a new flash drive, it will be on the left.

I just hate not knowing how this is all set up, i mean in windows i had my .exe, .dll, etc and i knew where they all were and what files went to what prog. and in OSX i had my .app, and .kext and such. But I am learning slowly but surely, and i cant wait till im able to help others. :)

If anyone thinks there are some other basic things that are important to know please post away, I dumped all the memories of my ex-grilfriend to make room for learning ubuntu. lol

---

### Post by oldfred on 2010-03-13
this is the file system hierarchy.
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Just about anything can be executable if you set the executable bit. Files are not defined by their extension. You can see what the file name used to lauch the application by right clicking on applications, edit menus and look at properties.

---

### Post by NT2015 on 2010-03-13
Thank you, I had no idea i could edit the menus like that. And im going to study the Link you posted too.

If anyone else has any other tips or any thing thats useful to know about Ubuntu or Linux in general please keep it coming. I'm dedicated to learning this system one way or another. :)

---

### Post by srs5694 on 2010-03-13
> **NT2015 said:**
> Ok I thought this would be simple to figure out myself but apparently not. I have no clue how the directories are set up in ubuntu.

Oldfred's pointer to the Filesystem Hierarchy Standard (FHS) is a good place to look for many details, but I thought I'd post with some other pointers....

> I dabbled with Mac OSX by running it on my pc, and i know that all of your programs are installed into a folder called "applications" yada yada yada.

Actually, in OS X the Applications directory only contains the OS X-specific GUI programs. OS X is built atop Unix, and so it includes many of the same directories and text-mode programs as Linux does. OS X just tucks these out of the way so that users don't stumble upon them in file browsers too often.

> 1. Where are my programs installed to? (I know there are hidden folders in the Home folder, but not all my apps are there and furthermore the contents of the folders make absolutely no sense to me.)

As the FHS details, applications do *not* ordinarily go in users' home directories. The main exceptions would be programs that users compile themselves (either because they wrote them or because they downloaded them for personal use but didn't formally install them) and Windows binaries run via WINE (although these can also be installed system-wide if you tweak the WINE configuration).

Users' home directories do often hold application settings, though. These are usually stored in files or subdirectories whose names start with a dot ("."), as in .bashrc or .mozilla. System-wide settings usually go in /etc.

One key point to remember is that Windows evolved from a single-user OS into one that's (kinda-mostly) a multi-user OS, whereas Linux began life as a multi-user OS. Therefore, the separation between system files and user files is much better in Linux than in Windows. Windows programs often dump user files wherever it's convenient for them, but this is rare in Linux programs. (The main exception that springs to mind is high-score files for some games.)

> 3. What is considered to be a executable file on Ubuntu? (All i know is that packages are .deb. again we all know windows has ".exe" and most OSX apps are ".app". I know most of my apps are in the menus but what are the files called, and where can i find them?

As the FHS details, most programs are in /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin, or occasionally other directories called bin or sbin. Linux program files don't normally have distinctive filename extensions. Unix and Linux filesystems support an "executable bit" to identify program files. You can set this bit on any file using the chmod command ("chmod a+x foo" sets it on the file foo), but doing so only makes sense for binary program files and scripts.

Debian package files, with the .deb extension, are just carriers; they're similar to .zip files, but a little more specialized.

> 4.How do i remove dead launchers from my menus?

That depends on your desktop environment. I'm most familiar with Xfce in this respect. With it, you'd right-click the launcher category, select properties, select the specific launcher you want to remove in the dialog box, and click the "-" button.

---

### Post by 3rdalbum on 2010-03-13
The hidden folders in your home directory contain the settings for your user account. If a program starts misbehaving, try removing its settings from your home directory. And if you want to change computers without losing all your settings (including e-mail from Evolution and stuff like that), you need to copy over the contents of the hidden folders from your home directory.

---

### Post by NT2015 on 2010-03-13
Wow, Im amazed at how much ive just learned within the past few hours. If anyone has some more links that are easy to understand shoot-em my way. Im just....I simply cant believe i stayed with windows as long as i did. Its a decent OS dont get me wrong, but the security problems, and the constant problems with wga, etc, etc.... I just didnt realize how different linux was :o.  And Wine just made it all the easier to switch.;)

Please keep the info coming, but at this point my original question was more than answered. Even though I hope people will continue to post new info in here, should I mark this thread as [solved]?

---

### Post by azertyh on 2010-03-14
hi,
have you read the sticky of this forum, especially the "free beginners" and "new to ubuntu"? they are very useful imo.

---

### Post by Choragos on 2010-03-14
The best way to learn this OS is to have a patient office-mate who is an expert in these things.  This forum is a close second.

(Thanks Trevor)

---

