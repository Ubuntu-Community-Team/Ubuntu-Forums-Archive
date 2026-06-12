---
title: "First time user first problem"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by strangelymade on 2008-12-27
Hi every one, well I decided to go over to Linux and I'm glad I did so far. It's a good system and much better than the other one I had (made by some bloke called Gates)

Any way, came across my first problem, tried to install DAZ3D  yesterday and it wouldn't work, so left it, gave it another go today and it sort of worked but not totally. I'd quite like to uninstall the program and try again once I've figured out what the problem is but I can't work out how to uninstall it. 

I'm using Ubuntu 7.10 and Daz in a Non Linux 3D rendering program (like Poser) if thats of any help.

---

### Post by Bucky Ball on 2008-12-27
System->Administration->Synaptics Package Manager

and do a search for Daz. Completely remove.

You can also find it in:

Applications->Add/Remove

... I don't doubt, and remove.

---

### Post by strangelymade on 2008-12-27
Unfortunately I've tried both of those methods and it can't find it. Even though I know it's there, I can't seem to find out where there darn thing has hidden it's self.

---

### Post by Bucky Ball on 2008-12-27
Okay, open a terminal and type or paste:

```
locate DAZ3D
```... or whatever the ***exact ***name of the file is to make sure you have it somewhere. When you locate it, give the command:

```
sudo apt-get remove DAZ3D
```

---

### Post by strangelymade on 2008-12-27
Figured it out. (I think)

I'd used WINE to install it, so I went into Applications> WINE> Programs> Daz3D and then used the uninstall function.

It's still shows up in WINE but doesn't open at all, so I guess it's gone from the system.

---

### Post by Bucky Ball on 2008-12-27
> **strangelymade said:**
> Figured it out. (I think)

I'd used WINE to install it, so I went into Applications> WINE> Programs> Daz3D and then used the uninstall function.

It's still shows up in WINE but doesn't open at all, so I guess it's gone from the system.

That explains everything. Yea, maybe that is just a shortcut icon you can delete showing up. Could you mark your thread as solved, please from 'Thread Tools' at the top of the page. :)

---

### Post by strangelymade on 2008-12-27
Bugger, just tried the terminal thing you advised and it looks as if DAZ is still there even after I tried the apt remove command. might try a re-boot and see if that gets whats left out of the system.

---

### Post by Bucky Ball on 2008-12-27
Did you input in the terminal exactly the same name as was showing up in wine? Not sure if an apt-get remove command will kill that file/directory, but you could try it.

---

### Post by strangelymade on 2008-12-27
Entered it the same as far as I can tell, the terminal came up with a long list of all the seperate DAZ files. Tried the apt remove again and it still doesn't look as if it's got rid of it. sure I'll figure out just what I'm not doing eventuallybut for today, I'm beat.

---

### Post by stoogiebuncho on 2008-12-27
If you installed it via WINE, the program files will be in your virtual C drive.  You can delete them by going to Applications > Wine > Browse C:\ Drive

Or you can open up the file manager, press Ctrl + H to show hidden files, and locate the .wine folder.  It should be in there.

You won't find it in apt-get if you installed it through wine.

I've found that the WINE uninstall often doesn't do the job very well, so I just go in and delete everything by hand.

---

### Post by strangelymade on 2008-12-27
> **stoogiebuncho said:**
> If you installed it via WINE, the program files will be in your virtual C drive.  You can delete them by going to Applications > Wine > Browse C:\ Drive

Or you can open up the file manager, press Ctrl + H to show hidden files, and locate the .wine folder.  It should be in there.

You won't find it in apt-get if you installed it through wine.

I've found that the WINE uninstall often doesn't do the job very well, so I just go in and delete everything by hand.

I'm probably doing something really silly but when I tried Ctrl + H I got the browser history tab up, I then tried it with Caps Lock on and still got the History. Should I be doing something else to get into hidden files?

---

### Post by Bucky Ball on 2008-12-27
This is not in a web browser, open 'Computer' in 'Places'. :)

---

### Post by strangelymade on 2008-12-28
*Palmface* Oh, that explains it then. Right managed to find the hidden files and get rid of the offending program. Now all I have to do is figure out just how to get DAZ to install properly, for some reason it doesn't seem to like WINE that much.

---

### Post by Bucky Ball on 2008-12-28
Is this the program you are talking about?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1998](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1998)

I have no idea what it does (looks like animation). Is there nothing equivalent in the open source realm? Anyhow, looks like 1.7 works better in Ubuntu than windoze.

(ps: Blender springs to mind, though I haven't used it myself - Applications->Add/Remove - search for animation and Blender and a bunch of other packages will turn up).

---

### Post by strangelymade on 2008-12-28
That is exactly the program. It's similar to Poser. I've tried Blender but it's not really the same type of program and not something I can use in my art. But thanks for suggesting it.

BTW, in the bit where the review wrote> 

I had to do
**winetricks vcrun6**
else it would complain about missing msvcp60.dll early
during install. I had to do
**winetricks wsh56**
else it would complain about not being able to run a script
at the end of install.
I had to make c:\ my current directory, i.e. cd ~/.wine/drive_c,
before installing, else it would try to create directory /DAZ
(and die because I'm not root). 

Am I right in assuming that the bold bits' should be done in a terminal?

---

### Post by Bucky Ball on 2008-12-28
Probably, but I have never used wine so am unfamiliar with its commands. :)

---

### Post by hyper_ch on 2008-12-29
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Bucky Ball on 2008-12-29
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11903](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11903)

I would make sure you are using DAZ version 2.1 and the same Wine version as outlined on this page as it is reported to work with Gold status, which you would presume means it works. There are also some tips down the bottom of the page.

... And as hyper_c mentioned, try and be as descriptive as possible in your post description. You will get more help. :)

---

