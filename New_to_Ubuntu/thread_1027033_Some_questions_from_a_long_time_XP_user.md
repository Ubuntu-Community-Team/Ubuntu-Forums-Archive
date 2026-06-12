---
title: "Some questions from a long time XP user"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Zsev on 2008-12-31
Hi everyone, I've been a "1 day" (install then delete after spending a day trying to figure out driver issues) ubuntu user ever since the 6.XX releases. 

Thankfully, I have now installed ubuntu (without issues) using virtualbox, and I have several questions for you gurus here. 

1. Are the packages and softwares (firefox, OOffice etc) in a release ever updated? For instance a freshly downloaded 8.10 required 208 updates after installation. 

2. Occasionally while messing about the settings, the system would freeze up. Whats the ctrl-alt-delete equivalent of ubuntu (both gnome and kde)? 

3. Suppose I try out the KDE(which is awesome btw) beta 2 right now, will it upgrade automatically to the stable release in late january?

4. Whats a good place to learn using the terminal for ubuntu? Often I see experienced users telling a beginner to input a string of commands in terminal (to fix an issue). Problem is, most of us newbies have no idea what those commands are.  

5. Whats the state of audio in ubuntu? Is it a huge fail? Often I hear about pulseaudio breaking things(digg posts). All I know is that unless i use virtualbox, audio in ubuntu is extremely soft, almost inaudible.  

6. Kindly suggest a ubuntu equivalent software from this list of programs i use regularly in XP. 

**Image Viewer**
XP = IrfanView (lightweight, batch rename, resize etc) 
Ubuntu = ?

**ISO tool**
XP = Daemon Tools 
Ubuntu = ?

**Text Editor**
XP = Notepad++ (syntax highlighting, tabbed)
Ubuntu = ? 



Thanks in advance !

---

### Post by Paqman on 2008-12-31
> **Zsev said:**
> 
1. Are the packages and softwares (firefox, OOffice etc) in a release ever updated? For instance a freshly downloaded 8.10 required 208 updates after installation. 


There are updates to the disk images for LTS releases, but not normal releases (AFAIK)
> 
2. Occasionally while messing about the settings, the system would freeze up. Whats the ctrl-alt-delete equivalent of ubuntu (both gnome and kde)? 


That ain't good. There's no equivalent to ctrl-alt-del on Linux, although we do have ctrl-alt-backspace, which trashes your session and dumps you at a login screen.

For misbehaving apps, try Alt-F2 and type xkill, then click on the app to kill it.

> 
3. Suppose I try out the KDE(which is awesome btw) beta 2 right now, will it upgrade automatically to the stable release in late january?


Yep, any software you get from the repos upgrades automatically when the new version hits the repos.

> 
4. Whats a good place to learn using the terminal for ubuntu? Often I see experienced users telling a beginner to input a string of commands in terminal (to fix an issue). Problem is, most of us newbies have no idea what those commands are.


Depends. If it's a one-off command, just google it. Otherwise try:
```

man *commandname* 

```

It's always good to know what the commands mean, but you'll find much of what you're asked to do in the CLI as a newbie can often be done GUI-style. People traditionally give CLI-based help as it's unambiguous and quick to post. I don't always agree with providing CLI-based instructions to newbies, myself. 

> 
5. Whats the state of audio in ubuntu? Is it a huge fail? Often I hear about pulseaudio breaking things(digg posts). All I know is that unless i use virtualbox, audio in ubuntu is extremely soft, almost inaudible.  


I've not had an probs with Pulseaudio myself. Is it all your apps that were too quiet?

> 
6. Kindly suggest a ubuntu equivalent software from this list of programs i use regularly in XP. 

**Image Viewer**
XP = IrfanView (lightweight, batch rename, resize etc) 
Ubuntu = ?


I just use nautilus-image-converter to resize pics from a right-click. Or GIMP. I suspect you're after something between those two extremes.

> **ISO tool**
XP = Daemon Tools 
Ubuntu = ?

Linux can mount ISOs without any special software (just use the CLI command mount) If you want a GUI try gmount-iso.

> 
**Text Editor**
XP = Notepad++ (syntax highlighting, tabbed)
Ubuntu = ? 


There's about a million. Try Gedit, Kate, Nano, VIM, etc, etc.

---

### Post by AlanR8 on 2008-12-31
Let's have a go at this then....

> 1. Are the packages and softwares (firefox, OOffice etc) in a release ever updated? For instance a freshly downloaded 8.10 required 208 updates after installation.

**And how many updates does XP require? Yes the apps in the repos get updated on a regular basis. Most of the updates relate to systems, kernel and security.**

2. Occasionally while messing about the settings, the system would freeze up. Whats the ctrl-alt-delete equivalent of ubuntu (both gnome and kde)?

**ctrl + backspace. Reboots the GUI, not the OS. Sweet!**

3. Suppose I try out the KDE(which is awesome btw) beta 2 right now, will it upgrade automatically to the stable release in late january?

**Probably! I'm using Kubuntu 8.10 and KDE 4.2 Beta and loving it. If all goes to the usual plan it will automatically update to the stable release.**

4. Whats a good place to learn using the terminal for ubuntu? Often I see experienced users telling a beginner to input a string of commands in terminal (to fix an issue). Problem is, most of us newbies have no idea what those commands are.

**Search these forums. I came across something the other day about command line learning.**

5. Whats the state of audio in ubuntu? Is it a huge fail? Often I hear about pulseaudio breaking things(digg posts). All I know is that unless i use virtualbox, audio in ubuntu is extremely soft, almost inaudible.

**? Not from where I'm sitting! No problems with sound at all but I do use KUBUNTU not Ubuntu.**

6. Kindly suggest a ubuntu equivalent software from this list of programs i use regularly in XP.

Image Viewer
XP = IrfanView (lightweight, batch rename, resize etc)
Ubuntu = ?

**In Kubuntu Gwenview but you can install the Linux version of Picasa**

ISO tool
XP = Daemon Tools
Ubuntu = ?

**If you mean burning software, KB3 in Kubuntu**

Text Editor
XP = Notepad++ (syntax highlighting, tabbed)
Ubuntu = ? 

**In Kubuntu Kate**


Enjoy!

---

### Post by caro on 2008-12-31
I'm no guru but I'll give it a try...others can fill in the blanks or correct me.

> **Zsev said:**
> Hi everyone, I've been a "1 day" (install then delete after spending a day trying to figure out driver issues) ubuntu user ever since the 6.XX releases. 

Thankfully, I have now installed ubuntu (without issues) using virtualbox, and I have several questions for you gurus here. 

1. Are the packages and softwares (firefox, OOffice etc) in a release ever updated? For instance a freshly downloaded 8.10 required 208 updates after installation. 
[COLOR="Blue"]
You will get dot releases and bug fixes (eg. Firefox 3.0 to 3.01) but not new versions (like Firefox 2.0 to 3.0)[/COLOR]

2. Occasionally while messing about the settings, the system would freeze up. Whats the ctrl-alt-delete equivalent of ubuntu (both gnome and kde)? 
[COLOR="Blue"]If you have terminal open, use the command "kill" and enter the process number of the app you want to stop.  [/COLOR]

3. Suppose I try out the KDE(which is awesome btw) beta 2 right now, will it upgrade automatically to the stable release in late january?
[COLOR="Blue"]I've downloaded release candidates and received the upgrades through the upgrade manager.  If not you can force the upgrade from the terminal.[/COLOR]  

4. Whats a good place to learn using the terminal for ubuntu? Often I see experienced users telling a beginner to input a string of commands in terminal (to fix an issue). Problem is, most of us newbies have no idea what those commands are.  
[COLOR="Blue"]Start here:  [http://www.linuxcommand.org/]("http://www.linuxcommand.org/").  Also in terminal, type "man" followed by the command you want to learn about.  [/COLOR]

5. Whats the state of audio in ubuntu? Is it a huge fail? Often I hear about pulseaudio breaking things(digg posts). All I know is that unless i use virtualbox, audio in ubuntu is extremely soft, almost inaudible. 
[COLOR="Blue"]I use both Rhythmbox and Songbird and haven't noticed any problems but I'm not audiophile.  [/COLOR] 

6. Kindly suggest a ubuntu equivalent software from this list of programs i use regularly in XP. 

**Image Viewer**
XP = IrfanView (lightweight, batch rename, resize etc) 
Ubuntu = ?
[COLOR="Blue"]gThumb Image Viewer is one option.  If you need more editing capabilities for images, there is F-Spot Photo Manager and GIMP Image Editor.  [/COLOR] 

**ISO tool**
XP = Daemon Tools 
Ubuntu = ?

**Text Editor**
XP = Notepad++ (syntax highlighting, tabbed)
Ubuntu = ? 
[COLOR="Blue"]gEdit is standard.  there may be other packages.  [/COLOR]


Thanks in advance !

---

### Post by theozzlives on 2008-12-31
[QUOTE=
2. Occasionally while messing about the settings, the system would freeze up. Whats the ctrl-alt-delete equivalent of ubuntu (both gnome and kde)? 

[/QUOTE]

In VirtualBox, it's right ctrl+delete

---

### Post by SuperSonic4 on 2008-12-31
> **Zsev said:**
> Hi everyone, I've been a "1 day" (install then delete after spending a day trying to figure out driver issues) ubuntu user ever since the 6.XX releases. 

Thankfully, I have now installed ubuntu (without issues) using virtualbox, and I have several questions for you gurus here. 

1. Are the packages and softwares (firefox, OOffice etc) in a release ever updated? For instance a freshly downloaded 8.10 required 208 updates after installation. 

[B]If you allow the backport repo then you can major releases that came after the main release. This is in addition to what others have said
[/B]

3. Suppose I try out the KDE(which is awesome btw) beta 2 right now, will it upgrade automatically to the stable release in late january?

**Yes it will and any beta updates will also install, just remember it is beta so do not expect stability (that being said KDE 4.2 beta is very stable for a beta)**

5. Whats the state of audio in ubuntu? Is it a huge fail? Often I hear about pulseaudio breaking things(digg posts). All I know is that unless i use virtualbox, audio in ubuntu is extremely soft, almost inaudible. 

**No problem in Phonon, which is a frontend used by kubuntu. Amarok 1.4.10 is probably the best music player available on any platform (at least IMO :p)** 

6. Kindly suggest a ubuntu equivalent software from this list of programs i use regularly in XP. 

[I]XP = IrfanView (lightweight, batch rename, resize etc) 
Ubuntu = ?[/I]

**krename, kid3 will both batch rename files, gwenview and the gimp for resizing images**

*ISO tool*
XP = Daemon Tools 
Ubuntu = ?

**k3b - it does pretty much everything you can do with a cd from burning isos to ripping audio cds. You might also be interested in k9copy for ripping dvd to mpeg, avi or even to an ISO file to reburn in k3b/play in VLC.**

*Text Editor*
XP = Notepad++ (syntax highlighting, tabbed)
Ubuntu = ? 

**kate or nano. Possibly kwrite. nano is a cli meaning you can edit in terminal and kate and kwrite are gui.**


Thanks in advance !

I've tailored most of my answers to KDE because I run Kubuntu

---

### Post by honesthaxor on 2008-12-31
1. Yes, packeges usually update whenever needed. 

2. Don't know of any ctrl+alt+del shortcut, but the taskmanager equivalent is in System > administration > System moniter. There's also a panel applet for killing locked programs (force quit, I think). 

3. No idea about kde. I assume If you use the repositories, it will update. Don't ask me though; I don't use kde. 

4. For terminal tutorials, I personally enjoyed [this guide]("http://nemorathwald.com/wp-content/uploads/2008/03/unixforthebeginningmage.pdf"). The commands 'help' and 'man' are useful for help. 

5. Sound works ok. I had a little trouble in the beginning with flash, but I think thats fixed now. 

6. Synaptic package manager can find software pretty well. Just give it a search. Gedit (often referred to as "Text Editor" in menues) is already the default and has tabs and syntax highlighting.

---

### Post by Zsev on 2008-12-31
Goodness! Those are some really spot on replies. Cheers to you guys/girls who took time to respond. Such precise help is much appreciated :D

For killing frozen apps, the xkill method is new to me, i'll try that from the usual way i normmaly do it (kill -9 in terminal). 

As for the learning the command line, i'm gonna start off with the one in [http://linuxcommand.org]("http://linuxcommand.org") first. Although the unixforthebeginningmage recommended by honesthaxor seems like a more entertaining read (CLI with a sense of humor).

Haven't had time to try out all the suggested applications yet, but will do in due time. Seems like the default gnome and KDE apps already support all the advanced features I look for, something you just don't get from default XP applications. Pardon my windoze mindset of 15 years.

Once again, many thanks and have a happy new year ahead !

---

### Post by albinootje on 2008-12-31
> **Zsev said:**
> 

**Image Viewer**
XP = IrfanView (lightweight, batch rename, resize etc) 
Ubuntu = ?


According to this :
[http://www.irfanview.com/faq.htm](http://www.irfanview.com/faq.htm) Irfanview can run in Wine -->
you can run IrfanView in Wine in Linux :
[http://www.wine-reviews.net/applications/irfanview-410-on-linux-with-wine.html](http://www.wine-reviews.net/applications/irfanview-410-on-linux-with-wine.html)

My personal favorite image-viewer since years is gqview --> apt://gqview

> 
**Text Editor**
XP = Notepad++ (syntax highlighting, tabbed)
Ubuntu = ? 

Apart from what others suggested: vim-gtk and jedit

[http://www.jarcec.net/wp-content/2007/01/vim_gtk.png](http://www.jarcec.net/wp-content/2007/01/vim_gtk.png)
[http://packages.ubuntu.com/search?keywords=vim-gtk](http://packages.ubuntu.com/search?keywords=vim-gtk)

[http://www.jedit.org/index.php?page=screenshot&image=34](http://www.jedit.org/index.php?page=screenshot&image=34)
[http://packages.ubuntu.com/search?keywords=jedit](http://packages.ubuntu.com/search?keywords=jedit)

---

