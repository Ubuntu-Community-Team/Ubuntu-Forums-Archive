---
title: "Post-Compiz problems"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-08-17
Out of curiosity I tried out Compiz, installed CompizConfig Settings Manager, and checked off a few options... "Maximumize", "Desktop Cube", "Cube Reflection and Deformation", etc. I'm clearly not doing something right, because nothing set my panties on fire, and there's no real cube at all, so far as I can tell.

Whatever, no big. The problem is that in enabling some of those options, I disabled other stuff that was managing my desktop. Now I have problems: When I switch to Workspace 2, the right button on my mouse does absolutely nothing, and panels start disappearing on both Workspaces. I have to start clicking around wildly to get them back. What gives? How do I make it all go away? Should I try disabling all visual effects, logging out, then going back to "Extra Effects"?

Thanks.

---

### Post by realzippy on 2009-08-17
"and there's no real cube at all"

"and panels start disappearing on **both** Workspaces."

If you want a cube,you need 4 workspaces.
CCSM/General/GeneralOptions/DesktopSize

set first slider to **4**.....

---

### Post by ricardisimo on 2009-08-17
Thanks for the reply, but I answered my own question:
System > Preferences > Appearance > Visual Effects = None, and then log out and back in. Then go back to "Extra Effects" and all is well again.

As for the cube, I kind of figured as much, but even with just the two desktops that I had, the switching was less than attractive. I prefer just the regular "Extra" with no bugs. Thanks again.

P.S. - Hmmm... the desktop switching is not quite back to how it was. It is "flipping" away now, pivoting from the top of the screen, rather than sliding left and right with the brief arrow icons appearing as they used to do. It's not the end of the world, and my mouse buttons are working, which is all I really care about, but if I did want the old look back, how would I do that?

---

### Post by ajgreeny on 2009-08-17
You could try disabling compiz with ```
metacity --replace
``` renaming the folder ~/.gconf/apps/compiz as ~/.gconf/apps/compizbak and then start compiz again with ```
compiz --replace
```This will remove all configuration you have set in the past and take you back to the defaults.

---

### Post by ricardisimo on 2009-08-17
But isn't metacity what I had to begin with? Do I want compiz back at any point?

---

### Post by mcduck on 2009-08-17
> **ricardisimo said:**
> But isn't metacity what I had to begin with? Do I want compiz back at any point?

If you have desktop effects set to "none" you use Metacity, the other two settings give pre-configured Compiz setups.

What comes to your problem with desktops flipping instead of sliding, that sounds like you still have the Cube plugin enabled instead of the Desktop Wall.

And the problem with strangely acting desktops with the Cube plugin, that sounds like you had set the amount of desktops to higher than one, instead of using the horizontal & vertical virtual sizes which are what you should use to control the amount of virtual desktops.

(normal cube setup would be horizontal virtual size of 4, vertical virtual size of 1 and number of desktops set to 1. If you then changed the number of desktops to 2, you'd get two cubes, each one with 4 virtual desktops. The problem, of course, is that all your panels etc. are by default only configured to run on the first desktop so your second cube would be just empty cube without any panels)

---

### Post by ricardisimo on 2009-08-17
I tried your suggestion. Didn't correct the problems I noted and others I'm noticing. Hopefully a reboot will do.

---

### Post by john_lee on 2009-08-17
Hi, I would like to ask if ubuntu has a freeware network client server?where can I download that software?please help me on my problem. Thank you

---

### Post by ricardisimo on 2009-08-17
I think I've taken care of it. Thanks to everyone who responded.

System > Preferences > CompizConfig Settings Manager => Preferences > Profile > "Reset to defaults"

Ta-Dah!

---

### Post by gradinaruvasile on 2009-08-17
Install Fusion-icon from Applications->add/remove
 
Makes life sooo much easier. You can switch compiz/metacity in 1 click, launch the settings manager etc.

---

