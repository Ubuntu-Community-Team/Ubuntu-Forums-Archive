---
title: "Set the icon of a custom app launcher from a script"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by uligraf on 2009-04-30
Hi, 

I started to custumize my newly installed Ubuntu 9.04, by adding two launchers to the upper panel (starting .sh scrpts). Both change the default automatic booting (XP for the family, Ubuntu for me) after system  restart. It works fine, but I would like to change the Icon of both after changing the boot preference or, even better, make one launcher toggling between the two states and showing the icon of the select OS. So, I would would need to know: 

:confused:- where  are the files describing those launchers stored ? 

:confused:- which applications could I use to change those files from a .sh script?

Thanks

Uli

PS: Yes, I am an absolute beginner concerning Ubuntu, Gnome, etc., but what I saw so far makes me eager to learn a lot!

---

### Post by TheLions on 2009-04-30
> **uligraf said:**
> Hi, 

I started to custumize my newly installed Ubuntu 9.04, by adding two launchers to the upper panel (starting .sh scrpts). Both change the default automatic booting (XP for the family, Ubuntu for me) after system  restart. It works fine, but I would like to change the Icon of both after changing the boot preference or, even better, make one launcher toggling between the two states and showing the icon of the select OS. So, I would would need to know: 

:confused:- where  are the files describing those launchers stored ? 

:confused:- which applications could I use to change those files from a .sh script?

Thanks



Uli

PS: Yes, I am an absolute beginner concerning Ubuntu, Gnome, etc., but what I saw so far makes me eager to learn a lot!

right click on launcher and click on left icon on new opened windows. Then click on search button and select image which you want to represent that launcher.

you can find windows logo:
[http://images.google.hr/images?q=windows+logo&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=hr&tab=wi](http://images.google.hr/images?q=windows+logo&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=hr&tab=wi)

and ubuntu logo:
[http://images.google.hr/images?hl=hr&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&um=1&sa=1&q=ubuntu+logo&btnG=Pretra%C5%BEi+slike&aq=f&oq=](http://images.google.hr/images?hl=hr&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&um=1&sa=1&q=ubuntu+logo&btnG=Pretra%C5%BEi+slike&aq=f&oq=)

---

### Post by sdennie on 2009-04-30
They are in ~/.gnome2/panel2/default/launchers.  The format of the desktop files there is very straightforward and using a simple script it should be very easy for you to accomplish what you are trying to do.

---

### Post by uligraf on 2009-04-30
Many Thanks sdennie and TheLions, both very helpfull responses. Now I need to find an editor for those desktop configuration files, which works from command line. Will search for it an come back to here if I can't find.

Uli

---

### Post by Niniel on 2009-04-30
Cool idea, but why not just set the default to Windoze and be done with it? 
And how his this supposed to work? Can you always be certain that after a Windows/Linux user shuts down, a Linux/Windows user will start the computer next? And does this actually work from Windows?

---

### Post by uligraf on 2009-04-30
Niniel, 

Why? Because I have to deal with PCs about 2000 km (more than 1000 miles) away. I have two PCs in my wife's flat and two here, but need access to all and want to switch to Ubuntu without figthing all the time against the XP family members. So, I need dual boot remotely, allowing me to decide via terminal sessions from both XP and Ubuntu which OS should show up next time. It already works, but editing with sometimes slow connections is boring.

How it works: a tiny Fat32 partition containing a menu.lst copied from the original grub. Editing the original grub menu.lst by adding a new title which just loads the menu.lst from this Fat32 partitions where the default entry is set to what you want. It's not my idea, but, nevertheless quite genious. Details here:
[http://www.ibm.com/developerworks/linux/library/l-osswitch/]("http://http://www.ibm.com/developerworks/linux/library/l-osswitch/")

[Digg]("http://digg.com/linux_unix/Automate_OS_switching_on_a_dual_boot_Linux_system") the guy, he merits it. It works like charm, but you have to deal with some pecularities of the different grubs. 8.10 for example has a divider (between Ubuntu titles and XP) which counts as a title, where jaunty produces a menu.lst (or interpretes) the divider not as a a title. 

What I want now is: having a small desktop item on both XP and Ubuntu, which is set to the actual autoboot OS (indicatted by an icon) a set by reading the actual default setting in the menu.lst in the Fat32 partition (which I call BOOTCONTROL). Clicking the item should start a script (Batch) modifying (by copying from a perepared .lst file) the BOOTCONTROL menu.lst and setting the icon to the show the other OS. The final stage could be to remind you to set it before you restart or shut down the PC (which certainly would be easy in Gnome-Ubuntu, but quite tricky in XP). 

I'm still dealing with the Ubuntu setup: I have actually two Launchers in the upper panel, which switch perfectly to the new auto boot setting. With the  help of above friends I know where those custom launchers are stored, that they are .xml files which can be edited be commandline (sh. scripts), but I have to know more about gnome: Are those items reset during the start of the desktop (or only if you go to edit them via left mouse click)? Who decides and knows their position? How do reset them on startup? etc. Maybe a Gnome specialist is listening and finds the idea worth to help!!

Uli

---

### Post by uligraf on 2009-05-01
I thought that I could just overwrite or rename the launchers in order to toggle between both after having switched the default OS to boot. However, I get following message when trying to rename from a terminal

> uligraf@ulih-linux:~/.gnome2/panel2.d/default/launchers$ ls
firefox.desktop   nextboot.desktop~    nextboot.sh.desktop~
nextboot.desktop  nextboot.sh.desktop
[email]uligraf@ulih-linux:~/.gnome[/email]2/panel2.d/default/launchers$ rename nextboot.desktop nextub.desktop
Bareword "nextboot" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "desktop" not allowed while "strict subs" in use at (eval 1) line 1.

I can remove one of the items from :~/.gnome2/panel2.d/default/launchers but this has no effect on the panel. 

So, I believe that those .desktop files in :~/.gnome2/panel2.d/default/launchers are just copies of the items which are created when you change the items on the panel, because they re-appear once I have edited them by right-click them on the panel. 

Any hints where and how I can access to the active items and manipulate them from a .sh script.

Thanks

Uli

---

### Post by Niniel on 2009-05-01
Hello Uli,

thank you very much for taking the time to explain what you're doing. Very impressive. And good luck with refining this system.

---

### Post by uligraf on 2009-05-02
:confused: Hi again,

I made some progress, but still would need help: I now understand the custom panel launchers are stored in
~/.gnome2/panel2/default/launchers. However, changing them there doesn't have direct effect to the panel. The object itself is controlled in 
~/.gconf/apps/panel/objects/object_x/%gconf.xml (where x is a number).
The %gconf.xml contains the information concerning the position and refers to the .desktop file in ~/.gnome2/panel2/default/launchers. So I can change the icon and action either by replacing the %gconf.xml with another, pre-prepared .xml file or editing the file. However, this takes effect only after re-login, i.e. after restarting the x server. I assume that the actual object is still in another location, because editing-moving-etc the item via left-mouse-click updates the characteristics immediately, but doesn't leave a trace in ~/.gconf/apps/panel/objects/object_x/%gconf.xml until next login. 

So two new questions:
- where are the actual objects located?
- is it possible to re-actualize the panel so that it re-reads the instructions in ~/.gconf/apps/panel/objects/object_x/%gconf.xml without re-login?

A third, more general question: Is there an application which monitors (for example in a terminal) the commands provoked by actions on the desktop so that I can understand what actually happens when I, for example, change the attributes of such a custom panel item. 

Thanks

Uli

---

### Post by rikxik on 2009-11-21
I know this is a bit old thread. But I'm trying to do exactly the same thing - dynamically change the launcher icon using some script (kind of toggle thing). My questions are also the same:

- where are the actual objects located?
- is it possible to signal the panel so that it re-reads the instructions in ~/.gconf/apps/panel/objects/object_x/%gconf.xml without re-login/panel restart?

Has anyone else successfully done this?

---

### Post by bobodod on 2010-05-26
I'd like to resurrect this thread to see if anyone can answer these questions.

uligraf, rikxik, have either of you figured this bugger out?


Thanks much.

---

### Post by blue_bullet on 2010-10-16
I am looking for the same thing.  The volume control indicator applet icon changes when you mute the volume.  I do not know where the code for that is stored, but that accomplishes the icon toggling we are looking for.  I have a script written in Regina rexx that toggles the volume off and on.  My wife was complaining about all my email sounds going off in the middle of the night so I wrote a routine to force volume off or on and have it scheduled to force off at midnight and force on at 7am via cron.  Now she has a 7 am alarm ;->  I also have the routine set up as launcher on the task bar so it will toggle the volume on/off. I thought it would be nice to indicate the mute status by changing the icon. 

Any one know how to do this?  I realize this is like "Countin' Flowers on the Wall", but curious minds want to know.

---

### Post by kapetr on 2011-02-20
I would like to make similar thing.

Also - is there really nobody who knows, how to change icon in panel dynamically ?

e.g. I had made a script to record ma VOIP calls audio - but my button on panel is static - I don't know if I am recording or not. So I need to change the icon in this script to indicate this.

PLEASE HELP.

--kapetr

---

