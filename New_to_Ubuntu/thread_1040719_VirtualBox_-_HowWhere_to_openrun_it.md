---
title: "VirtualBox - How/Where to open/run it?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by EdwardD26 on 2009-01-15
I'm finding my web on ubuntu pretty well on my own, there's just ONE THING that I still dont get...

is how do I run the programs that I install, I mean where are they installed? wheres the quick access arghg im pulling my hairs right now...

ok.. so I'm done installing VirtualBox, now... how do I start it??

---

### Post by earthpigg on 2009-01-15
applications -> accessories -> VirtualBox OSE

;)

---

### Post by HotShotDJ on 2009-01-15
Applications --> System Tools

(I use the PUEL version.  If you installed the OSE version, Earthpigg might be right)

---

### Post by earthpigg on 2009-01-15
rely 2:

a 'package' can be/do anything... *usually* the makers are smart enough to make it add itself somewhere to your applications or (sometimes) system menu.

---

### Post by EdwardD26 on 2009-01-15
> **earthpigg said:**
> applications -> accessories -> VirtualBox OSE

;)

nope
> **HotShotDJ said:**
> Applications --> System Tools

(I use the PUEL version.  If you installed the OSE version, Earthpigg might be right)

nope

---

### Post by HotShotDJ on 2009-01-15
Please tell us exactly how you installed VirtualBox.  If you used either the repositories or the deb package downloaded from Sun, it should be in one of those places.

---

### Post by Vantrax on 2009-01-15
You could also try to locate a .desktop file called virtualbox.

Or you could make a shortcut yourself if for some reason the way you installed it didnt create a shortcut.

---

### Post by EdwardD26 on 2009-01-15
I dont remember... I remember that it downloaded, I think from sypnatic and then the installation dialog opened and I followed the instructions for a while and then it said complete, but it didnt prompt me to run/load the program or anything... it never asked me where I wanted it to have it installed...

---

### Post by EdwardD26 on 2009-01-15
> **Vantrax said:**
> You could also try to locate a .desktop file called virtualbox.

Or you could make a shortcut yourself if for some reason the way you installed it didnt create a shortcut.

Ok Vantrax this sounds like a good solution, but these are the things that I need to have explained... don't assume that a 1-week linux users knows how to do this :P

I'm guessing the search would be done in the terminal, whats the command??

and the shortcut, how?

---

### Post by HotShotDJ on 2009-01-15
Your description of the install process sounds strange -- the part about following on-screen instructions for awhile.  Once you've verified which packages you want installed, there aren't any instructions.  Synaptic just installs it and creates the menus.

But I guess that doesn't matter much at the moment.  Open a terminal (Applications --> Accessories --> Terminal) and type "VirtualBox" (without quotes... remember, Linux is case sensitive.  Type it in exactly like I showed, including upper and lower cases where indicated).

Let us know if VirtualBox opens.  If it does, we can create a quicklauncher for you quite easily.

---

### Post by EdwardD26 on 2009-01-15
> **HotShotDJ said:**
> Your description of the install process sounds strange -- the part about following on-screen instructions for awhile.  Once you've verified which packages you want installed, there aren't any instructions.  Synaptic just installs it and creates the menus.

But I guess that doesn't matter much at the moment.  Open a terminal (Applications --> Accessories --> Terminal) and type "VirtualBox" (without quotes... remember, Linux is case sensitive.  Type it in exactly like I showed, including upper and lower cases where indicated).

Let us know if VirtualBox opens.  If it does, we can create a quicklauncher for you quite easily.

Sweet! It worked, thanks DJ!

---

### Post by albinootje on 2009-01-15
> **EdwardD26 said:**
> I dont remember... I remember that it downloaded, I think from sypnatic and then the installation dialog opened and I followed the instructions for a while and then it said complete, but it didnt prompt me to run/load the program or anything... it never asked me where I wanted it to have it installed...

Please provide the output of :
```

dpkg -l|grep -i virtualbox

```
and try opening a terminal, and type :
```

VirtualBox

```
And don't forget to add your username to the vboxusers group!

---

### Post by empty_spaces on 2009-01-15
I had to manually enable the menu option for virtualbox on my system.
Go to System -> Preferences -> Main Menu. Highlight the System Tools option, and see if the option for Virtualbox need to be checked.

---

### Post by HotShotDJ on 2009-01-15
> **EdwardD26 said:**
> Sweet! It worked, thanks DJ!Cool.  To create a launcher... right click in an empty part of either your top or bottom panel.  From the pop-up menu, click on "Add to Panel..."  Now, click on "Custom Application Launcher" nd then click on the "Add" button near the bottom-right of he dialog box.  Fill in as follows:

Type: Application
Name: Sun xVM VirtualBox
Command: VirualBox
Comment: Run several virtual systems on a single host computer

Now, Click Ok... then close the "Add to Panel" dialog.

NOTE:  Only Type and Command need to be exactly as I indicate above.  The Name and Comment field can be anything you want... I've just used the entries from the menu entry that my version of VirtualBox put in the menu.

---

