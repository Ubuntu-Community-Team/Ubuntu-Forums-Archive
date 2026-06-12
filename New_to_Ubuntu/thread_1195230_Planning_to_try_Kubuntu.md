---
title: "Planning to try Kubuntu"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by rausuar on 2009-06-23
Hi!

Although I have used Ubuntu (with Gnome) for some time now, I would like to try Kubuntu (with KDE4).  However I have some doubts I would like to solve:

Is there a manual or some help on the different commands used in Kubuntu from those in Ubuntu?

Do the following applications work without a problem in Kubuntu?:

Compiz (for desktop effects)
Audacious
Openoffice
Pidgin
Cairo-Dock (or GLXDock)
Firefox

Any suggestions?

Thanks!

---

### Post by LowSky on 2009-06-23
kubuntu is only ubunt with KDe instead of Gnome as the desktop enviroment.

all applications you used before will work


when in doubt use the live cd

---

### Post by fabounet on 2009-06-24
no problem with Cairo-Dock (it is environment independant), except for the 2.0.5 version (there is a bug preventing launchers to work on KDE, will be fixed soon in the 2.0.6)

---

### Post by NightwishFan on 2009-06-24
Kubuntu is very similar to Ubuntu though it has been falling off lately. I have used Kubuntu solely since 7.10 until 8.10, which was terrible, though I really do not blame Kubuntu devs, they obviously do their best, as Kubuntu is fairly stable KDE4. Jaunty has a fairly good KDE4, and is fun and fast. If you like impressive eye candy, rather than just window management KDE is a good choice, as it offers a lot. Tips:

Install the package: plasma-desktopthemes-artwork

It has some more plasma themes, as oxygen in this release is terrible without compositing. (8/10 times it is a blue color and not black)

I made a review of Kubuntu KDE4, here is a link.

[http://ubuntuforums.org/showthread.php?t=1132910](http://ubuntuforums.org/showthread.php?t=1132910)

I recommend you install these programs (if you need them) unless I say otherwise, as with Amarok, they will be in the repos.

Ktorrent: Very full featured torrent client.
Amarok2.1: Check Kubuntu.org for a how-to.
Digikam: Excellent photo manager, great search tool.
Kipi-Plugins: Add-ons to Digikam and Gwenview.
KDE-Games: Suite of games, though I wish they had some more common games like chess and blackjack. Mahjongg and Solitaire are included.

---

### Post by carml on 2009-06-24
If you want to try it,just run ```
sudo apt-get install kde
```,if I recall correct.

---

### Post by NightwishFan on 2009-06-24
You can install Gnome and KDE on the same system, using apt or synaptic. If you want 'only kde' or 'only gnome' then it is much simpler to back up personal data and just reinstall Kubuntu or Ubuntu. If you want both then run this command.

```
sudo apt-get update && sudo apt-get install kubuntu-desktop
```

---

