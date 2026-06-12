---
title: "REALLY beginner stuff"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by bsmith52 on 2008-12-27
I just installed ubuntu. Saw the vertical lines. Searched the forums and found a revised driver for my d201gly2 video....

[http://ubuntuforums.org/showthread.php?t=930930](http://ubuntuforums.org/showthread.php?t=930930)

But I need to find a way to learn REALLY basic stuff: file structure (I heard about this thing called ROOT?) - editor (many years ago I used a line editor for my FORTRAN - is there something newer?) - what do I edit? - how does it effect my version of ubuntu?

I believe that there is some basic tutorial on this website on this stuff - just can't find it.  Thanx.

---

### Post by Moop on 2008-12-27
Check out psychocats. [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by chrisod on 2008-12-27
Try the posts pinned at the top of this forum.

---

### Post by inxygnuu on 2008-12-27
Both of the above posts will work.

[Terminal Basics]("https://help.ubuntu.com/community/UsingTheTerminal")
 
the editor is "gedit" or text editor and root is the all powerful administrator on your system. you are a sudoer, or right below root (same/similar abilities).

Hope I helped,
3v4n

---

### Post by inxygnuu on 2008-12-27
you can also try Moop's sig links. Those look promising.

---

### Post by appi2012 on 2008-12-27
As for the file structure, it's a little different, and IMO, simpler than windows.

Ubuntu runs on a filesystem. the root of this system is /. There are no drive letters like C:/. Other drives, other than the one the system is running on, can be mounted onto the filesystem, kind of like docking a space shuttle to a space station. It is possible to mount drives anywhere you want, but when you plug in a usb, for example, ubuntu automatically mounts it at /media/disk. Programs are stored in /bin/. However, the programs in this directory can be acessed by simply typing the name of the program into a terminal. However, most applications install a shortcut which runs its command in the applications menu. The files you normally use are stored in /home/[username]/. This is referred to as your "home folder." It can be acessed quickly through the file manager, as it is bookmarked in the side pane. That's pretty much all you need to know about the filesystem.

What kind of editor are you talking about?
Word?
Text?
Image?

---

### Post by hyper_ch on 2008-12-28
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Michael.Godawski on 2008-12-28
hi, 

have a look at my introduction to root and sudo. Perhaps it will help you.

[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[/LIST]

If you want to learn more about root and sudo do not miss the question and answer session on irc:

[LIST]
[*][https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events/01172009](https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Education/Events/01172009)
[/LIST]
there I will be answering together with forestpixie as many beginner questions conerning root and sudo as possible.

---

### Post by bsmith52 on 2009-01-01
Sorry I didn't respond to you guys sooner - twists and turns in my life.  But thanks mucho for the place to get some beginner info.  I've checked out a few of your suggestions, and it seems to fill in some of the (BIG) holes in my knowledge of Linux.

Again, thanks.

---

