---
title: "And al the gtk look like this"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-03
[http://img92.imageshack.us/img92/4390/screenshot1tz5.jpg](http://img92.imageshack.us/img92/4390/screenshot1tz5.jpg)

spotty and nothing is like in the screen shot of the theme i want. i have everything i need installed anyone know a fix?

---

### Post by k33bz on 2009-09-03
what exactly are you trying to attempt?

---

### Post by R3fr4cti0n on 2009-09-03
this theme.
[http://d0od.blogspot.com/2009/08/minimal-gtk-themes-megapost.html](http://d0od.blogspot.com/2009/08/minimal-gtk-themes-megapost.html)

---

### Post by ad_267 on 2009-09-03
What GTK theme are you trying to use? What have you installed and how?

---

### Post by ad_267 on 2009-09-03
> **R3fr4cti0n said:**
> this theme.
[http://d0od.blogspot.com/2009/08/minimal-gtk-themes-megapost.html](http://d0od.blogspot.com/2009/08/minimal-gtk-themes-megapost.html)

There's 8 themes listed there...

---

### Post by R3fr4cti0n on 2009-09-03
its called [SIZE=2]MurrinaStudio its a gtk2 theme i put it in my theme window and it shows like the linc in the first post
[/SIZE]

---

### Post by R3fr4cti0n on 2009-09-03
i extracted and dropped in my theme window rather.

---

### Post by Dharmachakra on 2009-09-03
That happens when the actual theme engine is not installed. I haven't used Ubuntu in awhile but I'm sure that the Murrine engine is not installed by default. Look for it in Synaptic. Once you have it installed the theme will look as it should.

You can also drop the theme on the window as an archive. Unless there are multiple parts to the theme it doesn't matter whether it's extracted or not. 

That's my guess.

---

### Post by R3fr4cti0n on 2009-09-03
> **Dharmachakra said:**
> That happens when the actual theme engine is not installed. I haven't used Ubuntu in awhile but I'm sure that the Murrine engine is not installed by default. Look for it in Synaptic. Once you have it installed the theme will look as it should.

You can also drop the theme on the window as an archive. Unless there are multiple parts to the theme it doesn't matter whether it's extracted or not. 

That's my guess.


well i installed murrine and there is like 5 dozen murrine themes in my themes folder but i can not display any of them how do i get it under my apperearnce preferences theme tab so i can preveiw it or just use it?

---

### Post by Sealbhach on 2009-09-03
When you download the theme, extract it until you have just a folder called MurrinaStudio.

Create a folder called .themes in your /home folder. Drop the MurrinaStudio folder in there. Then you should be able to find it in the list of available themes.

Maybe you didn't include the "." before the name of the .themes folder?
.

---

### Post by 4Orbs on 2009-09-03
It sounds like you have installed the Murrine themes but not the engine. The engine is listed in Synaptic Pkg Mgr as gtk2-engines-murrine. Install that and everything should fall into place.

---

### Post by CatKiller on 2009-09-03
> **R3fr4cti0n said:**
> its called [SIZE=2]MurrinaStudio its a gtk2 theme i put it in my theme window and it shows like the linc in the first post
[/SIZE]

They've called the file the wrong thing, for a start. It's a g-zipped tar archive. If you rename it to *whatever*.tar.gz the Appearances window will correctly interpret what it is and extract it properly.

Secondly, it's just a GTK theme. It will only affect the controls - checkboxes, tabs, that kind of thing - not icons, colours,  window borders or anything like that. You'll need to do that yourself.

The comments on the DeviantArt page say that the icons are from one of the Ubuntu Studio icon themes. It looks like the wallpaper is from Ubuntu Studio, too. Installing the *ubuntustudio-look* package should get you all of those. Actually, the colours are from there, too, so selecting an Ubuntu Studio theme and then customising it to use the MurrinaStudio GTK controls should get you pretty close.

---

### Post by R3fr4cti0n on 2009-09-03
> **CatKiller said:**
> 
Secondly, it's just a GTK theme. It will only affect the controls - checkboxes, tabs, that kind of thing - not icons, colours,  window borders or anything like that. You'll need to do that yourself.
crap i just wanted those minimal windows, instead of this bulky crap around mine

---

### Post by CatKiller on 2009-09-03
> **R3fr4cti0n said:**
> crap i just wanted those minimal windows, instead of this bulky crap around mine

It's only a case of finding an appropriate Metacity/Emerald theme, or modifying your own. Emerald Theme Manager, which is what you'd use to change Emerald themes, includes quite a lot of tools to customise the theme, including the ability to change the sizes of the titlebar and window borders. I haven't looked into Metacity themes, so I don't know what's available.

Mix-and-match, man.

---

