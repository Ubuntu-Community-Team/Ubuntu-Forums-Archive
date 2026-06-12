---
title: "Kubuntu login and logoff screen in ubuntu."
date: 2011-02-13
forum: New to Ubuntu
---

### Post by abnordude on 2011-02-13
I installed ubuntu. then i used apt to integrate kubuntu into ubuntu.
Now i'm getting kubuntu login and logoff screens. I just want to use the default ubuntu login /logoff screen.
Please suggest a way to change it.

---

### Post by candtalan on 2011-02-14
I am not *sure* but I think that looking for 'kubuntu' graphic stuff using synaptic package manager may be helpful. I think that once I  removed the kubuntu graphic whatever, My similar problem to yours, went. This was  some long time ago.

ISTR that Kubuntu starts using different procedures than Ubuntu, so if you find some kubuntu graphics and remove, it is possible that kubuntu may have some complications. I guess then you could reinstall kubutu-desktop to re instate.

---

### Post by Trooper_Max on 2011-02-14
The login managers you're talking about are called gdm (for Gnome/regular Ubuntu) and kdm (for KDE/Kubuntu).

You may be able to go to the package manager and remove kdm, but if not, try to find gdm and look for the Configure option in the menus so you can reconfigure it. That should give you option to set your login manager.

Or you might try this from the terminal:

**sudo dpkg-reconfigure gdm**

I think something in there should work, but I haven't verified...

~Troop

---

### Post by abnordude on 2011-02-17
Thanks Guys. Problemo solved.

---

