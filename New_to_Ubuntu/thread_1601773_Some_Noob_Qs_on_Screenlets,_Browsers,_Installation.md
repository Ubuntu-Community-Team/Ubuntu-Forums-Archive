---
title: "Some Noob Qs on Screenlets, Browsers, Installations"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by onaridge on 2010-10-20
p { margin-bottom: 0.08in; }  Looking for some basics here....

All the browsers in Ubuntu don't allow you to just type in the address line without first deleting whatever is in there. In Windows I could just click on the address line, it would highlight and then I could type whatever. Having to delete first is driving me crazy and can't be right. What simple procedure am I missing?

Also I am trying to figure out where things go when installed. For example, when I install screenlets that aren't already in the screenlet manager, I can't figure out how to install them and then manage them via the manager.  Do all programs that aren't from a repository install in the opt folder? I usually have to unzip them and choose a folder but what folder and then what do i do with the files? I am used to just clicking on an .exe file.

With Windows, if you didn't reboot daily, you had a slow beast after awhile. In Linux, can you leave your computer on for days and not suffer performance degradation?

Some of my effects work on the cube, other's done like, reflection and dream. Why is this?

If you want to remove a program not in the software center, how do you delete the folder? I tried to delete a program I decided I didn't want that I didn't get from the repository and I can't do anything with the folder.

I hope this isn't too many questions...  :confused:

---

### Post by sandyd on 2010-10-20
> **onaridge said:**
> p { margin-bottom: 0.08in; }  Looking for some basics here....

All the browsers in Ubuntu don't allow you to just type in the address line without first deleting whatever is in there. In Windows I could just click on the address line, it would highlight and then I could type whatever. Having to delete first is driving me crazy and can't be right. What simple procedure am I missing?
**double click the address bar (firefox)**

Also I am trying to figure out where things go when installed. For example, when I install screenlets that aren't already in the screenlet manager, I can't figure out how to install them and then manage them via the manager.  Do all programs that aren't from a repository install in the opt folder? I usually have to unzip them and choose a folder but what folder and then what do i do with the files? I am used to just clicking on an .exe file.

With Windows, if you didn't reboot daily, you had a slow beast after awhile. In Linux, can you leave your computer on for days and not suffer performance degradation?
**depends if you close programs. If you open programs, and never close them. and continue using the computer, its obviously going to get slow after you open a million programs**

Some of my effects work on the cube, other's done like, reflection and dream. Why is this?

If you want to remove a program not in the software center, how do you delete the folder? I tried to delete a program I decided I didn't want that I didn't get from the repository and I can't do anything with the folder.
**what program?**
I hope this isn't too many questions...  :confused:.

---

### Post by onaridge on 2010-10-20
OMG knew it was something easy with the address bar!!
The program was an install of Google from the Google site. I am using Chromium instead and just for educational purposes I wanted to remove it. The files are in the OPT folder.

re the PC staying on, yes I meant the programs would be closed and no I wouldn't be opening and opening programs .   Thanks!!!

---

### Post by sandyd on 2010-10-20
> **onaridge said:**
> OMG knew it was something easy with the address bar!!
The program was an install of Google from the Google site. I am using Chromium instead and just for educational purposes I wanted to remove it. The files are in the OPT folder.

re the PC staying on, yes I meant the programs would be closed and no I wouldn't be opening and opening programs .   Thanks!!!

tripple click it for the google browser (dont know why they did it, but...)

---

### Post by SuaSwe on 2010-10-20
How did you install the program? Was it from a .deb package? If so you should be able to use Synaptic (GUI) or apt-get (command line) to remove it.

You need to be root to remove things in the /opt folder - best not to manually touch things in there unless you're sure it's safe!

---

### Post by onaridge on 2010-10-20
Don't remember if it was a DEB pack but I will stay away from the Root for now. It's not doing any harm in there. No it wasn't in Synaptic, I had checked there. 

So in general, where do certain pkgs go when they are installed? Is there a rule of thumb?

---

### Post by SuaSwe on 2010-10-20
You don't have a "Program Files" equivalent to Ubuntu as such - a lot of file 'libraries' are shared by several programs, and separate configuration files can end up in /etc, /opt, /home and various other places. If you're curious, [this article]("http://www.pathname.com/fhs/pub/fhs-2.3.html") goes into some depth about the file structure of UNIX-like operating systems. :D

---

### Post by ivarn on 2010-10-20
Every single program here is a package, so to remove or add packages you just go to system > admin > synaptic package manager.
Remember, some programs are not supported by the ubuntu theme so if you don't find them in synaptic or the software center, check their websites.
I.e. LimeWire.
And yes you can leave the PC as long as it doesn't heat up which happens from time to time and often if you use a laptop. If it gets worm you should probably give it a few hours break.
Screenlets will be installed under your user folder > .screenlets.
Click "view hidden files" to see the folder.
In firefox you just have to double click to select all in the address bar.
EDIT: And executable files are always in a bin folder which means, when you make a shortcut to a program or wanna open a program you just type in the program name (most of the time) i.e to open up firefox, just time firefox.

---

### Post by onaridge on 2010-10-20
yes! that article is exactly what I was looking for. 
Re screenlets, ok I had found the .screenlet file..now when i go to unzip them, is that where I place them?

---

### Post by ivarn on 2010-10-20
> **onaridge said:**
> yes! that article is exactly what I was looking for. 
Re screenlets, ok I had found the .screenlet file..now when i go to unzip them, is that where I place them?
No you don't have to unzip them. just open up the screenlets program and drag-n-drop the tar.gz file into the program and it will ask if you want to install it.
This drag and drop method works for most things such as backgrounds, themes, cursors, screensavers etc. Btw you can find a lot of good stuff like that on [www.gnome-look.org]("http://www.gnome-look.org").
EDIT: To change the theme, icons, cursors and stuff, right click and go to change the background and the first tab there is theme.

---

### Post by onaridge on 2010-10-20
AHHHH because I just found some background I wanted and I didn't know what to do with the tar.bz2 and was gonna extract it. Works great! Thank you. Now everything makes sense. So what do you suggest I do with the archive which sits in downloads for the moment. Just delete it since it is now in the the repository?

---

### Post by ivarn on 2010-10-20
Your choice. if they are useful to you, I would backup the files somewhere.
Then you don't need to visit 100 websites every time you do a fresh installation (if you ever have to).

---

### Post by onaridge on 2010-10-20
good point!
Thanks for your help...much appreciated!

---

### Post by trikster_x on 2010-10-21
> **onaridge said:**
> p { margin-bottom: 0.08in; }  Looking for some basics here....

All the browsers in Ubuntu don't allow you to just type in the address line without first deleting whatever is in there. In Windows I could just click on the address line, it would highlight and then I could type whatever. Having to delete first is driving me crazy and can't be right. What simple procedure am I missing?

double click= highlight the word the cursor is in
triple click= highlight the entire entry field

This is true of basically any search bar in linux.  Unlike windows which at times does not allow complete text highlighting without running the cursor from one end of the entry field to the other.

> Also I am trying to figure out where things go when installed. For example, when I install screenlets that aren't already in the screenlet manager, I can't figure out how to install them and then manage them via the manager.  Do all programs that aren't from a repository install in the opt folder? I usually have to unzip them and choose a folder but what folder and then what do i do with the files? I am used to just clicking on an .exe file.

Most things that are installed as user specific will end up in your home folder and be hidden.  Simply press ctrl+H to unhide everything while in the home folder.

The screenlets are installed in the /usr/share/screenlets directory.  If you want to install screenlets manually (since sometimes the GUI method can cause problems, at least it has for me), I would suggest you find out how to use the "sudo", "cd", "mv", and "cp" terminal commands.  Learning to use the terminal in general will make linux a lot easier to use.  Most applications that will be available for use on all users will be found in /usr/share. 

> With Windows, if you didn't reboot daily, you had a slow beast after awhile. In Linux, can you leave your computer on for days and not suffer performance degradation?

No worries there.  I have a desktop that I leave going for weeks at a time with no problems.

> Some of my effects work on the cube, other's done like, reflection and dream. Why is this?

Some of the compiz settings can take some messing around with in the options to get them running just right.  And some stuff you vid card may just not be capable of.  For instance, I love the blur feature for adding that little extra cool to drop downs and dialogs, but I am unable to run it on one of my computers because the vid card just doesn't have enough oomph to do it.  Also make sure in the appearances settings you have extra selected on the visual effects tab.

> If you want to remove a program not in the software center, how do you delete the folder? I tried to delete a program I decided I didn't want that I didn't get from the repository and I can't do anything with the folder.

I hope this isn't too many questions...  :confused:

Again, this is where sudo comes into play.  Learn as much as you can about that command and some of the basic commands like cd (change directory), cp (copy), mv (move), rm (remove), etc.  If you installed it using a .deb file, then try looking in synaptic, which is found in System>>Administration.  I have to assume this is the method you used since, from the questions you are asking, you would not have built the software from source, and anything installed through software center would allow you to delete through software center.  Also, look into apt-get and aptitude (both command line tools).  Those three programs allow much finer control than the software center as far as installing and uninstalling programs.

For new users, I can never stress enough getting very familiar with sudo and the use of root commands, because a bad command does have the ability to frag your install beyond repair.  And any time you use the rm command, double check EVERYTHING you type, since that is one of, if not the, most dangerous commands for someone new to linux.

---

### Post by onaridge on 2010-10-21
Thanks for the very useful info and I will learn the commands, they look pretty straight forward. Great OS I am loving it!

---

