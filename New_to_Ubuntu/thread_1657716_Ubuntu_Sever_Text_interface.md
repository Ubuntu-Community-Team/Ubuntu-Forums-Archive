---
title: "Ubuntu Sever Text interface ?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Aaron A. Dennis on 2011-01-01
Hello everyone, 

I am very new to Ubuntu Forums just activated rite before i started this tread. Please forgive me I understand the annoyance of superfluous threads I searched through three sets of key words and skimmed 600 ish pages and did not find an answer to my question. 

I would like to make my Ubuntu server a bit more pronounced, I want to be able to read things clearly and I would like to see some color. But I don't want a full blown GUI (gnome, KDE) I need different font sizes and hoping for colorful font. 

I would like it to resemble Damn Small Linux before it loads X thats my only example i love how that looks can anyone point me towards how to set that up or to a script or apt or something?

Thank you.

---

### Post by solar george on 2011-01-01
You can configure the console font by running;
```
sudo dpkg-reconfigure console-setup
```
As for colours and the like take a look at [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html) and try running byobu (you should read about using screen and byobu if you're going to be doing a lot of work at the console anyway)

---

### Post by LewRockwellFAN on 2011-01-01
I'm not sure if this will help. Sounds like you know more than I do. But since there are 0 replies I'll post this on the chance it MIGHT.

If you have NO gui (rather than simply not wanting to use it as a matter of routine) this may be irrelevant. But from a terminal I can click edit, profile-prefs and that lets you change some colors. I use white on black. And from the Gnome desktop I can click System, Preferences, Appearance, Fonts tab, and the settings there affect the appearance of fonts in the terminal.

P.S. - Well there were 0 when I hit reply. Snails type faster than me.

---

### Post by solar george on 2011-01-01
That will only apply to gnome-terminal however it's something thats worth keeping in mind since console-setup will only affect the fonts when you are using the machine locally not via ssh (when it will follow the font setup at the client end) however the colour and prompt setup will apply to both.

---

### Post by kaldor on 2011-01-01
Maybe you'd like to install a very lightweight desktop environment? I recommend Icewm or Fluxbox if you want something very very small but still usable for basic stuff.

---

