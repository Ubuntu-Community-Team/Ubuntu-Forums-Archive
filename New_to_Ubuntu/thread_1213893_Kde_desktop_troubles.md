---
title: "Kde desktop troubles"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by gertrude58 on 2009-07-15
I installed Kde desktop on my Ubuntu yesterday in a moment of madness or curiosity or something,mow I wish I hadnt!It looks very pretty but since I cant get it to see my wireless network ,it's pretty pointless.There was an icon or widget or something when I first booted into it,so I clicked onto it ,it disappeared and I cant get it back.Network connections shows the network name so I dont know what to do next,I never have any trouble with Ubuntu and wireless,as soon as I go back to gnome it's fine.I got so cross last night I was going to uninstall it but I cant find it in Synaptic and the command instructions for getting it didnt include the command for getting rid if it.So I am stuck with a useless desktop I cant even go on line with.Please can somebody help-either tell me how to get the wireless working or a command to get rid of it,or both!

---

### Post by sunexplodes on 2009-07-15
well, for a temporary fix, open a terminal and type:

sudo ifconfig wlan0 up

followed by

sudo iwconfig wlan0 essid <your network name>

this works with open networks.

---

### Post by lykwydchykyn on 2009-07-15
Did you actually uninstall GNOME?  It's probably still there, just switch back to it at the login screen.  

You can also run GNOME's network manager tray applet in KDE just fine, just hit alt-f2 and type "nm-applet".

That is, assuming that you didn't uninstall GNOME.

---

### Post by n8bounds on 2009-07-15
I love KDE. Sort of like I love Mac OS X Aqua. Both really great approaches... but, well, I dunno. They never stay on my screen long when I try to use them. Nothing is as easy, or as reliable, as Gnome. There's A Reason Ubuntu chose Gnome as the default desktop, methinks. :)

Cheers to you for trying other things though!

---

### Post by gertrude58 on 2009-07-16
No luckily I kept Gnome so will try to run the network applet.Its true its fun to try new things but they dont always work out! and Gnome is just so reliable.I did find kde in Synaptic under kubuntu-desktop so at least I can get rid of it if necessary.;)

---

### Post by Finalfantasykid on 2009-07-16
If you want to get rid of kubuntu-desktop entirely, you can do this...

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

That helped me when I installed kubuntu and xubuntu.

But after doing that, I noticed my update manager took super long to work, but I fixed it > [http://ubuntuforums.org/showthread.php?t=1210493](http://ubuntuforums.org/showthread.php?t=1210493)

---

### Post by allenbradley on 2009-07-16
> **sunexplodes said:**
> well, for a temporary fix, open a terminal and type:

sudo ifconfig wlan0 up

followed by

sudo iwconfig wlan0 essid <your network name>

this works with open networks.
@sunexplodes : That fix is not totally recommended for people new to linux. If you do that once, nm-applet gives up and says that the wireless device is not under its purview. I could never make nm-applet handle my wireless after that.

---

### Post by gertrude58 on 2009-07-16
The nm-applet works great but only as long as the terminal is left open. Is there a way to make it stay or do I have to open a terminal every time I boot into Kde? It is kind of a nuisance!I wish I knew how to get the Kde widget back.:confused:

---

### Post by lykwydchykyn on 2009-07-16
> **gertrude58 said:**
> The nm-applet works great but only as long as the terminal is left open. Is there a way to make it stay or do I have to open a terminal every time I boot into Kde? It is kind of a nuisance!I wish I knew how to get the Kde widget back.:confused:

Either (1) don't run it it a terminal, but put it in the alt-f2 runbox as I suggested or (2) run it like this:
```

nm-applet &disown

```

You can get the kde widget back like so:
 - click the "cashew" in the corner.
 - Unlock widgets
 - Select "add widgets"
 - locate the network manager plasmoid in the list
 - drag the entry to wherever you want the widget (panel, desktop, etc).

---

