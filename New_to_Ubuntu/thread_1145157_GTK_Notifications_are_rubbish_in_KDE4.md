---
title: "GTK Notifications are rubbish in KDE4"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Mazza558 on 2009-05-01
I'm loving Kubuntu, but one annoying thing is the notifications for Pidgin and other GTK programs, which comes up as an ugly yellow unmovable fallback notification rather than using KDE's. I'd like to either:

1. Run the normal Ubuntu Jaunty notifications on Kubuntu (notify-osd, what's the command to launch this in terminal?)

2. Get GTK apps to use KDE notifications

3. Turn off pidgin notifications, but I'd really not want to do this.

---

### Post by NightwishFan on 2009-05-01
You should probably not run Notify-OSD in KDE.

---

### Post by nikolardo on 2009-05-23
I have the same thing with my pidgin notifications.  They look absolutely terrible.  If they could appear with the normal KDE notifications that would be lovely.

---

### Post by Tibuda on 2009-05-23
What about Kopete?

---

### Post by nikolardo on 2009-05-23
I actually just tried Kopete.  I really didn't like the interface too much.  I might fiddle around with it at some point, but I prefer Pidgin's larger icons and text on the buddy menu, and I was also unimpressed by the notifications...they were much better than for pidgin, but not great.
If it's not possible to make pidgin use the KDE notification system, is there any way to change the default ugly yellow that it falls back on?  Or, as Mazza558 said, disable them altogether?  (The main problem I have with the Kopete notifications is that there is a "view" and "ignore" button, and if you don't hit either, the notification won't go away.  I like that the ugly yellow ones just show themselves and disappear, it's only how they look that's bad.

---

### Post by anewguy on 2009-05-23
If you feel up to making pidgin from source, I have just downloaded the source and was glancing at it.  I think the colors are set in the gtkrc-2.0 module (just from first quick glance).  you may want to try changing the hex values there for other colors and re-making pidgin to see if it helps.

I don't know if pidgin, or any of the other tools you have tried, have a runtime configuration file - if so, you may want to look there for colors.

I haven't done it lately, but in the "old" days we used to provide a runtime config file just so such things as colors, etc., could be specified for our applications.

I'll keep looking at the source and see if I see anything else.

Dave :)

---

### Post by Mazza558 on 2009-05-24
I'm using Karmic now, and on KDE 4.3, pidgin seems to use the new notifications (not KDE's), which is much better behaviour. I actually prefer these notifications to KDE's, because KDE's sometimes get in the way.

Why Pidgin? Simple and supports Facebook chat too.

---

