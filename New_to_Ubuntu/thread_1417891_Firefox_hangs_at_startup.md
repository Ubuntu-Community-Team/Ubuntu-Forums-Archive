---
title: "Firefox hangs at startup"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Jaraxle on 2010-02-27
I'm running Ubuntu 9.10 and have Firefox 3.5 set to open to a blank page. The only add-on I have is Adblock Plus. Whenever I open the browser it shows the spinning icon that indicates the system is busy. This goes on for about 60 seconds, then stops.

If I start Firefox from the terminal it doesn't do it, only if I open Firefox by clicking on the icon on my panel in Gnome (which is how I normally start Firefox). Anyone encounter this before? 

I can still work, but it's annoying and I want it to work the way it should. When I had Firefox running on Ubuntu 9.04 it never did that. I installed the Epiphany browser as a workaround.

---

### Post by lovinglinux on 2010-02-27
Close Firefox, go to Synaptic and mark xulrunner-1.9.x for re-installation and click "apply".

If that doesn't help, then create a new profile and copy only the essential stuff from the old one, after making sure the new  profile works.

To create a new profile, start Firefox with:

```
firefox -P
```

Optimizing databases would also help.

For more info see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Jaraxle on 2010-02-28
Thank you, should this also work for Icecat? Firefox had started working somehow after installing and removing both Icecat and Iceweasel numerous times. I don't know what changed -- maybe xulrunner got reinstalled in the process?

It's no big deal if I can't get Icecat working because Firefox is working great, but I wouldn't mind using it. It's the same problem: loads fine when launched from the command line, otherwise it clocks for about 60 seconds  upon startup.

---

### Post by Jaraxle on 2010-02-28
Update: Firefox is doing it again. I reinstalled xulrunner. That didn't help, so I deleted then created a new profile in Firefox. Same thing. It loads fine when using the "firefox" command from terminal, but hangs for about a minute when launched from panel or menu.

Do you think installing 3.6 might help?

---

### Post by Scott M. Sanders on 2010-06-12
I'm getting something akin to this topic intermittently too, almost every other Firefox startup. 

My workaround is to use System Monitor, end the firefox-bin process, and restart Firefox, at which point it always says an add-on has been installed, but it shows the add-ons languages tab, and only Firefox (en-GB) 3.6 is listed. 

This Firefox is from repo.

---

### Post by lovinglinux on 2010-06-12
> **Scott M. Sanders said:**
> I'm getting something akin to this topic intermittently too, almost every other Firefox startup. 

My workaround is to use System Monitor, end the firefox-bin process, and restart Firefox, at which point it always says an add-on has been installed, but it shows the add-ons languages tab, and only Firefox (en-GB) 3.6 is listed. 

This Firefox is from repo.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Scott M. Sanders on 2010-07-09
It seems that the All-in-One Sidebar add-on was the culprit, as it has documented issues w/ the default Ubuntu mods: [http://firefox.exxile.net/](http://firefox.exxile.net/)

See this forum topic for uninstalling: [http://firefox.exxile.net/forum/viewtopic.php?t=7770](http://firefox.exxile.net/forum/viewtopic.php?t=7770)

---

### Post by lovinglinux on 2010-07-09
> **Scott M. Sanders said:**
> It seems that the All-in-One Sidebar add-on was the culprit, as it has documented issues w/ the default Ubuntu mods: [http://firefox.exxile.net/](http://firefox.exxile.net/)

See this forum topic for uninstalling: [http://firefox.exxile.net/forum/viewtopic.php?t=7770](http://firefox.exxile.net/forum/viewtopic.php?t=7770)

Well, I use it for years and I have no problems. Perhaps it is interacting with another extension in a bad way. For example I had an extension that caused huge CPU usage when combined with AIOS, because of the Sidebar Collapsing feature of AIOS.

---

### Post by Scott M. Sanders on 2010-07-10
Yeah, in fact it seems to be the en-GB language pack I mentioned, which is actually for Thunderbird (?) (which I use too) and where my All-in-One Sidebar decided to install its extension folder for some reason. 

I had to delete en-GB manually (I'm American so shouldn't need it), which removed itself from Thunderbird, however it remains listed in Firefox, so I disabled it there, but I'm guessing that All-in-One Sidebar just won't work on my Firefox, at least not the repo one.

---

### Post by lovinglinux on 2010-07-10
> **Scott M. Sanders said:**
> Yeah, in fact it seems to be the en-GB language pack I mentioned, which is actually for Thunderbird (?) (which I use too) and where my All-in-One Sidebar decided to install its extension folder for some reason. 

I had to delete en-GB manually (I'm American so shouldn't need it), which removed itself from Thunderbird, however it remains listed in Firefox, so I disabled it there, but I'm guessing that All-in-One Sidebar just won't work on my Firefox, at least not the repo one.

I see. I don't use any extensions from the repositories. I get all of them from Mozilla.

---

