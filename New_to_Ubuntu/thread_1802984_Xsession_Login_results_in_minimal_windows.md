---
title: "Xsession: Login results in minimal windows"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by Lorin Ricker on 2011-07-12
Ubuntu Studio 10.4 (LL/LTS), upgraded from 9.10 on 4-June-11.  Recent lightning storms have me shutting down frequently to protect equipment... Upon reboot, each time I re-login to Gnome (v2.30.2), I end up with "undecorated" windows -- that is, each application window lacks its title bar, they cannot be moved or resized, and each lands in a fixed position.  Only my top-panel works, and I cannot get access to workspace control widgets.

I've discovered that to (temporarily until next login/reboot) fix this, I can right-click on the workspace background to display the pop-up menu, select "Change Desktop Background", go to "Visual Effects" tab, observe that the "None" button is selected, and then click on the "Normal" button.

This displays a progress box labeled "Searching for available drivers...", which ping-pongs a progress bar back and forth for about 20-30 seconds.  Then (every time), all visible windows get re-displayed with the "normal" title bars -- another box pops up with "Do you want to keep these settings?" and, of course, I click on the Keep These Settings button.

Then all's well -- normal application windows... until my next reboot/login cycle.

What's going on here? For me, this is new behavior with my upgrade to Ubuntu 10.4/LTS.  I've looked in my /home/user directories for something to do with Xsession, perhaps a config-file, but have only found .xsession-errors (and .xsession-errors.old), with some formidable logging in 'em.  They don't (yet) help me much...

What should I be looking for?  What can I post to help diagnose this?  What "drivers" is Gnome searching for, and why can't it find them at login?  Why won't setting visual effects to "normal" stick (be permanent) now?

TIA -- I'm lost on this one.
Lorin

---

### Post by jtarin on 2011-07-12
After you get to the desktop open a terminal and issue the command 
```
tail -f /var/log/syslog
```then we can see if anything out of the ordinary happens after you login in. Copy and post the output here. 
Use the "#"code brackets from the reply menu to place your output in.

---

### Post by Lorin Ricker on 2011-07-28
> **jtarin said:**
> After you get to the desktop open a terminal and issue the command 
```
tail -f /var/log/syslog
```then we can see if anything out of the ordinary happens after you login in. Copy and post the output here. 
Use the "#"code brackets from the reply menu to place your output in.

(Sorry to take so long with this -- "real work" got in the way...)

Here's the results from /var/log/syslog immediately after logging into the desktop:

```

$ # Immediately after logging into desktop and opening a terminal...

$ tail -f /var/log/syslog
Jul 28 11:27:20 music udev-configure-printer: Queue ipp://localhost:631/printers/LaserJet2300 has matching device URI
Jul 28 11:27:20 music udev-configure-printer: URI of detected printer: usb://HP/LaserJet%202300%20series, normalized: laserjet 2300 series
Jul 28 11:27:20 music udev-configure-printer: Queue ipp://localhost:631/printers/LaserJet2300 has matching device URI
Jul 28 11:27:20 music udev-configure-printer: URI of print queue: cups-pdf:/, normalized: cups pdf
Jul 28 11:27:20 music udev-configure-printer: URI of detected printer: hp:/usb/hp_LaserJet_2300_series?serial=CNBFB11606, normalized: laserjet 2300 series serial cnbfb11606
Jul 28 11:27:20 music udev-configure-printer: URI of detected printer: usb://HP/LaserJet%202300%20series, normalized: laserjet 2300 series
Jul 28 11:27:22 music rtkit-daemon[4383]: Failed to make ourselves RT: Invalid argument
Jul 28 11:27:28 music rtkit-daemon[4383]: last message repeated 10 times
Jul 28 11:27:28 music nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Jul 28 11:27:28 music nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Jul 28 11:28:24 music AptDaemon: INFO: Initializing daemon
^C
$ 
$ # The very last line, "...AptDaemon: INFO:..." appears as I'm (re)configuring window
$ # decorations to "normal" (from "none").
$ !No other messages appear during this re-config.

```

Does this help shed any light?  TIA!
-- Lorin

---

### Post by jtarin on 2011-07-28
> What should I be looking for? What can I post to help diagnose this? What "drivers" is Gnome searching for, and why can't it find them at login? Why won't setting visual effects to "normal" stick (be permanent) now?
Your saying....that when you set visual effect to normal they don't stick??? Have you tried setting them to _none_? Wobbly windows are only amusing for about 10 min.

---

### Post by sirgogo on 2011-07-28
> **jtarin said:**
>  Wobbly windows are only amusing for about 10 min.
Totally agree. Sticky windows are pretty useful though.

But yeah, try disabling effects, then re-enabling. Sometimes it glitches. 

If that doesn't work...
This may be an outdated command since 11.04 (haven't really used it a whole bunch yet, using Sabayon), but disable the effects (None option), then run
```
sudo dpkg-reconfigure xserver-xorg
```
in the terminal to reconfigure your gfx drivers. Reboot, ensure proprietary drivers are installed via the gui (Restricted hardware) and check your effects.

Let us know how it goes!

---

### Post by Lorin Ricker on 2011-07-29
Thanks for responses!  jtarin: The problem is that, upon reboot/login, X-Windows are starting up un-decorated, in "none" by default.  No, I'm not using wobbly windows or any advanced eye-candy at all -- I just want my windows to start in "normal" mode, and when I login, I have to take the extra steps now (since 10.4 upgrade) to put them in normal mode.

sirgogo: I'll try the steps you've outlined, and I'll let you know -- won't likely happen for a couple of days, tho', due to outside schedule... and I like to be careful & thorough with such experiments, so I understand the variables and what (hopefully, finally) works!

Thanks!  I'll let you know soon...
 -- Lorin

---

