---
title: "Problems with themes for Ubuntu"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Marfish on 2009-10-09
K, so I have GTK as well as emerald. I can can get emerald themes on it just fine, but when I try to put a theme for GTK that colours the inside of each window and toolbars in windows. It leaves the toolbar at the top of the screen, half without the theme. So while half the bar is nice and glossy, the other half is dull with the default. It only seems to want to colour the areas that have apps on it, the other areas of the bar aren't covered. Everything else is working fine for the theme, why only the toolbar? Ive also had this problem with two themes, so I'm under the impression it's not the themes fault.

---

### Post by ankspo71 on 2009-10-09
Hi,
I get this when applying new themes too. It seems to only happen with themes that use images for the panels (toolbars). For me it always went away after logging out and back in, or restarting the computer. So that would be my advice, log out or restart.
Hope that helps,
James.

---

### Post by Marfish on 2009-10-09
So far, rebooting has not soloved the problem. Nothing has changed.

---

### Post by Jesus_Valdez on 2009-10-09
Wich half? as in up and down? 

If that's the case, maybe the toolbar is just big and the theme is not prepare for toolbar that high.

It happens to me with certain themes.

---

### Post by Marfish on 2009-10-09
No, the start menu for example, is completely in the theme. Where it stops, is where the bar doesnt have the theme. It only goes around the icons. sort of like

\\\\\\\\\*********\\\\\\\\\    
=  The toolbar at top of page.

There's no theme in the middle portion because there arent really any icons.

---

### Post by gdonwallace on 2009-10-09
I have had the same problem in the past.  It usually starts popping up after I download and install a couple of themes from gnome-look.  

If I delete the themes from the ~/.themes folder, it fixes the problem.  It fixes the problem, but then the theme that I want to use is no longer on the machine.  Not a real fix, but one that will get rid of the problem.

Sorry I could not be of any more use.

---

### Post by Marfish on 2009-10-09
> **gdonwallace said:**
> I have had the same problem in the past.  It usually starts popping up after I download and install a couple of themes from gnome-look.  

If I delete the themes from the ~/.themes folder, it fixes the problem.  It fixes the problem, but then the theme that I want to use is no longer on the machine.  Not a real fix, but one that will get rid of the problem.

Sorry I could not be of any more use.

So your fix involves not having the theme at all? I've dont that, but I was sort of hoping to have something a little nicer than the given ones :(

---

### Post by Marfish on 2009-10-10
Lol, I'm an idiot. Problem solved. I had the bar properties set on solid colour rather than none(theme).

---

