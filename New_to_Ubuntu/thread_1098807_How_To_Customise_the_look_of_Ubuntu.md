---
title: "How To Customise the look of Ubuntu"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Scubdup on 2009-03-17
Please can someone explain the different options and resources to me?

I've found some nice wallpapers and changed the desktop background, and I've downloaded Compiz from the repositories and enables a cool cube effect thing for when I change desktops (but it only works horizontally, not in 360°) and now I'm trying to do other stuff.

Is there a decent list of the most complete themes available? Ie the ones that have no bugs but do significantly cool things with the desktop?

How do I set up the cube that rotates in more than one plane? And how do I give it a cool backdrop?

---

### Post by overdrank on 2009-03-17
> **Scubdup said:**
> Please can someone explain the different options and resources to me?

I've found some nice wallpapers and changed the desktop background, and I've downloaded Compiz from the repositories and enables a cool cube effect thing for when I change desktops (but it only works horizontally, not in 360°) and now I'm trying to do other stuff.

Is there a decent list of the most complete themes available? Ie the ones that have no bugs but do significantly cool things with the desktop?

How do I set up the cube that rotates in more than one plane? And how do I give it a cool backdrop?

Hi and you may look at the link in my signature on the FAQ's :)

---

### Post by kanikilu on 2009-03-17
> **Scubdup said:**
> Is there a decent list of the most complete themes available? gnome-look.org is a good place to start.

> the ones that [...] do significantly cool things with the desktop? That's a bit subjective. Why don't you tell us what you are looking for, and maybe someone will know of a theme that fits?

> How do I set up the cube that rotates in more than one plane? I don't use it, so someone correct me if I'm wrong, but I think you just need to have 2 "rows" of workspaces, (e.g. 2x2 rather than 2x1).

---

### Post by SunnyRabbiera on 2009-03-17
Well the best way to get more themes is to head over to gnomelook:
[http://gnome-look.org/](http://gnome-look.org/)

Here is an explanation of the sections, I will explain the most common sections people use to theme Ubuntu:
Wallpapers is obvious, new wallpapers for your setup
GTK 1 and 2x sections: Changes the look and feel of your main interface, Ubuntu uses GTK2x by default so use GTK2x themes
Metacity: the window decoration (in Ubuntu the window decoration and user interface are separated) Metacity is what gives you your close/minimize/maximize buttons and titlebar.
Compiz/Beryl: both contain themes for an alternate window decoration engine (also called a window manager) called Emerald, Emerald is simpular to metacity but only works with desktop effects.
It offers users transparent window surroundings.
Emerald is not installed by default, it needs to be installed separately then later activated by modding a few things.
GDM themes: changes the look of your login theme.
Colour themes: provides extra color schemes, but really its not needed if you know how to edit the colors of your themes.

Compiz itself has something called compiz settings manager, if you need help using it we can aid you.

---

### Post by Therion on 2009-03-17
**The Basics of Customization**


Go to:  System/Preferences/Appearance

This opens the Appearance Manager... This is your gateway to a cooler looking Ubuntu.  Behold!!

Notice the Tabs.  You're on the Themes tab now, and changing themes is the easiest way to make-over the total look.  Don't miss the "Customize" button though, down at the bottom.  

Here you can play around with different individual *elements* of installed Themes (things like Window borders and such).  You can also change things like your Cursor and/or Icon set.  

To install NEW themes or Icon sets that you can then play with, you just download them (from Gnome-Look, linked above) and then drag & drop the file ONTO the theme Manager (Themes tab, even for Icon sets you download).  

If you get an error message that what you're trying to install "Doesn't Appear to be a Valid Theme", try right-clicking on the file, then on "Extract Here" and then drag & drop the resultant FOLDER onto the Appearance Manager.  If still no joy post back for further assistance.

---

### Post by suitedaces on 2009-03-17
> **Scubdup said:**
> Please can someone explain the different options and resources to me?

I've found some nice wallpapers and changed the desktop background, and I've downloaded Compiz from the repositories and enables a cool cube effect thing for when I change desktops (but it only works horizontally, not in 360°) and now I'm trying to do other stuff.

Is there a decent list of the most complete themes available? Ie the ones that have no bugs but do significantly cool things with the desktop?

How do I set up the cube that rotates in more than one plane? And how do I give it a cool backdrop?

If you have cube effect enabled, make sure there are 4 workspaces in the bottom corner (right click and edit preferences if not), then use Ctrl+Alt+Left mouse button to spin the 3d cube. For some reason it only works with my usb mouse and not the touch pad button.

---

### Post by Scubdup on 2009-03-17
Thanks a lot. All those replies are helpful. My pronblem was I wanted to know what I could do but wasn't sure exactly what I wanted. Thanks for all the good starting points!

---

### Post by Scubdup on 2009-03-19
Is there a tutorial about pimping Ubuntu somewhere?

When I first found Ubuntu I was thoroughly impressed.

Now I have a slick wallpaper, a *cyclindrically distorted cube with tiered windows* effect going on in Compiz, and a mac-style Cairo-dock.

What I thought was a slick, functional OS is now just as slick but also better looking than a mac (IMO).

The pimping potential has come as a bit of a revelation and I'm sure other newbies would relish a comprehensive tutorial - I'm wondering if there's already one out there, before I start writing one.

Edit: Scratch that. [Overdrank's FAQ list]("http://ubuntuforums.org/showthread.php?t=809695") is pretty much perfect.

---

### Post by Scubdup on 2009-03-19
I'd like to write a sort of beginner's glossary to all the options for Overdrank's FAQ list. I'm aware the FAQ covers all points, but when I started looking out for what could be done I found it very confusing to see all these different names of programs that might overlap with others or entirely encompass another program's functionality.

I would have benefited from a simple explanation of the different options and how they fit together.

Working off SunnyRabbiera's very helpful summary I've so far got:

-----------------------------------------------------------------

***I&#8217;m new to Ubuntu. It seems like a slick operating system but it looks a bit drab next to its counterparts. I&#8217;ve heard a lot of terms about programs and systems that can help me spruce up my desktop. Can someone explain them?***

Themes, Wallpaper, icons, colour themes can all be changed in Ubuntu without the need for addition software. For more advanced changes you should consider the following:-

**Windows Manager** - draws windows and/or their borders (sometimes borders are left to a window decorator - see below). It also controls how they are displayed and interact with each other, and the rest of the desktop environment.

[INDENT][LIST]
[*]**Metacity** &#8211; is the lean windows manager that comes as default with Ubuntu

[*]**Compiz** &#8211; full name Compiz-Fusion - A more extensive Windows manager than the default Metacity. This allows for more impressive effects. You can only run one windows manager at a time. Compiz comes with a basic settings manager &#8211; esoterically named &#8220;Compiz Settings Manager&#8221;. For more comprehensive settings management you can use CompizConfig Settings Manager

[*]**Beryl** is an old manager project that has now merged with Compiz (to become Compiz-Fusion).
[/LIST][/INDENT]

**Windows Decorator** - used by window managers to improve the usability of a multi-windowed desktop

[INDENT][LIST]
[*]**gtk-window-decorator **&#8211; the default windows decorator. Using GTK2x Themes

[*]**Emerald** &#8211; (formerly known as cgwd, which stands for Compiz Generic Window Decorator) is a window decorator for the Compiz. Allows the user to install comprehensive theme packages written for Emerald[/INDENT][/LIST]
**GNOME Display Manager (GDM) **- Allows users to easily customize or troubleshoot login display settings by the use of themes.

**Additional Options**

[INDENT][LIST]
[*]**Docks** - A row of icons on the desktop used to launch programs or provide other information or functionality. **Cairo Dock**, **AWN** ("Avant Window Navgator"), and **Docky** are all popular port software.
[*]**Widgets** - desktop features (like a clock, calendar, system monitor etc)that can be added through various widget managers. **Screenlets** is the most popular desktop widget manager and allows the user to install different screenlet applications. Other options are **Gdesklets**. **Cairo Dock **(see above) has the option to detach its applications and place them on the widget layer, and in this way it can offer widgets.
[/LIST][/INDENT]

-----------------------------------------------------------------

I want to linkify most of the options so it's easy to find out more/install/get help on each feature.

---

