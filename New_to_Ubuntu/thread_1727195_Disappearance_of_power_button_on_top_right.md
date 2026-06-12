---
title: "Disappearance of power button on top right"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by de_island on 2011-04-12
Hello folks.

I'm having a bit of trouble with the power button that previously was in the top right corner of my screen (far right button on panel). This being the button which when clicked would give the option of shutting down, sleeping, hibernating, etc.

This button randomly disappeared the other day for some reason, and I can't work out how to get it back.

I assumed that right clicking the panel and then going to 'add to panel' would have it, but apparently it doesn't. The only similar button appears to be a simple shutdown button.

Any help would be appreciated.

---

### Post by de_island on 2011-04-12
I should probably mention that I'm using 10.10

---

### Post by pcwiz11 on 2011-04-12
That's strange. Have you tried turning the computer off and then on again?

---

### Post by Jechem on 2011-04-12
try:

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

this will reset the panels in their default settings like a fresh install

---

### Post by de_island on 2011-04-12
> **pcwiz11 said:**
> That's strange. Have you tried turning the computer off and then on again?

Was that an IT Crowd quote? ;-)

And yes, multiple times.

> **Jechem said:**
> try:

```
gconftool --recursive-unset /apps/panel && killall  gnome-panel
```this will reset the panels in their default settings  like a fresh install

I tried that just there, and it didn't make any changes. It's exactly as it was. It did reload the panel, but it didn't make any changes at all. The power button is still missing, and all my added buttons (Firefox, Chrome, etc.) are still there (which I assume your "fresh install" method should have removed).

---

### Post by Hippytaff on 2011-04-12
You could try uninstalling and reinstalling it. open a terminal and do```
sudo apt-get remove gnome-panel && sudo apt-get install gnome-panel
```

---

### Post by bfmetcalf on 2011-04-12
> **de_island said:**
> Hello folks.

I'm having a bit of trouble with the power button that previously was in the top right corner of my screen (far right button on panel). This being the button which when clicked would give the option of shutting down, sleeping, hibernating, etc.

This button randomly disappeared the other day for some reason, and I can't work out how to get it back.

I assumed that right clicking the panel and then going to 'add to panel' would have it, but apparently it doesn't. The only similar button appears to be a simple shutdown button.

Any help would be appreciated.

If you right click on the panel and click "add to panel" add the indicator applet (session), that should get it back up there.

---

### Post by de_island on 2011-04-12
> **Hippytaff said:**
> You could try uninstalling and reinstalling it. open a terminal and do```
sudo apt-get remove gnome-panel && sudo apt-get install gnome-panel
```

I ran that and it didn't make any changes even though it went through the full uninstall and re-install. The panel didn't even reload like it did with Jechem's solution. 

Are we definitely talking about the same panel? It's the one at the top with the Ubuntu symbol, Applications, Places, System and the icons.

---

### Post by Hippytaff on 2011-04-12
THat's odd...maybe there is a config file in your home folder holding the setting. I can't check what its called or where it is because I'm in work (on a windows box) but if you open a terminal and do pwd to make sure you are in the home folder then do```
ls -a | less
``` you can scroll through and see if you can find the gnome-panel config file. 
 
or you could try doing it this way```
sudo apt --purge remove gnome-panel && sudo apt-get install gnome-panel
``` That should remove the config files as well and statrt from scratch.
 
I have used a sledghammer to crack a nut when I buggered up my panel one time and reinstalled the whole desktop ```
 sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop
```. obviously you might want ot save this as a last resort.

---

### Post by rvchari on 2011-04-12
> **de_island said:**
> Hello folks.

I'm having a bit of trouble with the power button that previously was in the top right corner of my screen (far right button on panel). This being the button which when clicked would give the option of shutting down, sleeping, hibernating, etc.

This button randomly disappeared the other day for some reason, and I can't work out how to get it back.

I assumed that right clicking the panel and then going to 'add to panel' would have it, but apparently it doesn't. The only similar button appears to be a simple shutdown button.

Any help would be appreciated.


i ll tell you how i solve this... i often resort to this as and when i find my panel icons not set right or behaving bad.

i presume you r using top panel. if yes then right click and make the position to bottom.
this panel shifts to bottom.
then right click on it and add new panel (by default, it will install a blank panel on top)
then you add whatever you want...by selecting add to panel option.
a) top left: main menu, global menu applet
b) top right: notifier, indicator etc.

if you add main menu app then you may not need the power button in top right corner (main menu has it all), still if u need it, then go ahead and add it.
your problem should be solved.

---

### Post by dcsoldschool53 on 2011-04-12
[B]Maybe this will help you out. It restores the gnome panel back to the default settings.

[http://ubuntuforums.org/showthread.php?t=1690239](http://ubuntuforums.org/showthread.php?t=1690239)
[/B]

---

### Post by de_island on 2011-04-12
> **bfmetcalf said:**
> If you right click on the panel and click "add to panel" add the indicator applet (session), that should get it back up there.

The indicator applet just gives me a duplicate of my sound and mail icons. No inclusion of the elusive power icon.


> **rvchari said:**
> i ll tell you how i solve this... i often resort  to this as and when i find my panel icons not set right or behaving  bad.

i presume you r using top panel. if yes then right click and make the position to bottom.
this panel shifts to bottom.
then right click on it and add new panel (by default, it will install a blank panel on top)
then you add whatever you want...by selecting add to panel option.
a) top left: main menu, global menu applet
b) top right: notifier, indicator etc.

if you add main menu app then you may not need the power button in top  right corner (main menu has it all), still if u need it, then go ahead  and add it.
your problem should be solved.

I tried that, and the button wasn't included. I can, of course, live without it but it was convenient to have and I'd like to know why exactly it chose to run off.

> **dcsoldschool53 said:**
> [B]Maybe this will help you out. It restores the gnome panel back to the default settings.

[http://ubuntuforums.org/showthread.php?t=1690239](http://ubuntuforums.org/showthread.php?t=1690239)
[/B]

I then tried this, only to get the following error:

Error while parsing options: Unknown option -recursive-unset.

---

### Post by Hippytaff on 2011-04-12
> Error while parsing options: Unknown option -recursive-unset. recursive should have to dashes before it --recursive

---

### Post by gandaran on 2011-04-12
are you talking about the power option it the system menu or the power button you add to panel?
the button you add to panel just click on the panel and chose the power applet in add to panel option, this button is not on panel by default you have to add it.

---

### Post by dcsoldschool53 on 2011-04-12
[B]two dashes with no space between them, *–-recursive-unset /apps/panel*
[/B]

---

### Post by de_island on 2011-04-12
> **gandaran said:**
> are you talking about the power option it the system menu or the power button you add to panel?
the button you add to panel just click on the panel and chose the power applet in add to panel option, this button is not on panel by default you have to add it.

The grey power button which was at the top right of the screen when I first installed Ubuntu. Not the red button that can be added.



Just so you know, I followed the instructions on [http://ubuntuforums.org/showthread.php?p=10667546#post10667546](http://ubuntuforums.org/showthread.php?p=10667546#post10667546) and it completely ruined my panel. It deleted everything except for two buttons that I recently added and it added a quarter length panel just below the main one. I left a message asking the original poster to review it, but is it worth flagging it?

Thanks again to Jechem for his piece of code which managed to reset it back to something resembling normal.

---

### Post by safarin on 2011-04-12
Hi de_island,

I also face this problem and found some useful scripts...
You could refer to this thread

[http://ubuntuforums.org/showthread.php?t=1716534&page=3]("http://ubuntuforums.org/showthread.php?t=1716534&page=3")

I already upload that scripts in that thread. 
Hope this could solve your problem.

---

### Post by bfmetcalf on 2011-04-12
> **de_island said:**
> The indicator applet just gives me a duplicate of my sound and mail icons. No inclusion of the elusive power icon.




I tried that, and the button wasn't included. I can, of course, live without it but it was convenient to have and I'd like to know why exactly it chose to run off.



I then tried this, only to get the following error:

Error while parsing options: Unknown option -recursive-unset.

There should be 2 indicator applets one has (session) after it.  That is the one you want.

---

### Post by dcsoldschool53 on 2011-04-12
[quote=safarin]I also face this problem and found some useful scripts...
You could refer to this thread

[http://ubuntuforums.org/showthread.php?t=1716534&page=3](http://ubuntuforums.org/showthread.php?t=1716534&page=3)

I already upload that scripts in that thread. 
Hope this could solve your problem.[/quote]

This is just what the Doctor ordered, and thank you for the script. :D

---

### Post by de_island on 2011-04-12
> **safarin said:**
> Hi de_island,

I also face this problem and found some useful scripts...
You could refer to this thread

[http://ubuntuforums.org/showthread.php?t=1716534&page=3](http://ubuntuforums.org/showthread.php?t=1716534&page=3)

I already upload that scripts in that thread. 
Hope this could solve your problem.

I ran that programme, and it reset it, but without the button and with the error:

```
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

```

I reinstalled FastUserSwitchApplet, ran PanelRestore again and it's back. Thanks Safarin. Now let's hope that it doesn't run off again. =)

> **bfmetcalf said:**
> There should be 2 indicator applets one has (session) after it.  That is the one you want.

I was wondering why the original post had (session) included... It wasn't  there. I just had the regular indicator applet. Reinstalling FastUserSwitchApplet put it back in the list.

---

### Post by bfmetcalf on 2011-04-12
> **de_island said:**
> I ran that programme, and it reset it, but without the button and with the error:

```
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

```I reinstalled FastUserSwitchApplet, ran PanelRestore again and it's back. Thanks Safarin. Now let's hope that it doesn't run off again. =)



I was wondering why the original post had (session) included... It wasn't  there. I just had the regular indicator applet. Reinstalling FastUserSwitchApplet put it back in the list.

So, does that mean it worked for you?

---

### Post by de_island on 2011-04-12
> **bfmetcalf said:**
> So, does that mean it worked for you?

Yes, yes it did. :D

It didn't work at first, but then I installed the missing (whatever you would call fastuserswitchapplet), re-ran the programme and then it worked.

---

### Post by bfmetcalf on 2011-04-12
> **de_island said:**
> Yes, yes it did. :D

It didn't work at first, but then I installed the missing (whatever you would call fastuserswitchapplet), re-ran the programme and then it worked.

Glad it worked for you.  This was one of the first threads I could help solve!  Makes it even more fun learning about Linux/ubuntu.

---

### Post by Sidewinder1 on 2011-04-12
I have had the exact same problem; the default shutdown icon would periodically disappear completely or, what is even more strange, appear in a munged fashion (and more importantly be "unclickable").
As you can see by my attachment, I solved this by adding to panel the RED shut-down (got tired of [alt-prt-screen-shift REISUB]), icon/applet.
The really funny thing is that the default, gray, version 'magically' reappeared after a reboot or two and I haven't had any problems since.
Please note that this has happened only twice since I upgraded (through update mgr.) from Hardy to Lucid.
Curiouser and curiouser...
I hope this helps others that may be experiencing the same behavior.

Side

[ATTACH]188829[/ATTACH]

---

### Post by safarin on 2011-04-12
> **de_island said:**
> Yes, yes it did. :D

It didn't work at first, but then I installed the missing (whatever you would call fastuserswitchapplet), re-ran the programme and then it worked.

Nice! :popcorn:

---

### Post by safarin on 2011-04-12
> **Sidewinder1 said:**
> I have had the exact same problem; the default shutdown icon would periodically disappear completely or, what is even more strange, appear in a munged fashion (and more importantly be "unclickable").
As you can see by my attachment, I solved this by adding to panel the RED shut-down (got tired of [alt-prt-screen-shift REISUB]), icon/applet.
The really funny thing is that the default, gray, version 'magically' reappeared after a reboot or two and I haven't had any problems since.
Please note that this has happened only twice since I upgraded (through update mgr.) from Hardy to Lucid.
Curiouser and curiouser...
I hope this helps others that may be experiencing the same behavior.

Side

[ATTACH]188829[/ATTACH]

This "red button" could be annoying, not good-looking.. :p

---

