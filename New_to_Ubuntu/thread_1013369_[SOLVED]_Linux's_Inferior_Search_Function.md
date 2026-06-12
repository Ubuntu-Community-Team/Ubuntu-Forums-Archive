---
title: "[SOLVED] Linux's Inferior Search Function"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by icyest on 2008-12-16
I can't find where I installed KDEnlive on my computer. It's nowhere in  the main menus option, and preferences cannot reveal it. It's apparently hidden. I had to resort to command prompt every time to activate it, which I found to be very frustrating. This took 45 minutes to find.

The search function yielded a list of files, but their directories are not visible. The view option won't even enable me to see directories in visible columns.

With windows, you can actually get a view of what your computer's architect and what it looks like from directory to directory. This was how I (and many others) were able to learn windows faster than Linux. Not even that, but Windows Vista even included the spotlight function, which makes their systems even more logical in design.

My question is, how does Ubuntu compete with things like a logical search function and "Program Files" which makes computing on Windows more intuitive.

---

### Post by jerome1232 on 2008-12-16
Couldn't you have just created a desktop launcher? Program executables are generally kept in /usr, To locate them you can type "which *programname*". 

as an example this is what I get for k9copy
```
which k9copy
/usr/bin/k9copy
```


(also when I use tracker in gnome I do get a full path to the files I search for)

I don't know about kde but on gnome You can just right click on your desktop and select "create launcher". Or Just right click your menu and select edit menu to add launchers to any of your menu's. There's no need to know where the program is installed to as  it will be in the system's path, just need to know the name of the program launcher.

Perhaps an understanding of the Linux Filesytem Hierarchy would help you.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by starcannon on 2008-12-16
I use "Tracker"/"Deskbar Applet" in gnome, it works excellent, and does a lot more than just track down files; but, for this demonstration I only had it look for jpg's. Heres a screen shot of my search, I think you'll find it has it all (and a lot more):

[IMG]http://img213.imageshack.us/img213/5818/trackerxb8.png[/IMG]

---

### Post by samden on 2008-12-16
Just go to the System menu, find the Menus control panel, and in there will be the option to create a new launcher for a program. I can't recall exactly where as I aren't using Gnome right now, but it is easy to find.

You obviously already know the command to start it from the command line. All you do is make a new launcher that when you click on it will run that command, and start the program. You can put it wherever you like in the applications menu. Very simple and easy to follow. Actually simpler than on Windows because you don't even need to know where the program is saved!

For a good search function, use "which", as jerome1232 has explained. But you don't actually need to do this to solve your problem.

---

### Post by billgoldberg on 2008-12-16
> **icyest said:**
> I can't find where I installed KDEnlive on my computer. It's nowhere in  the main menus option, and preferences cannot reveal it. It's apparently hidden. I had to resort to command prompt every time to activate it, which I found to be very frustrating. This took 45 minutes to find.

The search function yielded a list of files, but their directories are not visible. The view option won't even enable me to see directories in visible columns.

With windows, you can actually get a view of what your computer's architect and what it looks like from directory to directory. This was how I (and many others) were able to learn windows faster than Linux. Not even that, but Windows Vista even included the spotlight function, which makes their systems even more logical in design.

My question is, how does Ubuntu compete with things like a logical search function and "Program Files" which makes computing on Windows more intuitive.

Edit the menu, and add it.

Or use the laucher (alt+f2).

Your statement in the title that linux search is inferiour doesn't make sense.

Linux doesn't search for anything.

I don't know what app you use to search for files, if you don't like it, use another one.

---

### Post by Unanimated on 2008-12-16
I use whereis when it's something in my filesystem, but I do agree that Tracker is awful. I use Google Desktop for all my searches.

---

### Post by JoshuaRL on 2008-12-16
I just don't know.  Maybe it's just me, but I have never used indexing or desktop search.  Not even once.  I just turn that off.

But then again, that doesn't help this discussion any.

---

### Post by handydan918 on 2008-12-16
Executable files (like programs/applications) can be located at the command line with ```
which <programname>
```

Try that with windows...

):P

---

### Post by mkvnmtr on 2008-12-16
Gee thanks guys .It turns out it's really easy and there are about a half dozen ways to find files.

---

### Post by iponeverything on 2008-12-16
```
locate <file>
```

```
dpkg -L <pkg-name>
```

---

### Post by emanresu on 2008-12-16
i have to agree with o.p. i get no results from tracker and when i do, they're useless. i searched with rhythm for Rhythmbox and i get the nebulous list in the left window and nothing on the right window. and the little search results thing with the magnifying glass and electricity thing icon doesn't usually do much for me either. what's the point?

---

### Post by jerome1232 on 2008-12-16
As a side note I added the repo for google desktop and installed it, I like it thus far. Might want to try that for your searching.

[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

---

### Post by handydan918 on 2008-12-16
> **jerome1232 said:**
> As a side note I added the repo for google desktop and installed it, I like it thus far. Might want to try that for your searching.

[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

I would recommend a little security related research before settling in on that....

---

### Post by HotShotDJ on 2008-12-16
> **emanresu said:**
> i have to agree with o.p. i get no results from tracker and when i do, they're useless. i searched with rhythm for Rhythmbox and i get the nebulous list in the left window and nothing on the right window. and the little search results thing with the magnifying glass and electricity thing icon doesn't usually do much for me either. what's the point?The point is to search your home directory (and subdirectories) for files and metadata containing the search term.  I find it quite useful.  It is GREAT for searching email, music collections, pdf files, documents, etc. It is not for searching the system files, although you COULD configure it to do that.

---

### Post by icyest on 2008-12-16
> **billgoldberg said:**
> Edit the menu, and add it.
 (and the same to samden)

That was precisely what I meant when I said Preferences could not reveal it. Preferences, under Systems, has a Main Menu option as most of us know. It just doesn't exist for some reason. What do you suppose is wrong?

[[IMG]http://img401.imageshack.us/img401/2114/screenshotmainmenufs3.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshotmainmenufs3.png)

---

### Post by samden on 2008-12-16
Just click on the "New Item" button, top right. That will let you make a launcher for the program, it should be very straightforward but post if you have any problems.

The discussion on this thread has gone on an interesting tangent regarding searching, which may be useful to you with other issues. But remember that you do NOT need to search AT ALL to solve your problem - you would have had to in Windows but that is unnecessary in Ubuntu. All you need to do is click on that "New Item" button and type in the command you usually type in the terminal to run the program. Very simple.

---

### Post by starcannon on 2008-12-16
> **emanresu said:**
> i have to agree with o.p. i get no results from tracker and when i do, they're useless. i searched with rhythm for Rhythmbox and i get the nebulous list in the left window and nothing on the right window. and the little search results thing with the magnifying glass and electricity thing icon doesn't usually do much for me either. what's the point?
My search results for the word rhythm were exactly what I would expect
[IMG]http://img340.imageshack.us/img340/8291/rhythmboxvp1.png[/IMG]

---

### Post by Paqman on 2008-12-16
I've always found Beagle to be a lot better than Tracker.

---

### Post by emanresu on 2008-12-22
that was helpful, HotShotDJ. now, since i know it doesn't do what i thought it was for, i won't use it.

---

### Post by emanresu on 2009-01-28
i know this thread says solved, but i didn't see the reason to start a new one.

i had uninstalled and then reinstalled tracker to see if it would be more effective for me.

i'm trying to use tracker to find a document i made the other day called inte. after i run the search, i get the Categories panel on the left of the window and the Search Result pane on the right side of the window. however, i don't see specific files anywhere. tracker tells me i have 3 results under the text category, but i can't figure out what or where they are. how do i get tracker to show specifics? i've included a screen print of what the results window looks like. 

i know it says that tracker is still indexing, but the results window had the same set up before i tried to reinstall and i don't think that should affect it anyway.

---

