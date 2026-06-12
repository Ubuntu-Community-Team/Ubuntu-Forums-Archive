---
title: "Google Earth 5.0"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-04-29
I'm working with my parents old desktop computer, which has 9.04 installed (upgraded from 8.10). I installed Google Earth 5 from a .bin, which worked fine except when you look at the pictures (the blue squares) the window opens, but it's blank. If you select the text with a mouse you can see it's there.

I figured I screwed something up by installing the .bin, so I uninstalled google earth. Then, I got the .deb from medibuntu and installed that one.


I don't know what the problem is. It works fine on my computer. I'm guessing maybe it's a graphics issue? But I've got compiz working on their computer fine.

The program itself runs fine, it's just these pictures that do not work. Sometimes I can get to see the picture if I click on it and do not move the mouse.

Anyone have a fix?

---

### Post by Kobalt on 2009-04-29
It can be caused by a graphic card driver : which one do you have?

---

### Post by Lazy-buntu on 2009-04-29
I'm not even sure what they have. All I know is it's an older integrated ATI card.

---

### Post by taurus on 2009-04-29
Have you tried turning off compiz to see if you still get the same problem with Google Earth?

---

### Post by CLomax on 2009-04-29
I found that having Metacity's compositing feature or Compiz on causes this problem.

---

### Post by Lazy-buntu on 2009-04-29
> **CLomax said:**
> I found that having Metacity's compositing feature on causes this problem.

What's weird is I have compiz on my computer with nearly the exact configuration, but google earth works fine on my computer.


Anyway, did you disable that feature to fix the problem? If so, how?

edit: Their computer isn't using Metacity window manager.

---

### Post by Lazy-buntu on 2009-04-29
I switched from compiz window manager to metacity window manager, and it works for some reason.

Maybe I'll tweak the settings and go from there.

Thanks guys :P

---

### Post by CLomax on 2009-04-29
> **Lazy-buntu said:**
> Anyway, did you disable that feature to fix the problem? If so, how?

edit: Their computer isn't using Metacity window manager.

I used Ubuntu Tweak: [http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak)

If their computer isn't using Metacity then I have no idea what to suggest. :(

**EDIT;**
Glad to see it's working :)

---

### Post by Lazy-buntu on 2009-04-29
Scratch that victory dance. I imported my old compiz settings even though they're using metacity now and it's doing the same thing.

---

### Post by HyperX on 2009-04-29
I have not been able to get google earth to work on my x300 laptop with integrated intel graphics card.

---

