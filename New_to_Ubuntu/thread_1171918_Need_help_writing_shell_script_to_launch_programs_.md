---
title: "Need help writing shell script to launch programs from desktop"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by mal1958 on 2009-05-27
Posting this here because I really don't know where to post it.

I need to get some basics on shell scripts.  I have Xubuntu 9.04, wine latest, and have installed the following through wine:  Caesar 3, Pharaoh, Write it Now 3.  I need to do some kind of script to beable to launch these programs from the desktop.  I would like to link the script to an Icon that I can double click to launch it.  I need to know if this is possible, and if so, what do I use to write the script file, where do I put the script, etc...

I am a NOOB so please be gentle with me.

Mike

---

### Post by anewguy on 2009-05-27
What do you need in the script?  If all you want is to put an icon on the desktop to launch a wine application instead of going through the menus, you can do that without a script.  Simply locate the item in the menu (in regular ubuntu [gnome desktop] Applications/Wine/Programs) then right click on the menu item and select "Add This Launcher to Desktop".  If you need to, you can then go to the desktop and change the icon.  Otherwise just click on the item on the desktop and it should go.

Dave :)

---

### Post by Didius Falco on 2009-05-27
Hi,

I think this guide will help you out:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Basically, you can just create Launchers on the desktop and use the command ```
wine /path/to/programname.exe 
```.

You should be able to change the Icons just like you would any other Launcher - Right-click the Launcher, go to **Properties**, click the icon picture and find the icon you want to use.

I'd still recommend reading the guide, though. Who knows what other tasty tips it will hold?

Regards,

Didius

---

### Post by clonne4crw on 2009-05-27
You mean a basic script that will just launch a bunch of programs? I've got some steps to follow:

1) Create a text file, name it something like script.sh [Replace 'script' with whatever], make the first line of it look like this:

```

#! /usr/bin/sh

```
That line just signifies that the file is an executable script

2)Now, let's just add lines that point to the programs you want to launch.

Right-click any of you desktop icons and select 'Properties'
Under the 'Basic' tab, you will find the section that contains  the command.

Copy whatever is in that box and paste it into your script.

Do this for everything that you want launched when you run the script.

3)Next, we save the script itself somewhere. I'll save it on my desktop for now, so it will be located in /home/[username]/Desktop/script.sh

4)Before we test it, we have to run a final command to make it executable:

```

$ chmod 755 /home/(username)/Desktop/(scriptname).sh

```
Or whatever the path to it is.

Now, we double-click the script, select 'Run', and it will launch what you put in there!

5) GO ahead and try it out, modify it to you heart's content. You could create a launcher for it, and change its icon, whatever.


---------------------------------------
Now, I imagine that clicking 'Run' each time will get annoying, but I'm a little tired right now to find a way to disable that. I'll look tomorrow. ;)


#####################EDIT########################
I started writing this when there were no replies to the post, now there are 4. I hope this at least helps you.

---

### Post by WhiskyChris on 2009-05-27
If you right-click on the desktop then one of your options is "Create Launcher". This will bring up a dialogue which will create an icon which you can double click to run a certain program.

The main thing you need to find is the location of the program so you can enter that into the "command" box. If you're not sure you can open a terminal and type

```
which xxx
```

where xxx is the name of the program. If you're not sure of the program name (usually not the full name as you've given) then guess the start and press TAB a couple of times and it will either complete the name or give you some options.

You can change the icon of the launcher by clicking on the image and finding the icon of your choice.

Hopefully this is what you were after, if not or if you have any questions then just ask!

---

### Post by kerry_s on 2009-05-27
it's not that complicated. for the command just put:

**wine "C:\Program Files\path\to\game"**

you might also want to checkout "playonlinux" its a front end for wine, it's in the repos so you can install it from synaptic or:
**sudo apt-get install playonlinux**
in a terminal.

---

