---
title: "finding programs supposedly installed"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by henry cow on 2010-04-29
I feel like I keep asking goofy and obtuse questions, but things continue to mystify me.

Yesterday I had a question that involved gconf-editor and I received instructions on getting and installing it, which I followed. (just to try to keep the Open-Close-Minimize buttons consistent in any application) Applications/Software Center/Installed Software reports that it is installed, but how do I access it?  Supposedly gconf-editor should "be in" Applications/System Tools, but it isn't. Where is it, and how can I run it, or put it somewhere that it can be run? 

I come from over a decade each of DOS and Windows, so I am not green,  but I am accustomed to "loading" - "installing" - and "running"  programs.

Same with Google Earth. Syanptic Package Manager shows it done, but where is it? The categories of Applications may help some people, but they irritate me. What is Google Earth? It's not a game, or graphics, or office. Maybe it is an accessory. I use it for work and for fun. Anyway, it is nowhere to be found.

This is obviously a conceptual issue on my part, but it is hard for me to get my mind around. I am a book person and have a couple of Ubuntu books but they make me want to scream - they spend endless ink describing the minutiae of simple stuff, and breeze over the difficult and obscure concepts with a snide and dismissive sentence or two, like that is what "everybody" knows.

This forum is great and all of you who patiently help beginners are magnificent and valuable. One day I hope to know enough to contribute something.

---

### Post by Sealbhach on 2010-04-29
Google Earth should show up in your Internet menu.

Just to make sure it's there, try opening a terminal and typing

```
googleearth
```If it's installed, it should launch for you. Then if it didn't create a menu entry, you can create one yourself in System/Preferences/Main Menu.

Welcome to the community, I know once you get over the initial irritations of not knowing how to do things, you will come to love Ubuntu and Linux like the rest of us.

If you want to know where a program is installed, try the "which" command, e.g.

```
which googleearth
```

.

---

### Post by aysiu on 2010-04-29
You shouldn't have to install *gconf-editor*

It's already installed. You can run it by pressing Alt-F2 and typing ```
gconf-editor
``` and hitting Enter.

Or you can right-click the Applications menu and Edit Menus and then check the box for *gconf-editor* so it shows up in the menus.

---

### Post by madjr on 2010-04-29
install ubuntu tweak

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

then install gnome-do (is like quick silver); helps you find and do stuff quick



[http://www.youtube.com/watch?v=oTxqE3M1k0U](http://www.youtube.com/watch?v=oTxqE3M1k0U)
[http://www.youtube.com/watch?v=7EKAlLvpovE](http://www.youtube.com/watch?v=7EKAlLvpovE)

[http://www.omgubuntu.co.uk/2010/03/gnome-do-to-get-more-kickass-than.html](http://www.omgubuntu.co.uk/2010/03/gnome-do-to-get-more-kickass-than.html)

you can summon it just by pressing super-key (windows-key) + space


another way is **deskbar-applet**
search for it in the **software-center**
[http://www.howtogeek.com/howto/ubuntu/search-your-computer-quickly-with-the-deskbar-applet-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/search-your-computer-quickly-with-the-deskbar-applet-on-ubuntu/)

yea there is a shift in mentality you need to get used to

it took me a month when i started back in 07 (but was not as easy as it's now, so for you probably few weeks)

but was worthed it :)

---

### Post by henry cow on 2010-04-30
Please do not think I am a pest. First, I already had Ubuntu Tweak and that made quick work of putting the buttons on the right. I could probably get accustomed to having them on the left - as long as that was a consistent location across all programs.

Regarding Google Earth: none of the advice worked. Typing "googleearth" in the (alt-F2) terminal returned "no such file or directory" and running "ggogleearth" from the terminal I set on the desktop (the one with the prompt) returns "googleearth: command not found"

Assuming that I had a bad install, I went to Synaptic Package Manager and completely un-installed it, then re-installed it. Package Manager said that the installation was successful, but Ubuntu Software Center does not show it in its list of Installed Programs. 

"which googleearth" returns a complete blank.

It has to be me, what am I doing wrong?

---

### Post by Sealbhach on 2010-04-30
Ok, this means you don't have Google Earth installed.

Make sure you have the medibuntu repository enabled, you can do this in Ubuntu Tweak - go to Source Centre, select Multimedia and tick on Medibuntu PPA. Then press Sync.

Now run search for updates in Update Manager. Finally go into Synpatic and install Google Earth. 

I suspect what has happened is that you have installed googleearth-package which is a packaging tool for developers, not the application itself. Opening up Medibuntu gives you an extra software channel, from which you can download the fun and games packages like Google Earth.

If that doesn't work, we'll talk you through installing the .bin file from the Google website.

.

---

