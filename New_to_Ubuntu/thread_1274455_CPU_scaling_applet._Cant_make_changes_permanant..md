---
title: "CPU scaling applet. Cant make changes permanant."
date: 2009-09-24
forum: New to Ubuntu
---

### Post by philinux on 2009-09-24
It defaults to "on demand". On my desktop full screen flash is much better if I select "conservative". But on reboot it reverts to the default "on demand'.

Had a look in gconf-editor and nothing there.

---

### Post by HarrisonNapper on 2009-09-24
So there was nothing in the config file to set the default? What is the name of the applet you're running and have you tried launching it through terminal to see if any of the initialization messages might provide more insight?

---

### Post by admiralspark on 2009-09-24
Mine always defaults to Performance. It really isn't THAT hard to just change it, as I find myself doing many times anyway when I switch between cruising the internet and, say, burning music CD's. Maybe some specs? (motherboard/CPU for specifics).

---

### Post by philinux on 2009-09-24
> **HarrisonNapper said:**
> So there was nothing in the config file to set the default? What is the name of the applet you're running and have you tried launching it through terminal to see if any of the initialization messages might provide more insight?

It's an applet. Right click on panel and choose add. CPU freq scaling monitor.

---

### Post by NoaHall on 2009-09-24
"sudo apt-get install rcconf"

sudo rcconf

Scroll down to "ondemand", press spacebar on it, and then enter.

---

### Post by philinux on 2009-09-24
> **NoaHall said:**
> "sudo apt-get install rcconf"

sudo rcconf

Scroll down to "ondemand", press spacebar on it, and then enter.

Now why didn't I think of that. LOL

I'm surprised gconf-editor has nothin under apps gnome-power-manager for this applet. Cheers for the rcconf though.

---

### Post by HarrisonNapper on 2009-09-24
Ah, the default CPU applet; sorry, I must not have been paying attention. Mine defaults to performance, too, and I've never poked around the configuration file for it. When I get back to my comp, if it's still an issue, I'll poke around and see if I catch anything. Sorry.

---

### Post by philinux on 2009-09-25
> **NoaHall said:**
> "sudo apt-get install rcconf"

sudo rcconf

Scroll down to "ondemand", press spacebar on it, and then enter.

Doing this results in the scaling set to performance as default. Whereas I want conservative as default.

---

### Post by philinux on 2009-09-25
Found this at last. 

Where the default is stored
/etc/init.d/ondemand

[http://ubuntuforums.org/showthread.php?t=1223116](http://ubuntuforums.org/showthread.php?t=1223116)

---

