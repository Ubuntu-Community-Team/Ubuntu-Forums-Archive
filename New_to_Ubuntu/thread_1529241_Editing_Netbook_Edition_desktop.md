---
title: "Editing Netbook Edition desktop?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by churp on 2010-07-12
Hi all, 

New to the forums. Been using Ubuntu for a few months now and am quite pleased with it, running 10.04 on my MacBook and 10.04 Netbook Edition on my EEE PC. 

I'm wondering if there's any way to get rid of the menus on the Netbook Edition desktop? If possible, I'd like it to look like the standard edition desktop with just the drop-down menu on top and tabs on bottom. Any advice on how to do this, if it can be done, would be greatly appreciated - thanks!

---

### Post by diablo75 on 2010-07-12
I think I read somewhere that you just have to pick a different session from the login window.  Log out of your account so you get the "type your username" box and at the bottom there should be a session button, which by default says "Ubuntu Netbook Edition".  Change this to "GNOME" and login with your username and password.  It should ask you if you want to use GNOME for just this session or for all future sessions.  Tell it you want to keep using GNOME and that should be it.

---

### Post by churp on 2010-07-12
Worked - thanks!

---

### Post by tonytraductor on 2010-07-14
I don't see that here.
I'm using Netbook Remix 9.10 on an everex cloudbook.
I get "failsafe gnome", "gnome", and "xterm" as session options, and choosing "gnome" gives me the nauseating, bloated, head-ache inducing "netbook remix" version with the graphical menu garbage.
Yuck.
I'm thinking of installing openbox in here, maybe.

---

### Post by KdotJ on 2010-07-14
tonytraductor, type this in the terminal

```
sudo apt-get install ubuntu-desktop
```

should do the trick when you select gnome at login

---

### Post by tonytraductor on 2010-07-14
I managed to disable the netbook-remix graphical, nauseating, bloated menu thingy, but only by removing it from startup applications.
When I tried to killall it, it just kept unkilling itself (restarting).  Obstinate little b@$+@®d.
However, I can't seem add anything to the gnome panel to get standard menus.
Considering adding xfce, maybe, still.
I can pretty well find most of what I need (using which or whereis at terminal) and use the alt-f2 run program dialog to get stuff going, but sometimes those menus are useful.

---

### Post by tonytraductor on 2010-07-14
Oh, I posted before seeing your reply.
I'm installing xfce at the moment, but, if that doesn't work out well, I'll install the default ubuntu-desktop.
I'm not a big gnome (or KDE fan).
I use openbox on my main desktop (debian) and my other (fullsized) laptop, but I think I want the gnome-applets for gnome-network etc., which, I believe run in xfce panel, too.
My daughter uses xfce or lxde on her machines, which I set up for her, so I'm familiar with those.
I use openbox without any panels or anything for myself, though.
I used ion3 and wmii, each, for a while, which are nice, being much leaner than any of these bloated graphical desktop environments.
I like openbox, in particular, because it's so trivial to create my own keyboard shortcuts for stuff by editing the rc.xml file (fluxbox is similar in that respect, in fact, easier to configure since the conf file is not xml, but I think fluxbox has kind of fallen behind in development, no?).

---

### Post by tonytraductor on 2010-07-14
Really, I should just click the upgrade to 10.04 and see what that does, before doing much of anything else.

---

### Post by tonytraductor on 2010-07-14
I have one thing to say about this netbook remix:
It's not nearly as quick as hardy herron was (with openbox).
But the wifi support is much better (probably because I replaced the gnome-network thingy with wicd on the previous install).

---

### Post by kerry_s on 2010-07-14
why even bother installing the netbook version if it's not what you want to use, just install the desktop version & be happy. ;)

if your looking for lite & like lxde/openbox, try lubuntu.
it also has a netbook setting you can select at the log in menu.
[http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)

just remember linux is up to you, where there's a will you can find a way to make it what you want.

i'm running netbook, but replaced gnome-panel with awn & i'm using xcompmgr for its compiz effects.

---

