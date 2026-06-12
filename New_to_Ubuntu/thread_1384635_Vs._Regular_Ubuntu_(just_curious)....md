---
title: "Vs. Regular Ubuntu (just curious)..."
date: 2010-01-18
forum: New to Ubuntu
---

### Post by 416inversed on 2010-01-18
So, my question extends from this thread ([http://ubuntuforums.org/showthread.php?t=1379301](http://ubuntuforums.org/showthread.php?t=1379301) ) but I was hesitant to post there as I didn't want to distract from the OP's actual problem.

So what exactly is the difference between UNR & Ubuntu?

From what I've been able to gather, the current version of UNR (9.10) is essentially regular Ubuntu, but with 'Netbook Launcher,' Maximus, and some battery/power related apps added.

Is this essentially correct? Or am I over looking something?

I installed UNR 9.10 on my vanilla-flavored Acer Aspire D250, mostly because its LiveCD fit on my 1gig USB stick, whereas straight Ubuntu did not. But since then, I've turned off 'Netbook launcher' paired Maximus with Namebar instead of the default panel app, and replaced 'Go Home' with 'Main Menu' among other things.

So would you say I'm still running UNR or by turning off "Netbook launcher' et al. am I now running straight Ubuntu?

I realize it's probably all just semantics, but I was curious.

---

### Post by J V on 2010-01-18
essentially yes, but this is a big difference...

Simply the fact that the title bar is moved into the panels leftover space is a huge improvement...

---

### Post by snowpine on 2010-01-18
You can see the *exact* differences by comparing these lists:

[http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)
[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

If you type the following in the terminal, you can see if you're "missing" anything that would be in a standard Ubuntu install. (You do not have to say "yes" to the install if you don't want to.)

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by warfacegod on 2010-01-18
> **snowpine said:**
> You can see the *exact* differences by comparing these lists:

[http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)
[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

If you type the following in the terminal, you can see if you're "missing" anything that would be in a standard Ubuntu install. (You do not have to say "yes" to the install if you don't want to.)

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

If you have previously removed any apps such as F-Spot or Empathy, these will show up in the out put as well.

---

### Post by 416inversed on 2010-01-27
> **snowpine said:**
> You can see the *exact* differences by comparing these lists:

[http://packages.ubuntu.com/karmic/ubuntu-desktop](http://packages.ubuntu.com/karmic/ubuntu-desktop)
[http://packages.ubuntu.com/karmic/ubuntu-netbook-remix](http://packages.ubuntu.com/karmic/ubuntu-netbook-remix)

If you type the following in the terminal, you can see if you're "missing" anything that would be in a standard Ubuntu install. (You do not have to say "yes" to the install if you don't want to.)

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

I just realized I never responded.

Just for anyone else's future reference, the difference was:
```

The following extra packages will be installed:
  brasero firefox-3.5-gnome-support firefox-gnome-support gdm-guest-session libavahi-ui0 libbeagle1 libgtk-vnc-1.0-0
  libwmf0.2-7-gtk rdesktop totem-mozilla tsclient vinagre vino xsane xsane-common
Suggested packages:
  dvdauthor vcdimager vnc-viewer xnest xsane-doc hylafax-client mgetty-fax gv gocr
The following NEW packages will be installed:
  brasero firefox-3.5-gnome-support firefox-gnome-support gdm-guest-session libavahi-ui0 libbeagle1 libgtk-vnc-1.0-0
  libwmf0.2-7-gtk rdesktop totem-mozilla tsclient ubuntu-desktop vinagre vino xsane xsane-common
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,870kB of archives.
After this operation, 27.3MB of additional disk space will be used.
```

Of course, perhaps missing some other packages I erstwhile reconciled in my constant tweaking of UNR.

Anything in that list look important?

---

### Post by J V on 2010-01-27
not for the average user no...

Besides, UNR also is designed to work :P

---

### Post by warfacegod on 2010-01-27
> **416inversed said:**
> I just realized I never responded.

Just for anyone else's future reference, the difference was:
```

The following extra packages will be installed:
  brasero firefox-3.5-gnome-support firefox-gnome-support gdm-guest-session libavahi-ui0 libbeagle1 libgtk-vnc-1.0-0
  libwmf0.2-7-gtk rdesktop totem-mozilla tsclient vinagre vino xsane xsane-common
Suggested packages:
  dvdauthor vcdimager vnc-viewer xnest xsane-doc hylafax-client mgetty-fax gv gocr
The following NEW packages will be installed:
  brasero firefox-3.5-gnome-support firefox-gnome-support gdm-guest-session libavahi-ui0 libbeagle1 libgtk-vnc-1.0-0
  libwmf0.2-7-gtk rdesktop totem-mozilla tsclient ubuntu-desktop vinagre vino xsane xsane-common
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,870kB of archives.
After this operation, 27.3MB of additional disk space will be used.
```

Of course, perhaps missing some other packages I erstwhile reconciled in my constant tweaking of UNR.

Anything in that list look important?

Looks fine to me. Then again, it depends on what you define important as.

---

