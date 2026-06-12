---
title: "what is going on with this new 10.04???"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by mrfoochie on 2010-07-03
where are the icons in the top right corners of the panels? exit, hide, fullscreen, etc? every time i upgrade i like ubuntu less... hardy heron was awesome... what was wrong with it?

---

### Post by mrfoochie on 2010-07-03
also, how do i grab the panels to move them around?

---

### Post by Evanescence on 2010-07-03
> **mrfoochie said:**
> where are the icons in the top right corners of the panels? exit, hide, fullscreen, etc? every time i upgrade i like ubuntu less... hardy heron was awesome... what was wrong with it?
Hi,
There is a high possibility that there is nothing wrong with your 10.04 Lucid; it could simply be that you're not used to the new panel. Did you upgrade from Hardy Heron to 10.04? 

However, just in case that there is something wrong with your Desktop environment, you can re-configure the Desktop anew: assuming that you are using Gnome (Ubuntu) hit ALT+CTRL+F1 and log in as prompted. Then run the following command: sudo dpkg-reconfigure ubuntu-desktop

That should be able to re-configure your Gnome.

---

### Post by mick222 on 2010-07-03
I don't remember these buttons ,unless you are talking of the shift in windows buttons from right to left.
To move the panel right click it choose preferences and change its orientation from there.

---

### Post by Evanescence on 2010-07-03
> **mrfoochie said:**
> also, how do i grab the panels to move them around?
Well, regarding the panel: if you are referring to moving it to a different position of the desktop, then this is what you do: Right-click on whichever panel you want to manipulate>properties>orientation ... then choose wherever you want it at. You can as well add to the panel whatsoever you please by Right-clicking>Add to Panel ... then highlight your choice and choose "Add" 

Hope that you will be able to use Ubuntu delightfully. Ubuntu is simply the best and once you get the hang of 10.04 you will love it as well :)

---

### Post by ddecator on 2010-07-03
> **mrfoochie said:**
> exit, hide, fullscreen, etc?

Sounds like you are talking about the window buttons. In 10.04 they have been moved to the left by default. If you do not like this behavior, it can be changed using gconf-editor, Ubuntu Tweak, or simply changing the theme (the button placement is on the left for Ambiance and Radiance). 

> **mrfoochie said:**
> how do i grab the panels to move them around?

Right-clicking a panel and selecting Properties will allow you to choose the orientation. Are you looking for a way to manually move it by grabbing the panel?

---

### Post by mrfoochie on 2010-07-03
uhh... maybe panel is the wrong word... window perhaps? you know, the little buttons in the top right of every thing, the button with the 'x' for exiting, the button with the dash to hide the window, the button with two squares to resize the window... and it used to be that i grab the top bar of the window and could pull it around the screen as i wished, now no go... lovely... oh, i upgraded from karmic... the computer with hardy got nicked, sniff, sniff...

---

### Post by ddecator on 2010-07-03
Sounds like the top of the window isn't showing up. Are you using compiz? Are you using proprietary graphics drivers? The top of the window may be hidden behind the top panel, so you can try auto-hiding the panel to see if it is (that happens sometimes with compiz/metacity issues). For now, you can use alt+clickanddrag to move windows around.

---

### Post by mrfoochie on 2010-07-03
yeah, there aren't buttons on the left side either... it seems like maybe the windows are opening too high on the screen and i can't grab the very top or see said buttons... btw thanks folks... i usually figure all this stuff out by reading through this awesome database so this is my first time posting been lurking for over a year...

---

### Post by mrfoochie on 2010-07-03
great minds, eh? how does one alt click and drag? don't know what compiz or the other thing you said is... the window definitely covers the top bar on the desk top...

---

### Post by 4Orbs on 2010-07-03
Suggest you go to menu System>> Preferences>> Appearance>> Effects tab and select "None" which will turn off compiz. Your window titlebars should then appear.

---

### Post by Elfy on 2010-07-03
> how does one alt click and drag? Alt + Left mouse button

---

### Post by mrfoochie on 2010-07-03
oh that alt click drag doesnt seem to work...

---

### Post by mrfoochie on 2010-07-03
also, no appearance effects were turned on... what's this ubuntu tweak?

---

### Post by bigsmitty64 on 2010-07-03
[Ubuntu Tweak]("http://ubuntu-tweak.com/")  :)

---

### Post by mrfoochie on 2010-07-04
yep, still no buttons on any of my windows, still can't move or resize windows... still thinking about building a 32 bit machine to run hardy on... also, should my pointer arrow be an"x"?

---

### Post by mrfoochie on 2010-07-04
got it... i turned down the resolution and presto!

---

