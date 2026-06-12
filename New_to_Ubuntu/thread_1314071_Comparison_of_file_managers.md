---
title: "Comparison of file managers?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Mander on 2009-11-04
I'll probably be attacked for this, but here goes.

I know this has been discussed a million times in various places, but can someone point me toward a *good* discussion of all the file managers available in Linux/Ubuntu?  I started up in Vista today to run some GIS software, and I found that for all Vista pisses me off, I actually quite like Explorer.  What is the closest equivalent for Linux?

The things I like about Explorer are the layout of the Details view, plus the available choices for more details in different columns.  I've tried a Nautilus script that adds some columns, and it works, but it made Nautilus un-useably (sp?) slow.  I also like the favorite links/folders pane on the left, and the various details that appear in the bottom pane in Explorer.  I also like the integrated options that appear when you highlight a file or folder, especially "organize" and "email".  The other little thing I like is that if you have a tree view in the left pane, which is my preference, and you select a long folder name, the position of the text in the pane automatically adjusts so that you can see the words better.  I do also like the integrated search, at least in theory, and the way the location bar works (shows "breadcrumbs" but will turn to a normal path when you click it).  I also like the idea of tags, but I haven't actually used them much.  And somehow the layout seems to include more information in a more compact space, even if the file previews are on, than anything I've tried on Ubuntu.

I have no plans to go back to Windows full time because it drives me bonkers in almost every other respect.  But I've never been very happy with the file managers I've tried on Linux.  So far I've tried various tweaks and scripts for Nautilus, Gnome commander, Konqueror, Dolphin, PCman, Thunar, and probably a couple of others that I've forgotten.  Surely there is one that is a little bit more comprehensive and integrated, without being so slow?

---

### Post by anaconda on 2009-11-04
I too like windows explorer better than any file browser in linux.

I tried most of the ones available in linux, and 
konqueror was the best that I tried, It can be configured to be/do about anything you want. 


But nowadays I am back with nautilus. It is pretty good, and I have gotten used to it...

---

### Post by fela on 2009-11-04
Well nautilus definitely sucks if you want features, it's an alright simple file manager though. I use KDE with dolphin as my file manager, and it definitely meets or surpasses the experience I have with the windows 7 explorer. Who cares really? It's a file manager, you browse the filesystem and open files. All the file managers I've used have done all this perfectly, on Windows, Linux, and even the Finder on OSX (which even Mac elitists shout FTFF at).

---

### Post by abhiroopb on 2009-11-04
I'm curious, what kind of features are we talking about here?

I've often found that I don't realise I need something until I see that its available!

---

### Post by fela on 2009-11-04
> **abhiroopb said:**
> I'm curious, what kind of features are we talking about here?

I've often found that I don't realise I need something until I see that its available!

Stuff like having an arrow after each folder in the 'breadcrumbs' or address bar so you can access any directory alongside each directory above the current one, if you see what I mean. Dolphin has it; Winblowsnsucks exploder has it; nautilus doesn't.

---

### Post by abhiroopb on 2009-11-04
Like the tree in the panel? Isn't that there already?

---

### Post by Mander on 2009-11-04
The tree in the panel is already there, but I just like the way it is handled in explorer better.  Namely, I can have a list of favorite places on top, and the tree view below.  The size of either part is readily adjustable, so I have as much of either one visible as I want. 

I guess the main thing is that is just seems like the layout and use of space is better, plus the larger number of things you can choose to display in a column in details view.  

That plus the fact that nautilus just seems to be stupidly slow for me.  There has to be some kind of problem but I can't figure out what it is.  Clicking on some folders (like /home) can take almost two minutes to open (yes, I timed it).  Gnome commander or Dolphin don't take as long, but they also seem to be missing some obvious features like extracting archives from the context menu and so on.  Probably I am just missing how to implement these things but it is kind of frustrating.

---

### Post by KIAaze on 2009-11-04
> **Mander said:**
> Gnome commander or Dolphin don't take as long, but they also seem to be missing some obvious features like extracting archives from the context menu and so on.  Probably I am just missing how to implement these things but it is kind of frustrating.

Dolphin/Konqueror context actions:
[http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus](http://techbase.kde.org/Development/Tutorials/Creating_Konqueror_Service_Menus)
[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)

Nautilus context actions:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

Mmh, I'm not on my Kubuntu machine right now, but I'm pretty sure extracting archives from the context menu is possible by default...
If not, it definitely should be.

I'm going to suggest another great filemanager: Midnight Commander
```
sudo apt-get install mc
```
:D

I mostly use it to easily switch diorectories in terminals actually.
To stay in the directory visited with mc on exit, add this to your ~/.bashrc:
```
source /usr/share/mc/bin/mc.sh
```
[http://polishlinux.org/apps/cli/midnight-commander-in-action/](http://polishlinux.org/apps/cli/midnight-commander-in-action/)

---

