---
title: "Programs question"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-13
Hi,
When you install Programs and packages and things, what if you want to remove them later?
I've installed a few things like emesene for example, but what if I want to remove these later?
Is there a graphical manager for installed programs like Windows has?
and how can I also do it through terminal? (to view all installed then remove completely)

Also last but not least, what directory do they get installed too usually?

---

### Post by SunnyRabbiera on 2009-06-13
The best thing for this is synaptic, located under system > administration > synaptic package manager.
Synaptic offers a easy to use GUI front end.

---

### Post by Viva on 2009-06-13
System -> Administration -> Synaptic is the most straight forward way, but you can also remove most programs using Add/Remove Programs in the menu. I recommend the later until you get used to ubuntu.

---

### Post by SunnyRabbiera on 2009-06-13
> **Viva said:**
> System -> Administration -> Synaptic is the most straight forward way, but you can also remove most programs using Add/Remove Programs in the menu. I recommend the later until you get used to ubuntu.

Yeh but even synaptic is quite easy to use, I got started on linux because of synaptic.
Synaptic makes things quite simple.
Here is a great guide to get one started:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

As for directories of where apps go, usually usr/bin is where most applications reside, though some can be found in usr/lib such as firefox.
Now the files that go along with them thats another story but its not that critical.

---

### Post by 3rdalbum on 2009-06-13
> **Gp. said:**
> Also last but not least, what directory do they get installed too usually?

You don't need to know. This isn't Windows. The package management system will get rid of the whole package and will not leave any of the package behind. It's not something you need to concern yourself with.

But I'll assume that you're asking for curiosity. Each program gets spread out over a number of different directories. If you look at the package properties in Synaptic, and go to the "Installed Files" tab, you can see what is where.

Usually, the executable itself is inside /usr/bin. Support files are usually in /usr/share/programname. Manual pages are stored where the "man" command can find them, and launchers (for your Applications menu) are usually in /usr/share/applications. Any necessary libraries are usually in /usr/lib. Icons are stored in one of a number of different places, but they are always stored where the program (and sometimes where Gnome) can find them.

You really don't need to know any of this, but if you wanted to know, well now you do!

If no launchers are installed, then your Applications menu will not contain the program (this happens with a handful of packages). You can manually create a launcher for the program by editing the menu and creating a new item with the "command" as just the name of the program. Often if there's no launcher, then it means that you've just installed a command-line program.

---

