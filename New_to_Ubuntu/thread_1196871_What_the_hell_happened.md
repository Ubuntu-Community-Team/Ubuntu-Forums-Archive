---
title: "What the hell happened???"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-25
Hi
I turned off my computer then when I switched it back on the whole desktop has changed.
There is now a rat on screen with XFCE written underneath it.

How did that happen?

Thanks

---

### Post by philcamlin on 2009-06-25
ok logoff and go to desktop  or somewhere on the logon screen and select ubuntu

you probably installed xubuntu desktop :P :popcorn:

---

### Post by Celauran on 2009-06-25
> **Anybloodyid said:**
> Hi
I turned off my computer then when I switched it back on the whole desktop has changed.
There is now a rat on screen with XFCE written underneath it.

How did that happen?

Thanks

Logout and choose GNOME (or KDE or whatever you like) from the Sessions menu.

---

### Post by sim-value on 2009-06-25
XFCE happend

---

### Post by ~sHyLoCk~ on 2009-06-25
Are you sure you didn't manually install XFCE? Since ubuntu doesn't come with XFCE by default! Xubuntu does.

---

### Post by Anybloodyid on 2009-06-25
I installed Ubuntu 9.0.4 Jaunty Jackalope I never installed XFCE
I've been using it for a bout a month no truoble then all of a sudden up pops XFCE?

---

### Post by sudeepk on 2009-06-25
just logout. select sessions. in that select GNOME. if everything goes right u will be getting gnome, or else go to terminal (ctrl +alt+f1) and look u have any gnome commands. or else install it if u want.

---

### Post by philcamlin on 2009-06-25
> **Celauran said:**
> Logout and choose GNOME (or KDE or whatever you like) from the Sessions menu.

yeah thats what i ment :D

---

### Post by DirtDawg on 2009-06-25
> **Anybloodyid said:**
> I installed Ubuntu 9.0.4 Jaunty Jackalope I never installed XFCE
I've been using it for a bout a month no truoble then all of a sudden up pops XFCE?

Is it possible you installed an XFCE specific app that installed the XCFE desktop packages as dependencies? I can't think of any off the top of my head. Mousepad as an example?

---

### Post by ~sHyLoCk~ on 2009-06-25
> **DirtDawg said:**
> Is it possible you installed an XFCE specific app that installed the XCFE desktop packages as dependencies? I can't think of any off the top of my head. Mousepad as an example?

Most likely so, but the entire XFCE DE as a dependency?

---

### Post by LewRockwell on 2009-06-25
It's a conspiracy!

---

### Post by Anybloodyid on 2009-06-25
The only thing I've done recently is to start using Deluge.
I logged out and went to sessions I tried KDE and Gnome failsafe but it just keeps loading XFCE
I'm not too bothered I just don't like my operating system doing something unless I say so had enough of that with Windoze

---

### Post by DirtDawg on 2009-06-25
> **~sHyLoCk~ said:**
> Most likely so, but the entire XFCE DE as a dependency?

I know it seems strange. It's the only thing I can think of that may have happened.

For example, if an Ubuntu user tries to uninstall Evolution, Aptitude tries to also uninstall ubuntu-desktop as a dependency. Maybe there's an app with the reverse behavior of this?

EDIT: Actually, I just tried to remove Evolution with apt-get and it didn't try to remove ubuntu-desktop. So, who knows what I'm talking about :D You get what I'm saying though.

---

### Post by waspbr on 2009-06-25
just remove the xubuntu-desktop package and install the ubuntu-desktop package.

---

### Post by Mornedhel on 2009-06-25
apt-cache rdepends xubuntu-desktop returns no dependencies on xubuntu-desktop that my repositories know of. No conspiracy there, or it is well hidden.

---

### Post by Anybloodyid on 2009-06-25
I've installed Ubuntu desktop but still seem to have XFCE 
I went to synaptic to uninstall xubuntu desktop but it's not showing as being installed?

---

### Post by LewRockwell on 2009-06-25
it's almost like your machine is booting up a totally different OS

wierd

---

### Post by DirtDawg on 2009-06-25
> **Anybloodyid said:**
> I've installed Ubuntu desktop but still seem to have XFCE 
I went to synaptic to uninstall xubuntu desktop but it's not showing as being installed?

So there is no way to boot into a normal Gnome or KDE desktop? That is really terrible. I installed Xubuntu-desktop on an old laptop and even after I uninstalled it, the XFCE splash screen was still displayed on boot up, but I was able to log into Gnome normally.

Have you tried using the 'history' command? Maybe there's a clue there, I guess. Also, check to see if any xfce4 packages are installed. Is it possible someone else with access to your Linux box may have made a change? Maybe it is all a conspiracy.

What a strange problem.

---

### Post by mcduck on 2009-06-25
> **Mornedhel said:**
> apt-cache rdepends xubuntu-desktop returns no dependencies on xubuntu-desktop that my repositories know of. No conspiracy there, or it is well hidden.

Nothing depends on metapackages like ubuntu-desktop, kubuntu-desktop or xubuntu-desktop. That simply wouldn't make any sense, as these packages contain nothing.

---

### Post by Mornedhel on 2009-06-25
> **mcduck said:**
> Nothing depends on metapackages like ubuntu-desktop, kubuntu-desktop or xubuntu-desktop. That simply wouldn't make any sense, as these packages contain nothing.

Sorry, but you are mistaken*. Dependencies are transitive. If something did depend on xubuntu-desktop, it would install it, and its dependencies (the xfce4 desktop). Some posters (DirtDawg, ~sHyLoCk~) wondered if the OP could have installed something that required xubuntu-desktop. This demonstrates their hypothesis is wrong. Now I grant you that dependencies on such large metapackages are rare.

* Example : edubuntu-desktop requires ubuntu-desktop, as evidenced by both apt-cache depends edubuntu-desktop and apt-cache rdepends ubuntu-desktop.

Further edit : If only the first level of dependencies were called, you would see xserver in the depends list for every GUI app, and coreutils about everywhere.

---

### Post by Anybloodyid on 2009-06-25
Nobody else has access to the computer,  well my wife but she only plays the games.
I turned it off and turned it on again when I did I had XFCE?
The only thing I did before turning it off was allow incoming connections for Deluge and used synaptic to remove Kget, transmission and vuse.  Re history where do I find that?

---

### Post by mcduck on 2009-06-25
> **Mornedhel said:**
> Sorry, but you are mistaken*. Dependencies are transitive. If something did depend on xubuntu-desktop, it would install it, and its dependencies (the xfce4 desktop). Some posters (DirtDawg, ~sHyLoCk~) wondered if the OP could have installed something that required xubuntu-desktop. This demonstrates their hypothesis is wrong. Now I grant you that dependencies on such large metapackages are rare.

* Example : edubuntu-desktop requires ubuntu-desktop, as evidenced by both apt-cache depends edubuntu-desktop and apt-cache rdepends ubuntu-desktop.

Further edit : If only the first level of dependencies were called, you would see xserver in the depends list for every GUI app, and coreutils about everywhere.

OK, edubuntu-desktop (and probably ubuntu-studio packages) is exception for the rule (As it's basically ubunntu-desktop with extra stuff). But these are pretty much the only situations where something depends on a metapackage, and only exist because it makes managing these desktop  metapackages easier.

Like you said, *if* something would depend on xubuntu-desktop, installing it would of course install xubuntu-desktop. That's just normal dependency. My point was that it's very unlikely that this would be the situation, as xubuntu-desktop is empty package and there isn't even any other metapackage that would build on top of the xubuntu-desktop..

Dependency is a one-way thing. If package A depends on package B, that doesn't mean that package B would depend on package A. And as, like I said, the metapackages don't actually provide anything, you can be absolutely sure that no normal software package depends on any of them Why would they depend on empty package?

edit: and here's how you can easily test if you have managed to install some package that, for some reason, would have xubuntu-desktop as it's dependency: uninstall xubuntu-desktop (just the metapackage). If anything you have installed has it as it's dependency, it will be removed as well.

---

### Post by Anybloodyid on 2009-06-25
That's the problem I can't uninstall xubuntu-desktop as it's not showing that it's installed.

Should I just uninstall anything to do with XFCE?

---

### Post by DirtDawg on 2009-06-25
> **Anybloodyid said:**
> That's the problem I can't uninstall xubuntu-desktop as it's not showing that it's installed.

Should I just uninstall anything to do with XFCE?

I don't know if I would uninstall XFCE until you're sure Gnome or KDE works or you may have no GUI at all.

To use 'history', simply type that into your terminal. However,if you don't use your terminal often, it may not make much difference. Still, give it a shot. Maybe something is there. Or not.

You said you removed Kget, Transmission and Vuse. I'm not terribly familiar with any of these. Could it be when you uninstalled one of these, it uninstalled your default Desktop as well? This still wouldn't explain why XFCE would take it's place, but I'm stumped and I can't help but think it must have something to do with package management.

EDIT: Are you using KDE or Kubuntu? Is Kget the KDE equivalent to Gnome's package manager? I took a look at the dependencies and there are some base KDE libraries in there. If you're using KDE and you chose to "completely remove" Kget when you uninstalled it, perhaps you removed some essential libraries? Just more guesses.

---

### Post by Mornedhel on 2009-06-25
> **mcduck said:**
> OK, edubuntu-desktop (and probably ubuntu-studio packages) is exception for the rule (As it's basically ubunntu-desktop with extra stuff). But these are pretty much the only situations where something depends on a metapackage, and only exist because it makes managing these desktop  metapackages easier.

Like you said, *if* something would depend on xubuntu-desktop, installing it would of course install xubuntu-desktop. That's just normal dependency. My point was that it's very unlikely that this would be the situation, as xubuntu-desktop is empty package and there isn't even any other metapackage that would build on top of the xubuntu-desktop..

Yes, it was very unlikely. Someone wondered if it could nevertheless be the case, since the OP could have had xubuntu-desktop installed from something entirely different. I demonstrated it wasn't. I didn't think such a big deal would be made of it :)

> **mcduck said:**
> Dependency is a one-way thing. If package A depends on package B, that doesn't mean that package B would depend on package A. And as, like I said, the metapackages don't actually provide anything, you can be absolutely sure that no normal software package depends on any of them Why would they depend on empty package?

As a counter-example, banshee depends on mono-runtime, which is a metapackage depending on two Mono packages. There probably is a reason you might want to install one of those two other packages separately, I am not a Mono developer.

Metapackages that depend on the latest version, a common occurrence, are another example of metapackages that could be depended upon.

Also, dependency is a one-way thing unless someone fubared the repositories. I don't think there's anything explicitely checking for depends loops. I've seen it happen before. It usually gets resolved after the package maintainers are flooded with bug reports, probably.

> **mcduck said:**
> edit: and here's how you can easily test if you have managed to install some package that, for some reason, would have xubuntu-desktop as it's dependency: uninstall xubuntu-desktop (just the metapackage). If anything you have installed has it as it's dependency, it will be removed as well.

It will. A less intrusive method is apt-cache rdepends.

---

### Post by Anybloodyid on 2009-06-25
I reinstalled Kget, but still no ubuntu
 I tried Log off and changed session to KDE and to Gnome but both were ignored
I tried apt-cache rdepends but again nothing happened?

You can see I'm truing

---

### Post by philcamlin on 2009-06-25
you installed xfce

---

### Post by DirtDawg on 2009-06-25
> **philcamlin said:**
> you installed xfce
C'mon now.

> **Anybloodyid said:**
> I reinstalled Kget, but still no ubuntu
 I tried Log off and changed session to KDE and to Gnome but both were ignored
I tried apt-cache rdepends but again nothing happened?

You can see I'm truing

Are you using Kubuntu? If you are, reinstalling Kget would not necessarily do the trick. If your default install was Kubuntu, see if you have kubuntu-desktop installed (nut only if Kubuntu was what you originally installed. If not, I don't think it would make a difference). Really though, you should be able to boot into Gnome since you have ubuntu-desktop installed, so I have no idea what that's about. What a mess. Surely someone knows what goes on here!

---

### Post by nothingspecial on 2009-06-25
Sorry to keep posting links at you but see [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by lisati on 2009-06-25
Having just read the entire thread (that's a first for me!) I get the impression that we're going round in circles here. 
I concur that the most likely explanations are that xfce and/or xubuntu-desktop have been installed manually or as a side-effect of some dependency when installing something else, or someone has somehow managed to access your system and played a practical joke on you - I, too, am stuck for an alternative explanation. 

Short of a backup of data and a clean install, I would suggest the following:

1. Reinstall the ubuntu desktop (replace this with kubuntu-desktop if required)
```
sudo aptitude reinstall ubuntu-desktop
```
2. Log out, and choose your preferred desktop (Gnome, xfce, whatever)
3. When asked, click on the option to make your choice the default.

---

### Post by 73ckn797 on 2009-06-25
Could you provide a screen shot of the desktop? I am curious.

---

### Post by boglio on 2009-06-25
I had the same problem.

---

### Post by LewRockwell on 2009-06-25
> **lisati said:**
> Having just read the entire thread (that's a first for me!) I get the impression that we're going round in circles here. 
I concur that the most likely explanations are that xfce and/or xubuntu-desktop have been installed manually or as a side-effect of some dependency when installing something else, or someone has somehow managed to access your system and played a practical joke on you - I, too, am stuck for an alternative explanation. 

Short of a backup of data and a clean install, I would suggest the following:

1. Reinstall the ubuntu desktop (replace this with kubuntu-desktop if required)
```
sudo aptitude reinstall ubuntu-desktop
```
2. Log out, and choose your preferred desktop (Gnome, xfce, whatever)
3. When asked, click on the option to make your choice the default.

I'm going with this also...maybe Aston Kutcher punked you!?!

---

### Post by Anybloodyid on 2009-06-26
Thank goodness Ubuntu Desktop is back!!

Thanks to all who contributed to this thread 

A special thanks to Lisati who gave me the solution.

The last question I have is how do I make it the default desktop as after I logged out and clicked gnome to come back in it did not give me the option  to make it default.

Again thanks to all

---

### Post by nothingspecial on 2009-06-26
At the login screen click Options > Select Session > Gnome > Change Session > Log in as normal and it should say "Do you wish to make GNOME the default for future sessions?

Just a bit of non-serious advice - 

> **Anybloodyid said:**
> Nobody else has access to the computer,  well my wife but she only plays the games.

Do what I did, get your wife her own little netbook. For some reason my wife can break a computer just by touching it. You`ll have to fix it all the time but at least yours will be safe! ;)

---

### Post by Anybloodyid on 2009-06-26
> At the login screen click Options > Select Session > Gnome > Change Session > Log

No need it's just doing it switch on and straight in to Ubuntu.

Get the wife her own computer! it was only 12 months ago I bought a new iron, if I go spoiling her it will only go to her head,
Thanks anyway

---

### Post by nothingspecial on 2009-06-26
When you start playing with new desktop environments at least you`ll know what to do. And trust me - never mind trojans and stuff like that. There`s nothing that can break a computer more effectively and quickly as a wife.

And we better stop now before we get a warning from the mods.

All wife breaking computer comments (and ones about irons) are intended humourously. I know who`s in charge, I`m just rebelling (I`m talking about wives not mods).

Nice to meet someone else from Cheshire btw.

---

