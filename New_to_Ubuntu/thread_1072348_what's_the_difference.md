---
title: "what's the difference?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by card_ace on 2009-02-17
this seems like kind of a dumb question, but i can't figure it out.  im working on downloading programs for my ubuntu and i'm wondering if theres a difference between GTK and KDE versions of the same program?

---

### Post by lukjad on 2009-02-17
As far as I know, if you install the GTK version, it looks and feels more like GNOME and the KDE version feels more like KDE. I also seem to remember hearing that installing the KDE version requires you to install a bunch of KDE base files for it to run, but I could be wrong.

---

### Post by snowpine on 2009-02-17
If you are running Ubuntu, the GTK version should run more efficiently on your system. If you were running Kubuntu, I would give the opposite advice. :)

---

### Post by Temposs on 2009-02-17
lukjad007 is correct.

Specifically, things like menus, buttons, the Open File dialog box look and act different.

GNOME and KDE are desktop environments.

GTK(Gnu Toolkit) is the code base for GNOME.

Qt is the code base for KDE.

So, each desktop environment uses different code as its foundation. So, if you start out using GNOME(standard Ubuntu) and you want to install a KDE program, it needs to install libraries built for KDE using Qt. And vice versa. There's no real downside to mixing the two except a KDE running in the GNOME environment won't have as much integration and will feel out of place. Sometimes a KDE-based program is the only/best one for the job, though!

---

### Post by card_ace on 2009-02-17
ok thanks.  i've been hearing about some programs but when i go to download them i found 2 different versions and just wasn't sure.  thanks for clearin that up!

---

### Post by Metallion on 2009-02-17
I guess you already know now but I'd like to try and explain in human terms just in case. :)

Gnome and KDE are a bit like the interior of a car. Even though the engine and other parts can be exactly the same, the interior is the eye candy you see and directly work with when you get in the car. Gnome and KDE are this for linux. They run on the same system but they're the interfaces you see on your screen and directly interact with.

Then there's the difference between Gnome and KDE versions op apps. Gnome is written on gtk and KDE is written on qt. You could see this as a car's interior made out of leather or wood. It's perfectly possible to install a wooden part into a leather interior. It would work perfectly but just look a bit out of place. That's Gnome and KDE's relationship exactly. :)

---

### Post by hello_kitty on 2009-02-17
> **Metallion said:**
> I guess you already know now but I'd like to try and explain in human terms just in case. :)

Gnome and KDE are a bit like the interior of a car. Even though the engine and other parts can be exactly the same, the interior is the eye candy you see and directly work with when you get in the car. Gnome and KDE are this for linux. They run on the same system but they're the interfaces you see on your screen and directly interact with.

Then there's the difference between Gnome and KDE versions op apps. Gnome is written on gtk and KDE is written on qt. You could see this as a car's interior made out of leather or wood. It's perfectly possible to install a wooden part into a leather interior. It would work perfectly but just look a bit out of place. That's Gnome and KDE's relationship exactly. :)

I like your analogy!  :D

---

