---
title: "main menu"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-10
How can I place locations (places) and system higher up the main menu?Now they're at the bottom.I'd like to move them where the orange arrow is pointing to.

---

### Post by laidback on 2009-11-10
Have a look at System>Preferences>Main-menu. Don't think it does exactly what you want but it does give the option for new menus which may help.

---

### Post by dzon65 on 2009-11-10
Places is not in the main menu editor.System is,but not places.Isn't there a way whith which I can add places to the main menu and then manually configure it?

---

### Post by ukripper on 2009-11-10
> **dzon65 said:**
> Places is not in the main menu editor.System is,but not places.Isn't there a way whith which I can add places to the main menu and then manually configure it?

You can play around with gconf-editor, just run from command line:
```
sudo gconf-editor
```

and see if that makes any difference for you.

---

### Post by dzon65 on 2009-11-10
I did but can't find anything that applies to this issue.Perhaps I'm looking in the wrong place.

---

### Post by Yanno on 2009-11-10
> **dzon65 said:**
> I did but can't find anything that applies to this issue.Perhaps I'm looking in the wrong place.

What exactly are you gonna do?To move a panel or to create a new panel?Right click on the panel you want to move and choose property then you will move it,right click on the place where you want to add a panel then you will get a new one and to configure it!

---

### Post by Ms_Angel_D on 2009-11-10
This doesn't answer your question about the gnome menu but have you heard of [Ubuntu-System-Panel]("http://code.google.com/p/ubuntu-system-panel/w/list")? I use it on any and all ubuntu installs I do, you can customize the layout quite nicely and easily.

---

### Post by SunnyRabbiera on 2009-11-10
Is that the gnome menu that is designed to look like vistas menu (gno menu?)
I dont think there is much you can customize with it, or the default menus for that matter, wish there was... sorry.

---

### Post by dzon65 on 2009-11-10
Yep,I'm afraid it's like that.Actually,I don't even use it but for them guys coming from windows,it's a bit more familiar to have the menu that way.I'll take a closer look at that ubuntu menu editor,ubuntu system panel.Thanks for the replies everyone.

---

### Post by dzon65 on 2009-11-10
Yanno,I was just looking for a way to replace (place them under the youtube icon see picture) places and system in the main menu.

---

### Post by Ms_Angel_D on 2009-11-10
> **SunnyRabbiera said:**
> Is that the gnome menu that is designed to look like vistas menu (gno menu?)
I dont think there is much you can customize with it, or the default menus for that matter, wish there was... sorry.

> **dzon65 said:**
> Yep,I'm afraid it's like that.Actually,I don't even use it but for them guys coming from windows,it's a bit more familiar to have the menu that way.I'll take a closer look at that ubuntu menu editor,ubuntu system panel.Thanks for the replies everyone.

> **dzon65 said:**
> Yanno,I was just looking for a way to replace (place them under the youtube icon see picture) places and system in the main menu.

ubuntu-system-panel is much better than gno menu and looks nothing like it. It's highly configurable and has plugins such as search, terminal, quick notes, and calculator. On my systems it completely eliminated the need for panel launchers because of it's compact list feature.

[[img]http://img35.imageshack.us/img35/1008/screenshot003ur.th.png[/img]](http://img35.imageshack.us/img35/1008/screenshot003ur.png)
[[img]http://img43.imageshack.us/img43/9456/screenshot004jd.th.png[/img]](http://img43.imageshack.us/img43/9456/screenshot004jd.png)
[[img]http://img690.imageshack.us/img690/9126/screenshot005t.th.png[/img]](http://img690.imageshack.us/img690/9126/screenshot005t.png)
[[img]http://img69.imageshack.us/img69/4860/screenshot006f.th.png[/img]](http://img69.imageshack.us/img69/4860/screenshot006f.png)

This is gnomenu
[[IMG]http://img198.imageshack.us/img198/5129/44367043.th.png[/IMG]](http://img198.imageshack.us/i/44367043.png/)

---

### Post by dzon65 on 2009-11-10
Miss Angel.I've installed it but I have a problem with it.When I close it,the window border remains on the screen.And it won't go away until I reboot.So,I want to uninstall it.I did what they suggested on their website but terminal doesn't recognize it.Do you have any idea how to do it?(I downloaded the file to my desktop.)

---

### Post by Ms_Angel_D on 2009-11-10
> **dzon65 said:**
> Miss Angel.I've installed it but I have a problem with it.When I close it,the window border remains on the screen.And it won't go away until I reboot.So,I want to uninstall it.I did what they suggested on their website but terminal doesn't recognize it.Do you have any idea how to do it?(I downloaded the file to my desktop.)

Window border? There may be a solution to your issue, just so you know USP has a support forum here On the Ubuntu forums. [http://ubuntuforums.org/forumdisplay.php?f=156](http://ubuntuforums.org/forumdisplay.php?f=156)

Did you try checking "hide window border"? That might work even you have reboot to get rid of it the first time.

If the removal instruction from the website don't work I'm not sure, I would post in the forums, they are very quick to respond and very quick to resolve issues.

---

### Post by P123 on 2009-11-10
My problem with all of the menus mentioned is that I can not get the search panel at the bottom of the menu (the same as vista).  Does anybody have any ideas?  I am using 9.04 .

---

### Post by Ms_Angel_D on 2009-11-10
> **P123 said:**
> My problem with all of the menus mentioned is that I can not get the search panel at the bottom of the menu (the same as vista).  Does anybody have any ideas?  I am using 9.04 .

UPS has the search feature not sure why the issues?

Right click on the menu and click preference, then under the applications tab make sure you don't have hide search checked. Then make sure that the search command matches this:

```
gnome-search-tool --named=SEARCH_STRING --start
```

---

### Post by dzon65 on 2009-11-10
P,what do you mean with "at the bottom"?Is it like the screenshot I added or do you mean with usp?

---

