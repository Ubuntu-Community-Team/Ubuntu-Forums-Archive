---
title: "What does this new applet do?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by josephellengar on 2009-04-26
The one that says "monitors if something on your desktop needs your attention."  What does it do?  When I put it on my gnome panel, nothing showed up.  Thanks!

---

### Post by Kobalt on 2009-04-26
Isn't this the new notification system ? If so, you only see it when something like an IM contact connects, you connect to a wireless network, etc.

---

### Post by cariboo on 2009-04-26
THe new notfication system, works with all sorts of applications, for instance last week when I was downloading Jaunty via bittorrent, the system pop up a notification that the torrent was finished. When using the volume up/down keys on my keybaord there is also a notification on screen.

---

### Post by josephellengar on 2009-04-26
> **Kobalt said:**
> Isn't this the new notification system ? If so, you only see it when something like an IM contact connects, you connect to a wireless network, etc.

I thought that the new notification system was the little bubble that appears in the corner, which shows up whenever one of those events that you just mntionecd occurs.

---

### Post by lovinglinux on 2009-04-26
> **cariboo907 said:**
> THe new notfication system, works with all sorts of applications, for instance last week when I was downloading Jaunty via bittorrent, the system pop up a notification that the torrent was finished. When using the volume up/down keys on my keybaord there is also a notification on screen.

That is actually a different thing. The OP is referring to the "Indicator Applet" which is a tray icon that currently inform you about new e-mails and private messages. You can only see it if you open Pidgin or Evolution, because it only integrates with these applications, but the idea of this project is to integrate with all applications that put an icon in the "Notification Area". It  will eventually replace the "Notification Area" to save space on the panel.

---

### Post by Crowder on 2009-04-26
I've noticed that Pidgin has begun creating pop-up - or "pop-down," i suppose - notifications in the top right corner of the screen since my upgrade to jaunty. A box briefly appears when a buddy signs on or off with reading "[Buddy name] is Online" and showing the buddy's icon. Could this be a function of the indicator-applet?

I'm not sure if that's a part of it or if Pidgin updated. Could also be something else. I like that function.

> It will eventually replace the "Notification Area" to save space on the panel.

I have to say that if that little envelope icon is planned to replace the notification area, I do not approve. The little drop-down menu currently shows Pidgin, as I don't use Evolution, and appears to do absolutely nothing. I have plenty of room on my panels. It's ok to leave this as an option, but the notification area works fine, and should not be going away.

---

### Post by Wiebelhaus on 2009-04-26
I love it , It really seems to sophisticate the desktop and having it fade if you mouse over it was a nice touch.

Kudos.

---

### Post by Crowder on 2009-04-26
i like on-screen notifications, like you (sx66gns) and cariboo are talking about, but not the icon, mostly because I don't get what it's supposed to be accomplishing.

Here's one thing I've been wondering. Is there any way to add functionality for other apps (instead of just evolution and pidgin)? I had played around with "mumbles" for a while, and it was much more customizable.

---

### Post by llamabr on 2009-04-26
> **sx66gns said:**
> I love it , It really seems to sophisticate the desktop and having it fade if you mouse over it was a nice touch.

Kudos.

My favorite new verb of the day: sophisticate.  Thanks.

I've not seen this new feature.  Is it on by default?

---

### Post by lovinglinux on 2009-04-26
> **Crowder said:**
> i like on-screen notifications, like you (sx66gns) and cariboo are talking about, but not the icon, mostly because I don't get what it's supposed to be accomplishing.

Here's one thing I've been wondering. Is there any way to add functionality for other apps (instead of just evolution and pidgin)? I had played around with "mumbles" for a while, and it was much more customizable.

I guess new applications will be added in the future by developers. They probably need some new code to work with the applet.

---

### Post by josephellengar on 2009-04-26
> **llamabr said:**
> My favorite new verb of the day: sophisticate.  Thanks.

I've not seen this new feature.  Is it on by default?

I had this problem too.  The package doesn't come installed by default.  I think it's called notify-ocd, or something similar.  If you search notify in synaptic you should get it.  It's a really great feature.  Integrates nicely with twitux without you having to close out every popup window whenever you get a new tweet.  I just wish it would integrate with gmail-notify.

---

### Post by lovinglinux on 2009-04-26
> **idigchess said:**
> I had this problem too.  The package doesn't come installed by default.  I think it's called notify-ocd, or something similar.  If you search notify in synaptic you should get it.  It's a really great feature.  Integrates nicely with twitux without you having to close out every popup window whenever you get a new tweet.  I just wish it would integrate with gmail-notify.

Again, this is not the applet the OP is talking about. He is talking about the "Indicator Applet" which is installed by default. This is only visible when Pidgin or Evolution are open. It's like a daemon icon, that can hide/show the applications which is integrated to and alert about events, but is not the black pop up alert thing.

Package *indicator-applet*
> indicator-applet is an applet to display information from
various applications consistently in the GNOME panel.

Currently this includes support for messaging applications in the
indicator-messages package.

There is also the *indicator-messages* and *indicator-evolution*, that probably make the bridge between "Indicator Applet", "Pidgin" and "Evolution" so they can work together.

The *notify-osd* and *notify-daemon* packages are probably responsible for the black pop up thing and they are also installed by default.

> 
The Desktop Notifications framework provides a standard way of doing
passive pop-up notifications on the Linux desktop.  These are
designed to notify the user of something without interrupting their
work with a dialog box that they must close.  Passive popups can
automatically disappear after a short period of time.

---

### Post by Crowder on 2009-04-26
> I guess new applications will be added in the future by developers. They probably need some new code to work with the applet.

yeah, you'd think they'd let us work some of that out ourselves for the time being. Mumbles didn't support much more than this does, but at least it gave you the option of messing with DBus to make your own add-ons. I'm hoping someone figures out how to do the same for libnotify.

----------------------------------------------------------------------------------------------

I'm not sure why you guys are all saying that the package wasn't there by default, I just upgraded from intrepid and it was there.

---

