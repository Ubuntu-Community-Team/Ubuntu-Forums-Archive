---
title: "Installing HP CM1312 MFP on console"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-05-23
Question: I have a HP CM1312 MFP  color laser printer/scanner.
I've installed it on Lucid, and it worked fine, including scanner (but only with xsane).

Now, I wanted to install it on a server (console only), but it doesn't seem to work there.

My problem is gnome automatically installed some plugin, and I don't know which. I suppose it's this plugin that I am lacking.

So far I just connected the USB printer to the server.
The USB port is working correctly, I checked with a memory stick.

Did I miss anything? Is there anything gnome does automagically, like adding the printer to some configuration file ?


Or is there a way I can see a list of RECENTLY (today) installed programs (dpkg -l outputs everything).

---

### Post by WitchCraft on 2010-05-23
Well, all HP utilities are QT based, and there's no reference to the firmware to download. Crap, I wonder what they smoked when they wrote those utilities. Now I'm gonna install gnome / xorg, install the printer driver firmware, and then remove gnome & xorg.

1 printer - 600 $

40 kb Firmware, 1 operating system - 0$

45 minutes of your time and having to download 220 MB to install xorg/gnome, when you only want to run a console network printing server, just to download the 40 kb firmware - priceless.

Gee, that was the last time I bought anything HP.

---

### Post by WitchCraft on 2010-05-24
Correction: No it looks like it isn't the last time I bought HP.
The printer works fine, and the scanner, too.

But the fact that hp-setup only tells you to run it with the -i option (for interactive, console) when you started it from Xorg, is really stupid...

Now I've setup network printing and scanning, from windows and linux, and it works excellently.

---

