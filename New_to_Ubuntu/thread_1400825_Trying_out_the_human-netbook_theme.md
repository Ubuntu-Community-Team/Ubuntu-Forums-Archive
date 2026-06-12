---
title: "Trying out the human-netbook theme"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by gruvn on 2010-02-07
Hey Folks,
I'm interested in picking up a netbook with remix on it, so you can imagine when I saw this post - [http://www.tuxradar.com/content/ubuntu-netbook-remix-904-hands](http://www.tuxradar.com/content/ubuntu-netbook-remix-904-hands) describing how yo could try out the netbook remix on a normal ubuntu desktop, I was quick to try it out.  To do so, I followed the instructions of doing

sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet

and tweaking the panels.

It looks good and seems to work well, but is soooooooo slooooooooooow.  It takes about 10s for the items on the main screen to get focus.  My understanding was that this is really just a theme (it shows up as the "human-netbook" theme under System>Appearance), so it should run fine.

Has anyone encountered, and more importantly, addressed the serious lag?

Cheers!

---

### Post by gruvn on 2010-03-04
So it turns out that UNR is optimized for the Atom processor found in most netbooks.  I have tried UNR (USB boot) on several desktops and it's waaaay slow.  I went ahead and installed it on my new netbook and it runs like a dream.

Cheers!

---

### Post by spiderbatdad on 2010-03-04
good news. I really like the interface too...though maximus had to go.
Also took a little work to get the window switcher to move so I could add a few other items to the top panel.

---

### Post by NightwishFan on 2010-03-04
It could use some polishing, however since Netbook Edition is now more "official", I am betting they will work on it.

I do not think it is really compiled for Atom any more, as I can also run a 64-bit build of it. The **launcher** is made with the same thing as the Gnome Shell, Clutter. You need accelerated 3d hardware to run the clutter interface.

---

### Post by gruvn on 2010-03-05
Yeah - I liked the idea of maximus, since I typically maximize my windows even on my large monitor, but it was way too annoying.  One cool thing I found by accident was that when you double click the title bar in the window-picker, the window becomes unmaximized.  It may be due to my tweaking maximus in gconf-editor, but anyways I like it, since I was missing the minimize/restore/maximize buttons.

thanks for the info NightwishFan - I thought I'd heard that it was optimized, but I've been reading a lot of Ubuntu stuff recently, and probably mixed that bit of info up.  If it's not optimized, do you have any idea why it is slow when run on more powerful desktops?

Cheers!

---

### Post by NightwishFan on 2010-03-05
> **NightwishFan said:**
> The **launcher** is made with the same thing as the Gnome Shell, Clutter. You need accelerated 3d hardware to run the clutter interface.

The rest of UNR is just standard stuff such as GTK. Nothing that would not be noticeable time critical. Perhaps however you installed it was a fluke.

The desktop launcher needs good 3d support.

---

