---
title: "Blender isn't displaying correctly Ubuntu 9.10"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by helloworld922 on 2010-03-10
I'm having some problems with running Blender. I just installed the wubi standard 32 bit Ubuntu 9.10 and have 2.49a blender installed from the ubuntu repository.

When I tried running blender, it comes up, but the main blender frame renders strangely and there's no title bar. I'm trying to run it in windowed mode with a simple 'blender' command. I've also tried 'blender -W', 'blender -p 0 0 1024 768', and neither has worked.

Some info about my system: It's a Toshiba satellite with an ati x1250 integrated graphics card. It is basically a fresh install of ubuntu 9.10 with the automatic updates performed.

I'm not very used to running linux systems, but I have a basic knowledge. I've attached some screenshots of what's happening. The first one is of the missing title bar (i'm not sure what it's called, but it's the bar with the program name, icon, and the maximize/minimize/close buttons on it). The second picture is of the screen not being redrawn correctly when I move a second application/dialog box over the blender window.

thanks in advance!

---

### Post by themusicalduck on 2010-03-10
It might be that the graphics drivers aren't quite working properly.

Have you installed any drivers for your ATI card? You could look at System > Administration > Hardware Drivers to see if there is something there.

Another thing you could try is to disable compiz effects. Go to System > Preferences > Appearance. On the Visual Effects tab select None.

---

### Post by helloworld922 on 2010-03-11
On some of my previous attempts to get Ubuntu working I did install the open version of ATI's graphics driver and CCC. I've also tried installing the proprietary drivers (on a different installed Ubuntu), but it keeps telling me that my system doesn't meet the requirements.
 
I'll try turning off the visual effects to see if that works.

---

### Post by sdpiowa on 2010-03-11
I would recommend downloading 2.5 Alpha 2.  I was having some similar issues, but later versions of the software fixed it.

I use Blender a lot, but I use it in a 64-bit configuration.

---

### Post by helloworld922 on 2010-03-12
Ok, turning off the visual effects worked. Thanks! I'll give blender 2.5 alpha 2 a try later, too.

---

