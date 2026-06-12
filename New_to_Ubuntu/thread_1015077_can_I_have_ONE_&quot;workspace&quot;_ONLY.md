---
title: "can I have ONE &quot;workspace&quot; ONLY?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by stickman51 on 2008-12-18
V 8.10 on an "eMachines" laptop, and updated.

I really don't multi-task all that much, and HATE it when windows fly off my screen at random. I've set my Workspace Preference at ONE Column and ONE Row, but that did not do it.

Can I set it to permanently use/show only ONE Workspace?

---

### Post by drs305 on 2008-12-18
Here are two settings you can check.

To change the setting in gconf-editor:
```

gconftool-2 --type integer --set /apps/metacity/general/num_workspaces "1"

```

If you are using compiz:
System, Preferences, CompizConfig Settings, Manager (or in terminal: ccsm )
General, Desktop Size, Horizontal Virtual Size, 1 & Vertical Virtual Size, 1.

Can you elaborate on windows "flying off the screen"? That sounds like a compiz effect which you can probably turn off.

---

### Post by decoherence on 2008-12-18
> **stickman51 said:**
> V 8.10 on an "eMachines" laptop, and updated.

I really don't multi-task all that much, and HATE it when windows fly off my screen at random. I've set my Workspace Preference at ONE Column and ONE Row, but that did not do it.

Can I set it to permanently use/show only ONE Workspace?

When I right click on the workspace switcher and select Preferences, I'm given a window that says "Number of Workspaces." Setting this to 1 doesn't do what you want?

Are you running Compiz (special desktop effects, drop shadows under windows, etc)? If so you may have to change a setting there. Hopefully someone who uses compiz can help you with that.

---

### Post by stickman51 on 2008-12-18
> **decoherence said:**
> When I right click on the workspace switcher and select Preferences, I'm given a window that says "Number of Workspaces." Setting this to 1 doesn't do what you want?

Are you running Compiz (special desktop effects, drop shadows under windows, etc)? If so you may have to change a setting there. Hopefully someone who uses compiz can help you with that.

As far as I know, I don't have Compiz. When I go to the prefs, I can reduce the Columns and Rows both to "1" but that does not solve the problem of reducing the number of Workspaces to ONE.

---

### Post by stickman51 on 2008-12-18
> **drs305 said:**
> Here are two settings you can check.

To change the setting in gconf-editor:
```

gconftool-2 --type integer --set /apps/metacity/general/num_workspaces "1"

```

If you are using compiz:
System, Preferences, CompizConfig Settings, Manager (or in terminal: ccsm )
General, Desktop Size, Horizontal Virtual Size, 1 & Vertical Virtual Size, 1.

Can you elaborate on windows "flying off the screen"? That sounds like a compiz effect which you can probably turn off.

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

Sorry, I've been into Ubuntu for only a few days. Noooby 100%.

I have not seen any "Compiz" so am not sure if I have it; don't think so.

The windows, as I said, sort of "fly" away, and for a split second there is a very small, empty "table-like" box with 2 side-by-side cells in it, double border.

I can try what you suggest though; do you mean "Applications | Accessories | Terminal" and then, after the prompt "......:~$ type that line:
gconftool-2 --type integer --set /apps/metacity/general/num_workspaces "1"

and then?

---

### Post by decoherence on 2008-12-18
> **stickman51 said:**
> As far as I know, I don't have Compiz. When I go to the prefs, I can reduce the Columns and Rows both to "1" but that does not solve the problem of reducing the number of Workspaces to ONE.

Hmmmmm..... you say you're using 8.10? Is it all up to date? It seems like we're looking at different windows when we look at the workspace preferences. I do not get an option for columns but I do get a line that says "Number of Workspaces".

aah.... you ARE running compiz! I just enabled it and I'm seeing what you're seeing.

If you aren't comfortable running the gconf command that drs305 posted (which looks like it should be fine) you can try the following.

Go to System > Preferences > Appearance and select the "Visual Effects" tab and set this to "None." Now try changing the number of workspaces as you have been. You should get a window similar to the one I described. Make the change then turn compiz back on if you want. Please let us know if the change sticks when you turn compiz back on.

I'd say this is a user experience bug. A user should be able to set the number of desktops with the same interface regardless of whether they use compiz or metacity.

---

### Post by drs305 on 2008-12-18
> **stickman51 said:**
> $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

Sorry, I've been into Ubuntu for only a few days. Noooby 100%.

I have not seen any "Compiz" so am not sure if I have it; don't think so.

The windows, as I said, sort of "fly" away, and for a split second there is a very small, empty "table-like" box with 2 side-by-side cells in it, double border.

I can try what you suggest though; do you mean "Applications | Accessories | Terminal" and then, after the prompt "......:~$ type that line:
gconftool-2 --type integer --set /apps/metacity/general/num_workspaces "1"

and then?

What you describe sounds like compiz. If you follow decoherence's instructions on how to turn off visual effects that will probably solve your problem.

As to your question about the command I gave you. It is a terminal command that will change a setting in gconf-editor. What it does is tell gconf to set your desktops to 1. You run the command once and don't have to do anything else.

If you want to manually change the setting via a gui-app, type this in a terminal:
```
gconf-editor
```
When it opens, click on the *apps* folder to expand it, then click on *metacity* (a windows manager), then *general*. If you look at the earlier command, you will see you are following the same path - this time graphically.

On the right side, you will see a setting for "num_workspaces". Highlight that. When you do, you can see a description of what the command does in the lower window. under "long description". If you double-click the number you can change it to whatever you wish.

You have now changed a setting via the gui, but see how much easier it was just to open the terminal and run the command. :-)  
Of course, you have to know the command!

---

### Post by stickman51 on 2008-12-18
Well, I was working on all the suggestions you all so kindly provided and then "Gord Haverman" came over and being a genius in various fields, I think he fixed it but I could not follow what he did. If he did not fix it, I'll come back here and continue. If anyone is interested, Gordon is at [email]ghaverla@materialisations.com[/email]
and [www.materialisations.com](www.materialisations.com)
Thanks again!

---

### Post by stickman51 on 2008-12-18
SOLVED, I'm 99% sure, the EASY WAY.

Here is what I got from the ELUG *Edmonton Linux Users Group*

Oh, no problem.  You must be running Compiz with all that eye candy fluff.  When you're running compiz the number of workspaces setting is disabled in the switcher applet.

The only way I know of fixing this is to right-click anywhere on your desktop and select "Change Desktop Background", then select the "Visual Effects" thumb-tab and then change your effects to none.  Then the number of workspaces option should be available in the workspace switcher applet.  Change it to one and then go back and re-enable your visual effects.

:)
Keehan.

again, THANKS LOADS to all you great guys and gals.

---

### Post by stchman on 2008-12-18
> **stickman51 said:**
> V 8.10 on an "eMachines" laptop, and updated.

I really don't multi-task all that much, and HATE it when windows fly off my screen at random. I've set my Workspace Preference at ONE Column and ONE Row, but that did not do it.

Can I set it to permanently use/show only ONE Workspace?

You are giving up an excellent feature of Gnome or KDE.  Multiple workspaces are the best.  Use them and you will wonder how you ever got along without them.

To reduce your # workspace right mouse click on the switcher in the lower right corner and go to properties, select number of workspaces to '1'.  Selecting rows and columns will only show how the workspace manager display in the lower right corner.

Also the mouse wheel functions as a workspace switcher as well.

---

### Post by stickman51 on 2008-12-18
> **stchman said:**
> You are giving up an excellent feature of Gnome or KDE.  Multiple workspaces are the best.  Use them and you will wonder how you ever got along without them.

To reduce your # workspace right mouse click on the switcher in the lower right corner and go to properties, select number of workspaces to '1'.  Selecting rows and columns will only show how the workspace manager display in the lower right corner.

Also the mouse wheel functions as a workspace switcher as well.

Yes, stchman; I agree that once I am comfortable with Ubuntu, it probably would be helpful to me too but I've been a Windows user for such a long time I find it hard to switch to Linux. BUT I sure WANT to.

---

### Post by stchman on 2008-12-18
> **stickman51 said:**
> Yes, stchman; I agree that once I am comfortable with Ubuntu, it probably would be helpful to me too but I've been a Windows user for such a long time I find it hard to switch to Linux. BUT I sure WANT to.

I find is somewhat funny that people want to switch to Linux as long as it acts EXACTLY like Windows.  What are your reasons to switch to Linux?  If you are looking for a "free" Windows then you are looking in the wrong place.

My reasons for switching to Linux were as follows:
1.  Wanted to expand my knowledge of PC OSes.
2.  Did not want to deal with Microsoft and their controlling ways.
3.  Was concerned with Windows security measures and how easily they appear to be broken.
4.  Got kind of sick of Windows XP getting corrupted and needing a reinstall.
5.  Linux offers a great deal of open source software that does everything I need.  Base Windows installs come with nothing.

Switching to Linux means embracing the differences and not wanting a Windows replica.

For the main PC users (surf web, check email, office apps) etc. Linux does the job just as well.  Things like multimedia works just as well.

The thing about multiple workspaces is that you do not have to use them unless you want to.

---

### Post by stickman51 on 2008-12-18
> **stchman said:**
> I find is somewhat funny that people want to switch to Linux as long as it acts EXACTLY like Windows.  What are your reasons to switch to Linux?  If you are looking for a "free" Windows then you are looking in the wrong place.

My reasons for switching to Linux were as follows:
1.  Wanted to expand my knowledge of PC OSes.
2.  Did not want to deal with Microsoft and their controlling ways.
3.  Was concerned with Windows security measures and how easily they appear to be broken.
4.  Got kind of sick of Windows XP getting corrupted and needing a reinstall.
5.  Linux offers a great deal of open source software that does everything I need.  Base Windows installs come with nothing.

Switching to Linux means embracing the differences and not wanting a Windows replica.

For the main PC users (surf web, check email, office apps) etc. Linux does the job just as well.  Things like multimedia works just as well.

The thing about multiple workspaces is that you do not have to use them unless you want to.

Fairly similar to you, stchman; only I LIKE XP very much and found nothing but trouble with Vista. Sadly, I can never leave Windows completely, my favorite programs are not compatible with Linux: Irfanview, Corel Paintshop Pro, Crimson Editor etc. But the more people switch, the more GOOD programs will come along for Linux, so I want to encourage that. The $$ cost of Windows is not an issue for me. But, being a Flatulus Antiquatus, I do not want to get into the geeky stuff; that's best left to the young, smart crowd.

---

