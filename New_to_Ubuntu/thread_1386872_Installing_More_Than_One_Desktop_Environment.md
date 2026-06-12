---
title: "Installing More Than One Desktop Environment"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-21
A post in another thread that I found interesting said:

> **Dayofswords said:**
> did you choose it as a session? after clicking your name at the log in screen(if you have it that way) there's an option at the bottom where you can select Gnome, KDE, xfce, blah blah, you should be able to slect it from there, then log in in

it will only show what environments you have installed

The only DE I have on my PC is Gnome (Ubuntu), although I've changed it quite radically from the standard set-up. For example, I only have one panel, and it's at the bottom of the screen. I like this arrangement, and I don't want any tinkering I do to mess it up.

That being said, I'd rather like to see what KDE looks like, so I'd like to have the option mentioned to boot into one of various DEs at login time.

Would I get what I'm seeking just by installing the kubuntu-desktop package, including all its dependencies?

Would this add KDE-specific apps (such as Dolphin, Konqueror, etc.) to the Applications list in my current Gnome set-up? And would my current Gnome-specific apps (e.g. Nautilus, etc.) be in KDE's list of Applications? 

Is there any danger that my current set-up of Gnome will be compromised by adding a KDE option?

---

### Post by pranayama on 2010-01-21
Installing kubuntu-desktop adds a full KDE environment. When logging on you can then choose to log in to a Gnome or KDE session.

Dolphin and Konqueror will be there.

I have not come across any KDE applications which don't work in Gnome and vice versa.

The risk of breaking anything is low.

You may find some applications take on a Qt look in Gnome after using KDE for the first time.

---

### Post by tacantara on 2010-01-21
> **Roger Allott said:**
>  Would I get what I'm seeking just by installing the kubuntu-desktop package, including all its dependencies?

Downloading the kubuntu-desktop package from Synaptic should install the DE and all dependencies.

> **Roger Allott said:**
>  Would this add KDE-specific apps (such as Dolphin, Konqueror, etc.) to the Applications list in my current Gnome set-up? And would my current Gnome-specific apps (e.g. Nautilus, etc.) be in KDE's list of Applications? 

The standard KDE apps that come with Kubuntu will be present in when you install the package.  Your GNOME apps should also appear in the KDE "start menu," however, bear in mind that they're designed to work optimally in the GNOME DE, thus you might find that they're a "bit off" when run in KDE.

> **Roger Allott said:**
>  Is there any danger that my current set-up of Gnome will be compromised by adding a KDE option?

In my experience with running multiple DEs, I've found that there are no major issues.  I've done the GNOME/KDE thing, and I currently have a GNOME/XFCE setup with Karmic.

---

### Post by warfacegod on 2010-01-21
There should be no issues with what you are considering. Don't be surprised if you're Ubuntu logo changes to Kubuntu, for instance.

---

### Post by HarrisonNapper on 2010-01-21
> **warfacegod said:**
> There should be no issues with what you are considering. Don't be surprised if you're Ubuntu logo changes to Kubuntu, for instance.

You can, however, change it back, which I suppose should stand to reason. It is linux, after all.

---

### Post by Roger Allott on 2010-01-21
> **pranayama said:**
> 
You may find some applications take on a Qt look in Gnome after using KDE for the first time.

Oddly, it happened the other way round.

After I installed kubuntu-desktop and its dependent packages, I looked at my System Monitor and that had become Qt. I then looked at USB Startup Creator, and that had also become Qt.

So I rebooted the PC and at login, I selected KDE.

Unfortunately, I couldn't connect to the web. Can't figure out why not, but Kubuntu's network manager doesn't like me.

I then logged out of Kubuntu and logged back into Gnome. Everything as normal, which is nice, even System Monitor and USB Startup Creator, which was surprising.

---

