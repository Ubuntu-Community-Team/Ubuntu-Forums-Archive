---
title: "Uninstall Google Earth"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by lsc on 2010-04-25
As part of an ongoing attempt to get Google Earth running on Ubuntu 8.10, I  did a sudo install. This installation didn't run either, but unlike the times I've installed to the home directory, I can't find it to uninstall and neither can Synaptic. It still shows in the Applications menu and tries to run, so I know it's somewhere.

I could use help finding and deleting using Terminal, but please assume I know little in way of commands.

thanks!

---

### Post by thulefoth on 2010-04-25
There is a discussion of [the Google Earth problems on Ubuntu, on eHow]("http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html").

"Google Earth is a great tool that provides maps and satellite images of the whole world. Some Linux users, however, find that it's difficult to use or won't run properly on Ubuntu or need to uninstall it before installing a new version. For some reason, though, uninstallation on Ubunutu can also be a little complicated and there isn't one command that works for all users. So, there are a number of different approaches to try to uninstall Google Earth on Ubunutu."

There follows detailed instructions for using the Terminal, including specific command-strings.  I would do some further searching & homework & confirmation ... but this looks like a good place to get started.

I like maps & GIS & GPS too!

Ted

---

### Post by lsc on 2010-04-25
> **thulefoth said:**
> There is a discussion of [the Google Earth problems on Ubuntu, on eHow]("http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html").

"Google Earth is a great tool that provides maps and satellite images of the whole world. Some Linux users, however, find that it's difficult to use or won't run properly on Ubuntu or need to uninstall it before installing a new version. For some reason, though, uninstallation on Ubunutu can also be a little complicated and there isn't one command that works for all users. So, there are a number of different approaches to try to uninstall Google Earth on Ubunutu."

There follows detailed instructions for using the Terminal, including specific command-strings.  I would do some further searching & homework & confirmation ... but this looks like a good place to get started.

I like maps & GIS & GPS too!

Ted

Thanks, Ted-that's one place I hadn't looked yet. When I was installing to home directory, it was a snap to use GE's script to uninstall. If I could only find that folder...

Lorne

---

### Post by 3rdalbum on 2010-04-25
It's probably in /opt.

---

### Post by thulefoth on 2010-04-25
Lorne, since it's showing in the Apps Menu, go into Menu Edit (right-click Applications), find the program in the Editor, right-click on the menu-name for it, and then pick the Properties option.

One of the fields in the Properties Dialog is "Command":  in some cases this command (to start the program) is actually the Directory Path to the program.  Other cases, it's just the 'bare' name ...

Check that ...

---

### Post by Sef on 2010-04-25
How did you install it?

---

### Post by lsc on 2010-04-25
this last time I followed Ubuntu documentation and did  

sudo ./GoogleEarthLinux.bin

I quit the installer and lauched from Applications.

I'll try Thuleforth's second suggestion-eHow's instructions were coming back file not found.

Lorne

---

### Post by lsc on 2010-04-25
Yup, following Ted's instructions, Menu option found it in /opt as 3rdalbum predicted 

/opt/google-earth/googleearth %f

Trouble is, the uninstall script within the folder's not working this time. So what's my command line for removing it?

Lorne

---

### Post by thulefoth on 2010-04-25
Here is an Ubuntu forum post that talks about [making the uninstall script executable]("http://ubuntuforums.org/showthread.php?t=236589"), before it will work ...

---

### Post by lsc on 2010-04-25
Making the uninstall script executable did the trick, though previously I had only to dbl click for it to run. thanks! 

BTW, Ted, GPS comes in handy when we run up to the Olympic Peninsula to dive Hood Canal.

So now I'm back to trying to keep Google Earth from crashing, and I've tried most of the suggestions in the forum, though I never saw the libcrypto... file in GE's folder. Part of the problem may be needing something better than the on-board video I'm running, if anyone has a PCI/PCI express video card to suggest.

Lorne

---

### Post by thulefoth on 2010-04-25
Sounds like a dandy outing on Hood Canal, Lorne!  Tons of tempting places.  

I have some hand-recorded GPS tracks (Magellan 310) from off-trail hikes I make in the Olympic Park.  I need to get these entered in a standard format, and would like to publish maps with my routes on it.  I have downloaded both the DRG USGS topo maps, and the 1 meter satellite images for the quads.

I've been eye-balling Google Earth ... other people are 'familiar' with it and kinda hope I use it, but the reading I've done had me wary (I'm Ubuntu-noobi from '98 & XP).  Now, you've basically saved me from wandering into the 'GE swamp' ... thanks!  

I'm hoping to find lower/older-tech tools for doing this, and wait on GE.

I have a 6-8 yo custom XP box with a PC-Chips MB and a, uh "440" something video card in the 8x AGP slot.  I just upped the RAM from .5 to 2 gig ... mainly for those 1-meter (quater) quad images, which are 35 meg JPEGs.

You got a site or refs?  I'll have my site back up this week.

Ted

---

### Post by lsc on 2010-04-25
The occasional time I go back to the navigation charts, I use a Mac for waypoint management. If I can get GE running, I'll start geotagging photos and put them up on a site. Till then...

Lorne

---

