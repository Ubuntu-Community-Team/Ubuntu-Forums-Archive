---
title: "How to automatically start nm-applet"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Arla on 2009-08-19
Okay, so I've changed around all my network settings and am using nm-applet to get on my wireless network (works great, the KDE version seems to be horrific).

However, I have to run it every time I start, how can I get it to auto-start? (sorry, really new to this whole unix thing).

---

### Post by diablo75 on 2009-08-19
In Ubuntu 9.04:

System>Preferences>Startup Applications

You then add a new item and type nm-applet for the command.

In older versions of Ubuntu, the word "Startup Applications" was something like "Sessions", but worked the same way.

---

### Post by ptn107 on 2009-08-19
nm-applet is already in System -> Preferences -> Startup Applications listed as Network Manager.  The command it has is: ```
nm-applet --sm-disable
```

---

### Post by Ji Ruo on 2009-08-19
I don't know how helpful the above replies were as they are both for the GNOME desktop and not KDE (Kubuntu).

For Kubuntu, you want to go to K Menu>System Settings, then click on the 'advanced' tab, 'Autostart' and 'Add Program'. Then type in 'nm-applet' and click OK (I'm not sure what the '--sm-disable' argument that ptn107 has mentioned is for, but I don't think you need it).

You're right about the new network manager! It's the reason I've stuck with Intrepid for my Kubuntu install. Hope the KDE developers have this fixed by the time Karmic is due for release.

---

### Post by roomey on 2011-03-21
> **Ji Ruo said:**
>  You're right about the new network manager! It's the reason I've stuck with Intrepid for my Kubuntu install. Hope the KDE developers have this fixed by the time Karmic is due for release.

Yea, you can chalk that down. Sick of wrestling with the standard KDE network manager. This may sound crazy, but I reached the end of my patience when i removed the icon from the tool bar- And couldn't see how to add it back in!

I will try out that solution listed above.

---

### Post by wizard10000 on 2011-03-21
> **roomey said:**
> Yea, you can chalk that down. Sick of wrestling with the standard KDE network manager. This may sound crazy, but I reached the end of my patience when i removed the icon from the tool bar- And couldn't see how to add it back in!

I will try out that solution listed above.

Or you might try wicd.  I've been a lot happier with wicd under KDE than any networkmanager variant.

---

