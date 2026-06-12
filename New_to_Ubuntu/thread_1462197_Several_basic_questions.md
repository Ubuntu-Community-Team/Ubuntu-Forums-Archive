---
title: "Several basic questions"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by blueghoti on 2010-04-25
Hi - 

Apologies for the absolute newbie questions but a couple of general things in regards to Ubuntu use, if someone can help me please...  (Couldn't find them posted elsewhere)

1 - somehow I managed to set my mouse to activate an obstructed window when I hover over it.  I don't like that setting, and now want to revert to activating the window when I click it.  How to I do that?

2 - I've managed to create and rename several panels (one each for various projects).  I see that I can manage different software in each - say Presentation in one, Spreadsheet in the next and Word Processor in the third.  How can I put specific files on each desktop?  Like just Presentation files in the first desltop, just Spreadsheet files in the second, and so forth?

3 - how do I load new software?  I downloaded another web browser and it offered me the chance to extract all the files in the package but I don't know how to actually start the install process.

Again, sorry for the basic questions - or any incorrect terminology!  Any help welcome.

Chris

---

### Post by dwarfolo on 2010-04-25
Wellcome

1) From the upper menu select System->Preferencies->Windows
Uncheck *Select windows when the mouse moves over them*

2) If you right-click on a window titlebar you get a menu through which you can send the window to another workspace.

3) It depends on the type of packages. Which browser are you trying to install? Where did you get the package and which type is it?

---

### Post by blueghoti on 2010-04-25
Hi Dwarfolo - 

Thanks for your quick reply!  Very helpful.

1/ - worked like a treat.  Perfect!

2/ hmm - I understand what you mean, but I'm trying to put specifically some files on one workspace's desktop so that they don't appear on the other workspaces.  Any ideas on this?

3/ ah - it happens to be Flock, but I think it's a general issue I have about how to actually install most programs...  I'm not sure if I need to click some sort of executable, or open with a specific installer program?

Thanks again!
Chris

---

### Post by 3rdalbum on 2010-04-25
> **blueghoti said:**
> 2/ hmm - I understand what you mean, but I'm trying to put specifically some files on one workspace's desktop so that they don't appear on the other workspaces.  Any ideas on this?

Workspaces share the common desktop, which is full of files from the "Desktop" folder in your home directory. There is no way to have different files on the desktop for each workspace. Workspaces are currently just a convenience for window management.

> 3/ ah - it happens to be Flock, but I think it's a general issue I have about how to actually install most programs...  I'm not sure if I need to click some sort of executable, or open with a specific installer program?

For Flock, you run it from the directory that it is in.

Usually in Linux you use the package manager to find, download and install new software rather than trawling the web like you would on other operating systems. Your package manager has two main interfaces currently - "Applications > Ubuntu Software Center" and "System > Admnistration > Synaptic Package Manager".

Wherever possible, install from there. If you want software that's not in your package manager, you can add "repositories" or "PPAs" to your package manager, which are just different places where the package manager can find software.

I don't know if there's a PPA for Flock, but when I used it I just double-clicked the "flock" program inside the decompressed folder.

---

### Post by dwarfolo on 2010-04-25
> **blueghoti said:**
> Hi Dwarfolo - 

Thanks for your quick reply!  Very helpful.

1/ - worked like a treat.  Perfect!

2/ hmm - I understand what you mean, but I'm trying to put specifically some files on one workspace's desktop so that they don't appear on the other workspaces.  Any ideas on this?

3/ ah - it happens to be Flock, but I think it's a general issue I have about how to actually install most programs...  I'm not sure if I need to click some sort of executable, or open with a specific installer program?

Thanks again!
Chris

Ok, just to see if I get you right

2) You have several workspaces but only 1 desktop.
You can put different application windows in different workspaces. But you still have only 1 desktop, so you can  put a file or a directory on your desktop but that file or that directory will always be present, regardless of the workspace you are working on.

3) In general on Ubuntu and on other Debian based distros you're going to install software through a package manager callad apt.
When you're inside a GUI environmet like Gnome or KDE, you can use a GUI frontend to apt. Explore The System->Administration menu and searh for Packages Manager. Through this interface you can search for specific software and install them with just a few clicks.
In many tutorial on the web you will be asked to enter some command in the console (something like sudo apt-get install ...), in this case open a terminal and just follow the instructions given in the tutorial.
The above methods are the standard on Ubuntu, but there could be some software that isn't present in the repos upon which apt works. In this case the correct method to install the package is usually detailed inside its documentation (in a README file in the package or on the official web site).
The process itself could cover a simple double click on an executable file as well as a more complex compilation of the source code.

---

### Post by blueghoti on 2010-04-26
Hi 3rdalbum and dwarfolo - 

Thanks for those tips!  It gets easier every day :-)

Chris

---

