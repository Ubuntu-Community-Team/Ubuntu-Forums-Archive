---
title: "Taskbar?!"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by applecake on 2009-04-07
Hey!

Is there a way that I can make my tasklist (the normal gnome-bottom-tasklist..not some dock..) to only show icons??

---

### Post by Ms_Angel_D on 2009-04-07
Hi applecake, 

We call these panels ;)

if your wanting to remove the window list, look the far left of the panel you should see a little line next to the show desktop button right click on it and click remove from panel. You can re add it by right clicking on the panel and clicking add to panel and selecting window list.

Hope this helps,

Angel

---

### Post by ninjapirate89 on 2009-04-07
> **MetalHellsAngel said:**
> Hi applecake, 

We call these panels ;)

if your wanting to remove the window list, look the far left of the panel you should see a little line next to the show desktop button right click on it and click remove from panel. You can re add it by right clicking on the panel and clicking add to panel and selecting window list.

Hope this helps,

Angel

I think what the OP means is that instead of having window list they would like their bottom panel to only show the icons of programs they have open. I don't know how you could go about doing this though.

---

### Post by kanikilu on 2009-04-07
Unfortunately the Window List applet doesn't have an option to display icons only.

Some of your options are:

- [Gnome-Do](https://launchpad.net/do) (which has a dock implementation called "Docky")
- [Avant Window Navigator (AWN)](https://launchpad.net/awn)
- [Task Dock](http://ubuntuforums.org/showthread.php?t=986338) - Gnome applet, but you have to compile yourself...

I've tried Gnome-Do and AWN, and both have their pros and cons, but ultimately weren't for me, so I went back to the default gnome-panels. I haven't tried the 3rd option...

---

### Post by Tibuda on 2009-04-07
[http://www.gnome-look.org/content/show.php/DockBar?content=97822](http://www.gnome-look.org/content/show.php/DockBar?content=97822)

---

### Post by blue_shift on 2009-04-07
Regarding the XFCE4 panel there's an option for 'Show Application Names' which, when unchecked, yields the result you describe. I expect gnome-panel is similar?

---

### Post by ninjapirate89 on 2009-04-07
> **blue_shift said:**
> Regarding the XFCE4 panel there's an option for 'Show Application Names' which, when unchecked, yields the result you describe. I expect gnome-panel is similar?

This option is not available in gnome's panel.

---

### Post by Ms_Angel_D on 2009-04-07
> **ninjapirate89 said:**
> I think what the OP means is that instead of having window list they would like their bottom panel to only show the icons of programs they have open. I don't know how you could go about doing this though.

Hmm You might be right I was thinking the OP meant they just wanted shortcuts there. I'm sorry if I misunderstood.

---

### Post by Jakey_TheSnake on 2009-04-07
If you want to conserve space, remove the "Window List" from the dock by right clicking the separator before your first window and hitting remove, then adding to panel "Window Selector". 

Other than that, the "Window List" screenlet works exactly as you have described:
```
sudo apt-get install screenlets
```

Applications > Accessories > Screenlets, select Window List, Select "Start" and "Auto start on login", move it where you want (although you can't place it over the panel) and then lock it in place and set attributes via the properties/preferences option.

---

### Post by batharoy on 2009-04-07
Remove the Windows List applet as stated above and add the Windows Selector applet.
This will show an icon of the currently focused window, click on the icon and a list of all open windows will appear.

---

### Post by ninjapirate89 on 2009-04-07
> **danielrmt said:**
> [http://www.gnome-look.org/content/show.php/DockBar?content=97822](http://www.gnome-look.org/content/show.php/DockBar?content=97822)

This looks like the solution but I don't know how to install it.

Edit -> I got it but the method posted just above ^ works without installing anything.

Edit2 -> I've tried both and personally I think the applet found on gnome-look works better.

---

### Post by applecake on 2009-04-08
Hey all! Just had to say thanks for all your answers.. Ill probably do with an ordinary AWN or something..

> **MetalHellsAngel said:**
> Hi applecake, 

We call these panels ;)


Are you really sure?? :p

---

### Post by Jakey_TheSnake on 2009-04-08
> **applecake said:**
> Hey all! Just had to say thanks for all your answers.. Ill probably do with an ordinary AWN or something..



Are you really sure?? :p


I think: 

[http://dotonthehorizon.com/](http://dotonthehorizon.com/)

is smaller ;)

---

### Post by applecake on 2009-04-08
> **Jakey_TheSnake said:**
> I think: 

[http://dotonthehorizon.com/](http://dotonthehorizon.com/)

is smaller ;)

:lolflag: But its not interactive.. :mad:

Hmm.. I got one question.. What does LOL stand for??? Is it really laughing out loud? I think it was intended to mean long oily lobster...But I dont know..

Look at this: [The End of Internet]("http://translate.google.com/translate?prev=hp&hl=sv&js=n&u=www.slutet.se&sl=sv&tl=en")

Is this beginning to look like something that should be in the Cafe??

---

### Post by Jakey_TheSnake on 2009-04-08
Unfortunately, it does. It can also stand for lots of love, though ;) 

Eh I never check old threads, feel free to shoot me a pm if you have any more problems with Ubuntu!

---

