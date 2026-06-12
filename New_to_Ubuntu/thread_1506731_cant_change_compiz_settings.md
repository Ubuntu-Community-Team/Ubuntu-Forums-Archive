---
title: "cant change compiz settings"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by insanity99 on 2010-06-10
on compiz settings manager i cant change anything. all the check boxes are faded out. and annoyingly the wobbly window effect is stuck on check, one i particularity dislike.

---

### Post by tom.swartz07 on 2010-06-10
Could you please run this diagnostic script from the terminal and post the output here?

[http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/compiz-check](http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/compiz-check)

That script will check your computer's ability to run compiz, and it will give important information regarding the settings that we could then use to help you.

:D

---

### Post by insanity99 on 2010-06-11
ok here is the output:


neil@neil-desktop:~$ '/home/neil/Downloads/compiz-check' 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

neil@neil-desktop:~$

---

### Post by tom.swartz07 on 2010-06-11
> **insanity99 said:**
> ok here is the output:


neil@neil-desktop:~$ '/home/neil/Downloads/compiz-check' 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         fglrx
 [COLOR="Red"]**Rendering method:      None**[/COLOR]

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

neil@neil-desktop:~$

There's your problem. You dont have a specified rendering method. 

Could you verify that 3D at least works on your system?
From the terminal again, type the command
```
glxgears
```
If it runs, let it go for a few seconds then close it. Let us know what it does.


If thats the case, you simply might have to edit your XORG configuration file to specify that you want to use a rendering method..

Post back with the result of glxgears and Ill see if I could pull up a guide for rendering in the meantime

---

### Post by insanity99 on 2010-06-11
304 frames in 5.0 seconds

im sure 3D works anyway because i play heroes of newerth fine.

this is my Xorg.conf:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

---

### Post by insanity99 on 2010-06-12
bump

---

### Post by warfacegod on 2010-06-12
First place I'd start is checking Synaptic for broken packages and fixing them. Next I'd reinstall compizconfig-settings-manager.

---

### Post by insanity99 on 2010-06-12
already tried that.

---

### Post by warfacegod on 2010-06-12
This might be a silly question but you do have Extra Visual Effects enabled? I don't see how that could relate to CompizConfig graying out but I suppose it's possible.

---

### Post by insanity99 on 2010-06-12
no, still greyed out no matter what visual effects are active

---

### Post by tom.swartz07 on 2010-06-12
Try this:

hit ALT F2 and type
```
compiz --replace
```
then hit enter.

Alternately, you could try 
```
metacity --replace
```
to force it one way or the other
It could be that your systems somehow defaulted to metacity instead of compiz

---

### Post by warfacegod on 2010-06-12
And if all else fails, Tom's got a line on this s-video gadget from China that should have you fixed up in no time.

---

### Post by insanity99 on 2010-06-13
those commands did nothing, so where can i get this s-video thing that can help me?

---

### Post by warfacegod on 2010-06-13
> **insanity99 said:**
> those commands did nothing, so where can i get this s-video thing that can help me?

Sorry hoss. That was a joke at Tom's expense.

---

### Post by tom.swartz07 on 2010-06-13
> **warfacegod said:**
> Sorry hoss. That was a joke at Tom's expense.

HEYYY!! I leave for a few hours, and you just start making fun of me... I see how it is... :P

> **insanity99 said:**
> those commands did nothing, so where can i get this s-video thing that can help me?

Can you specify what you mean by 'doing nothing'? Those commands SHOULD have done something, by switching between the two different compositing methods for Gnome Window Manager.

Try running those same commands from the terminal (applications>accessories>terminal) and see what kind of information they spit out. Copy and paste everything it says back here for us to look at.

If you cant switch between Metacity and Compiz, that might be where your problem lies in this whole situation.

---

### Post by warfacegod on 2010-06-13
```
HEYYY!! I leave for a few hours, and you just start making fun of me... I see how it is... 
```

Left for a few hours nothing. You were still logged in when I posted that.:biggrin:

@insanity99

Try installing simple-ccsm, it's unlikely to work any better than CompizConfig but it's worth a shot.

I see that you are using 10.04. Is this a fresh install or is it an Upgrade install?

You may also want to consider creating another user account to see if this is restricted only to your account. If it is, it's a pretty good bet that there is a setting conflict somewhere in your personal settings.

---

### Post by insanity99 on 2010-06-13
> **tom.swartz07 said:**
> HEYYY!! I leave for a few hours, and you just start making fun of me... I see how it is... :P



Can you specify what you mean by 'doing nothing'? Those commands SHOULD have done something, by switching between the two different compositing methods for Gnome Window Manager.

Try running those same commands from the terminal (applications>accessories>terminal) and see what kind of information they spit out. Copy and paste everything it says back here for us to look at.

If you cant switch between Metacity and Compiz, that might be where your problem lies in this whole situation.

ah sorry i was in a hurry and rushed my reply. it doen't do nothing, the gnome window manager seems to restart and it switches between metacity and compiz. what i meant to say is it does not fix my problem.

> **warfacegod said:**
> ```
HEYYY!! I leave for a few hours, and you just start making fun of me... I see how it is... 
```

Left for a few hours nothing. You were still logged in when I posted that.:biggrin:

@insanity99

Try installing simple-ccsm, it's unlikely to work any better than CompizConfig but it's worth a shot.

I see that you are using 10.04. Is this a fresh install or is it an Upgrade install?

You may also want to consider creating another user account to see if this is restricted only to your account. If it is, it's a pretty good bet that there is a setting conflict somewhere in your personal settings.

yeah i upgraded from 9.10, i will try to make a new account and see if that changes anything.

thanks.

---

### Post by lidex on 2010-06-14
What is the output of this command:
```
dpkg -l | grep "compiz"
```
Use a Terminal="Applications->Accessories->Terminal"

---

### Post by insanity99 on 2010-06-14
here is the output:

neil@neil-desktop:~$ dpkg -l | grep "compiz"
ii  compiz                                1:0.8.6-0ubuntu1~ppa3                           OpenGL window and compositing manager
ii  compiz-core                           1:0.8.6-0ubuntu1~ppa3                           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra           0.8.6-0ubuntu1                                  Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main            0.8.6-0ubuntu3                                  Collection of plugins from OpenCompositing f
ii  compiz-gnome                          1:0.8.6-0ubuntu1~ppa3                           OpenGL window and compositing manager - GNOM
ii  compiz-plugins                        1:0.8.6-0ubuntu1~ppa3                           OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf            0.8.4-0ubuntu2                                  Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager         0.8.2-0ubuntu1                                  Compiz configuration settings manager
ii  libcompizconfig0                      0.8.4-0ubuntu3                                  Settings library for plugins - OpenCompositi
ii  python-compizconfig                   0.8.2-0ubuntu1                                  Compiz configuration system bindings
neil@neil-desktop:~$

---

### Post by xsandz on 2010-06-14
just a silly reminder...have u installed display drivers for your mobo?

---

### Post by insanity99 on 2010-06-14
do you mean for my graphics card? yeah.

---

### Post by warfacegod on 2010-06-14
I've compared your output to mine and there are some differences. You have apparently gotten some of your packages from a PPA whereas I have not. I don't see how this could effect CCSM's ability to work properly.

---

### Post by insanity99 on 2010-06-14
strange, seems to be no fix?

---

### Post by warfacegod on 2010-06-14
I've got a feeling this is due to the Upgrade install of 10.04 from 9.10. At this point, I'd say do a fresh install. Make a backup of your files and settings. Even better, copy the entire contents of your Home folder to a separate partition and do a fresh install marking the separate partition with your stuff as /home.

---

### Post by lidex on 2010-06-14
In the past I had issues with the ppa version of compiz. What solved it for me was removing the ppa and downgrading all the compiz packages to the standard ubuntu repository versions. I also think you need to install compiz-fusion-bcop.

---

### Post by warfacegod on 2010-06-14
bcop is a code generator for Compiz. I don't have it and my CCSM works just fine.

I agree with getting rid of the PPA's.

---

