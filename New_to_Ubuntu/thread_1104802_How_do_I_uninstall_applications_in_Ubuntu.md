---
title: "How do I uninstall applications in Ubuntu?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by illurim on 2009-03-24
Hi all,

Quick question: If I've downloaded and installed something in Ubuntu (i.e. Celetania or Savage2) **not** through the package manager, how can I uninstall it?

Is it just a matter of removing any "shortcuts", removing the application directory and removing any .<dir> in my home folder? I'm pretty sure there's no concept of a "registry" like in Windows, but as these programs didn't come with an "uninstall" package, I'm not sure of the best way to remove them.

Any advice appreciated!

---

### Post by The-IRS on 2009-03-24
were they .deb files?
If so, what I did is just remove the game and then remove it from the menu with menu editor.
BE CAUTIONED:
this is most certaintly not the safest way to do this! It is the only way that I know how though

---

### Post by rhcm123 on 2009-03-24
if you cant apt-get remove them, i think the solution is to simply ignore them - that's what i do when i have an installed package that i don't need anymore - never caused me any problems. Why, are these packages malfucntioning?

Edit: A while back, i heard of a debian command called dpkg-remove. I dunno if it's still supported/in the repositories though.

---

### Post by lisati on 2009-03-24
If the package was installed through apt-get, aptitude, "Add/remove software" or synaptic, the safest method is usually the same method, e.g. unchecking the application in Add/Remove software or synaptic, using "apt-get remove" or "aptitude remove"

---

### Post by Christmas on 2009-03-24
Usually these games have their own uninstallers (although you said they didn't come with an uninstall program, look into /usr/local/games and in the game's directory for an uninstall script). Were they DEB packages? If you installed them with dpkg -i package_name you can do a *dpkg -r name* or something (as root).

And yes, you can delete those manually but it's not recommended (do it carefully if you do it, anyway).

---

### Post by zvacet on 2009-03-24
In synaptic find that package and mark it for **complete remove**.If you want to do same thing from terminal 

```
sudo apt-get --purge remove package_name
```

---

### Post by abdusamed on 2009-08-20
hey-- i recently installed electric sheep on ubuntu 9.04. Later i found out it was the wrong one. I can't see it on add/remove nor in the synaptic window. It installed somewhere. I follwed the instruction here but i dontk now how to remove it:

[http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51)

[text which i followed-- from the same link above]
[COLOR=Teal][B]
The preferred way to install it is from source.  If you have Ubuntu or Debian, just right click on the link to the [script]("http://electricsheep.org/makesheep.sh"), and save it in your home directory.  Fedora users see [here]("http://www.taiter.com/blog/2009/06/electricsheep-gnome-screensave.html").  Then open up a terminal (under Applications/Accessories) and type the command ". makesheep.sh" and press return, then type your root password.  The rest should be automatic; if you have any problems just ask below.[/B][/COLOR] 
 It should configure itself to be your screensaver, but you can also run it from the command line just by typing "electricsheep". You can also use "electricsheep-preferences" to configure it, including setting your nickname for credit on the server, and the video driver. If mplayer and your X server are properly configured then the default (blank) should work, but if not, anything you pass to "mplayer -vo" can be put here. Common values are "x11", "gl", and "xv".
 We also have Ubuntu [packages]("https://launchpad.net/%7Eflam3/+archive") for Electric Sheep and FLAM3, available from a PPA (Personal Package Archive) on Launchpad. You can follow the instructions there, or use [another script]("http://electricsheep.org/install-electricsheep-package.sh").  Once you configure your computer to include this PPA, you can install and update Electric Sheep automatically, like the rest of Ubuntu packages in the Synaptic Package Manager.  However they are only compiled for 8.04 and 8.10, [SIZE=4][COLOR=Red]**not yet 9.04.**[/COLOR][/SIZE]

I followed everything in blue.. after that..i ignored cuz it said ''[COLOR=Teal]**The rest should be automatic; if you have any problems just ask below.**[/COLOR]'' after that..i chilled-- THAT WAS A BIG MISTAKE
[U][B][I]
I didnt read the last bit which is in [COLOR=Red]red[/COLOR] until it was toooooooooo late..-- after installing-- i know i'm a noob.. a noob who got himself into BIGGG TIME trouble[/I][/B][/U]

---

