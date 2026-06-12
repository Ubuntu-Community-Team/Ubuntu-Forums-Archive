---
title: "power manager/screen saver sometimes working"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by mustard greens on 2009-12-01
my power management/screen saver capabilities seem to turn themselves on then off with 9.10 upgrade.  through the GUI I have them both enabled and yet sometimes have found them to not be working. conversely, or maybe this should be another post, but the screen saver also is activating during VLC movie watching.  any clues?

---

### Post by ikt on 2009-12-02
> **mustard greens said:**
> the screen saver also is activating during VLC movie watching.  any clues?

I think I have the same issue, I've just set both options in power management to never and 'make default' ed them, I'll report back if the screensaver interrupts while watching VLC.

---

### Post by ikt on 2009-12-03
> **ikt said:**
> I think I have the same issue, I've just set both options in power management to never and 'make default' ed them, I'll report back if the screensaver interrupts while watching VLC.

just to confirm this does look like a bug.

---

### Post by ukripper on 2009-12-03
Gnome power manager has many bugs reported on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager)

---

### Post by ikt on 2009-12-03
> **ukripper said:**
> Gnome power manager has many bugs reported on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager)

Looked a little further and it was the screensaver activating after 5 minutes of idle time, so I've increased that to 2 hours so hopefully no more black screens in the middle of watching a movie.

---

### Post by ukripper on 2009-12-03
> **ikt said:**
> Looked a little further and it was the screensaver activating after 5 minutes of idle time, so I've increased that to 2 hours so hopefully no more black screens in the middle of watching a movie.

Yeh i remeber it was another bug. Where if you set it to never, it doesn't work. 2 hours workaround worked for many.

---

### Post by Excedio on 2009-12-03
For the time being, this might be of some help to you all.
 
[http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.htm](http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.htm)

---

### Post by mustard greens on 2009-12-04
yeah, I havent confirmed the bug status, but I havent been able to get power saver function to engage for three days despite being set to do so at different intervals.  will wait for the patch.

---

