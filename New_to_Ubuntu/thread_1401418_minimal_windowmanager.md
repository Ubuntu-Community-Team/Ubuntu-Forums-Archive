---
title: "minimal windowmanager"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by dzon65 on 2010-02-08
Did a minimal ubuntu install,gnome-core-base,using some leightweight managers,thunar,openbox etc...Now,when I use openbox as windowmanager,minimizing windows will come with a border delay.The window itself is already minimized,but the borders take a split second to minimize as well (a bit jerky).Maximizing same thing but reversed,borders take some time to keep up.Same thing happens with metacity but not with gnome.Had the exact setup on my previous full ubuntu install without this problem.How can I solve this?On a work/windows pc right now.

---

### Post by ubunterooster on 2010-02-08
Have you tried using xcfe instead of gnome?

---

### Post by dzon65 on 2010-02-08
The whole point with this install was to have a stripped down ubuntu.The looks,the feel but...faster.Which it sure is but,before I do some more speed up tweaking,really would like to get this solved cause it "ruins" the whole set up.

---

### Post by ubunterooster on 2010-02-08
okay
fluxbox: [http://fluxbox.sf.net](http://fluxbox.sf.net)
fast, good looking, easy to configure, feels less like windows than does IceWM: [http://icewm.org](http://icewm.org)
very easy to use, loaded w/ options and completely themeable; doesn't come w/ graphical config tool (add Iceconf for that)

---

### Post by dzon65 on 2010-02-08
Thanks,but same thing.Somehow,something's "disturbing" the graphics.Like I said,fluxbox,openbox worked flawless on the full install.Petty really.I have the same configuration on this old compaq with more or less the same symptoms.I blamed it on the old specs (300mb ram and a prehistoric nvidia vanta) but,same thing happens on this one.Of all things,compiz is the only windowdecorator working perfect.

---

### Post by etnlIcarus on 2010-02-08
Sounds as if you want xcompmgr, which will leverage the xcomposite extension in openbox. This ought to clear up the graphical glitches and painting artefacts, no doubt caused by your lacking CPU.

---

### Post by MooPi on 2010-02-08
Why did you install gnome ? It isn't necessary for an Openbox system. You may want to start from scratch again to fix this as the tangle you've created with the mix of gnome dependencies could get tricky. My personal setup consists of minimal install , xdm, xorg, openbox pcmanfm, feh,lxpanel and a mix of this and that to fill the full desktop. You can get the picture from what I've started with. A panel isn't required if you want to install a menu application to fill that need. Good luck

---

### Post by ubunterooster on 2010-02-08
From what I read you only need the "vanilla Xtoolkits". I've no idea what this is but if there is such a package in synaptic go get it.

As there are one-quarter posts in the absolute beginner catagories as there are in all of the others combined but less than one-tenth of the people here to help it is in your best interest to post in one of the other catagories. If in doubt where it belongs try "general help"

---

### Post by dzon65 on 2010-02-08
> **etnlIcarus said:**
> Sounds as if you want xcompmgr, which will leverage the xcomposite extension in openbox. This ought to clear up the graphical glitches and painting artefacts, no doubt caused by your lacking CPU.
  Will give it a try.Btw,the pc i'm working on has 2gb ram.

---

### Post by dzon65 on 2010-02-08
> **MooPi said:**
> Why did you install gnome ? It isn't necessary for an Openbox system. You may want to start from scratch again to fix this as the tangle you've created with the mix of gnome dependencies could get tricky. My personal setup consists of minimal install , xdm, xorg, openbox pcmanfm, feh,lxpanel and a mix of this and that to fill the full desktop. You can get the picture from what I've started with. A panel isn't required if you want to install a menu application to fill that need. Good luck

I wasn't aiming for a full openbox.I was merely setting up a leightweight ubuntu.Ubuntu at first glance but a diet engine under the hood.Mentioned it before,this setup worked just fine on a standard full install.I was wondering what I needed to synchronize them as they did before.Will take a look at that lxpanel.Intended to replace the gnome panels in favour of gnome-do,but trying out some stuff.
Perhaps that xcompmgr,might do the trick.

---

### Post by warfacegod on 2010-02-08
I don't suppose you got Synaptic? If so try using to fix broken packages.

---

### Post by dzon65 on 2010-02-08
Sure do warface.I allready did that one.Ps;asked the staff to move the thread to another place.Shangri-la perhaps?The Beijing ubuntu folums?;)

---

### Post by warfacegod on 2010-02-08
I can't say much except that hopefully someone will offer a fix as opposed to "don't use that crap, use *this* crap instead".

---

### Post by MooPi on 2010-02-08
The reasoning for no gnome is because Openbox is a window manager , whilst  gnome has it's own called metacity that may be in conflict. Simple to avoid and makes for a faster system as well. I have a minimal gnome install using gnome-shell which seems to be light as well. something to ponder.

---

### Post by dzon65 on 2010-02-08
> **MooPi said:**
> The reasoning for no gnome is because Openbox is a window manager , whilst  gnome has it's own called metacity that may be in conflict. Simple to avoid and makes for a faster system as well. I have a minimal gnome install using gnome-shell which seems to be light as well. something to ponder.
  Indeed.But why did it work before?I mean on a full install using openbox didn't conflict at all.Of the two (openbox and metacity) the last one's even worse.Tried gnome-shell,same result.

---

### Post by MooPi on 2010-02-08
Depends on what you were using for display manager, xdm , gdm , ? Besides why have so many redundancies when they can be avoided and lower the HD footprint.

---

### Post by dzon65 on 2010-02-08
> **MooPi said:**
> Depends on what you were using for display manager, xdm , gdm , ? Besides why have so many redundancies when they can be avoided and lower the HD footprint.

Gdm.Now,MooPi,I'm used to dutch,so what do you mean by  "so many redundancies"?Do you mean why compiz,metacity AND openbox?

---

### Post by MooPi on 2010-02-08
> **dzon65 said:**
> Gdm.Now,MooPi,I'm used to dutch,so what do you mean by  "so many redundancies"?Do you mean why compiz,metacity AND openbox?
Duplications of similar or identical. On a minimal install and just gnome-core you've got some config managers missing. Don't ask which ones because I couldn't say. I only know that I've run into problems getting themes and desktop features to work because of this. I suppose this may be happening on your setup. I once had multiple desktop environments running on the same computer, Openbox, fluxbox, Gnome, and KDE. Talk about confusion. I soon realized that it was cool but I would have conflicts and vagaries I couldn't explain.

---

### Post by MooPi on 2010-02-08
Our little discussion has got me thinking of a new system setup. Minimal install metacity, only system. I'll add a file manager of course butmetacity at the core. Hmm ?

---

### Post by dzon65 on 2010-02-08
> **MooPi said:**
> Duplications of similar or identical. On a minimal install and just gnome-core you've got some config managers missing. Don't ask which ones because I couldn't say. I only know that I've run into problems getting themes and desktop features to work because of this. I suppose this may be happening on your setup. I once had multiple desktop environments running on the same computer, Openbox, fluxbox, Gnome, and KDE. Talk about confusion. I soon realized that it was cool but I would have conflicts and vagaries I couldn't explain.

Very much true.This windowmanager problem isn't the only one.There are some more little annoyances.Small things,but nevertheless.I think it takes a while to solve all those little critters in ones own setup,just figuring out the dependencies.You know,would be nice if there were some more good tutorials on leightweight setups,could save time,for whatever setup one likes.

---

### Post by warfacegod on 2010-02-08
> **dzon65 said:**
> Very much true.This windowmanager problem isn't the only one.There are some more little annoyances.Small things,but nevertheless.I think it takes a while to solve all those little critters in ones own setup,just figuring out the dependencies.You know,would be nice if there were some more good tutorials on leightweight setups,could save time,for whatever setup one likes.

Just so you know, I'm about to dive head first into minimal installs. If I learn anything, I'll pass it along.

---

### Post by dzon65 on 2010-02-08
By this I name thee HEAD-member in the minimal-club.

---

### Post by MooPi on 2010-02-08
> **warfacegod said:**
> Just so you know, I'm about to dive head first into minimal installs. If I learn anything, I'll pass it along.
Bravo nothing like a minimal install to make your computer fly. More fun than a full because your in charge of all that go's into the install.

---

### Post by dzon65 on 2010-02-08
Agreed!! It's absolutely worth it.

---

### Post by warfacegod on 2010-02-08
> **dzon65 said:**
> By this I name thee HEAD-member in the minimal-club.

Argh! The pressure!:P

---

### Post by dzon65 on 2010-02-08
The weight of responsability my son.

---

### Post by warfacegod on 2010-02-08
> **dzon65 said:**
> The weight of responsability my son.

Sounds like you've been listening to too much Manowar.

---

### Post by dzon65 on 2010-02-08
Ah,Spartans.

---

### Post by etnlIcarus on 2010-02-08
> **warfacegod said:**
> I can't say much except that hopefully someone will offer a fix as opposed to "don't use that crap, use *this* crap instead".
+1

Also, if the issue is solved, would you care to explain how you solved the issue?

---

### Post by dzon65 on 2010-02-09
> **etnlIcarus said:**
> +1

Also, if the issue is solved, would you care to explain how you solved the issue?

It isn't,gonna do a total new install and see what it gives.

---

### Post by mushwars on 2010-02-09
sawfish, I thought it was broken when I ran it for the fist time

hint: you need to middle click to get a menu.

---

