---
title: "System documentation"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by andr3w on 2009-01-28
I don't know how to title stuff. :)

Hi! I'm just trying to figure out, like in depth where to find stuff in the filesystem.
I know this varies, but like, for example, I'm trying to find where the icons on the menu in GNOME are stored, and stuff I'd like to backup.

I just want a really good definition of where things are stored in Ubuntu, if possible.
Like, the difference between /usr/sbin and /bin, idk, and like what the main hidden folders do in the /home directory. There's a bunch, I'm just not sure..
Does anybody know?

---

### Post by marshall.robert on 2009-01-28
This is relevant to my interests.

---

### Post by Michael.Godawski on 2009-01-28
hi,

perhaps this chart will help a bit:


[LIST]
[*][http://www.doxit.net/blog/?p=197](http://www.doxit.net/blog/?p=197)
[/LIST]

---

### Post by andr3w on 2009-01-28
> **marshall.robert said:**
> This is relevant to my interests.

Hey cool. 
Yeah, I'm not really good @ explaining my question..

I know that obviously not **everything** can be documented. Because some programs do different things, or whatever. But a general overview (that **isn't** general) would be nice.

I'd like to know, like, what I would copy, if say I wanted to keep my settings for gnome-terminal. Or, whatever. Cause there's a **lot** of hidden folders in the home directory, and I know not all of them are from program settings.

I'm trying to find where I'd look for wine settings as well. And it seems that copying the .wine folder actually doesn't do it. I tried the .local folder as well but no luck.

I know if you copy the whole folder over it'll screw up everything. So I can't do that. lol. :D

---

### Post by Michael.Godawski on 2009-01-28
Files of one application are not stored in one folder in Linux.

You can open the Synaptic Package Manager, search for an installed package, right-click on it, then go to Properties and Installed Files.

There you will see all directories and folders which contain data which is native to this very package.

---

### Post by andr3w on 2009-01-28
> **Michael.Godawski said:**
> 

You can open the Synaptic Package Manager, search for an installed package, right-click on it, then go to Properties and Installed Files.

There you will see all directories and folders which contain data which is native to this very package.

Oh ok. Yes, that would help for doing it manually.

> **Michael.Godawski said:**
> 
Files of one application are not stored in one folder in Linux.

Well, I mean, I'm referring to that type of storing like;
copying .mozilla over to the new installation, type of storing.

Thanks for the tip.

> **Michael.Godawski said:**
> hi,

perhaps this chart will help a bit:


[LIST]
[*][http://www.doxit.net/blog/?p=197](http://www.doxit.net/blog/?p=197)
[/LIST]

It helped a bit.
But looking @ the directories in comparison, there's a ton of other stuff. That was a bit too general. (Solved the sbin bin difference question though.) :)

There **is** an explanation of where everything is stored and what it does for Ubuntu right?
... Like a detailed layout.

---

### Post by cariboo on 2009-01-28
The is no definitive documentation of where every thing in Ubuntu is located. 

[Overview of Linux File System]("http:///tldp.org/LDP/intro-linux/html/sect_03_01.html")

See attached picture.

Jim

---

### Post by linux_tech on 2009-01-28
There is no registry but for gnome gconf has alot of settings.

---

