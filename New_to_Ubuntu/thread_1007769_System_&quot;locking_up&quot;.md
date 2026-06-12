---
title: "System &quot;locking up&quot;"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Spartan22x on 2008-12-10
My system has been sort of locking up, but not really. What happens is it gets stuck in one specific program, and I can't click out of it or even move the window. It doesn't let me click anything outside of the current window, and even my compitz "hot corner" doesn't work when this happens. I only started noticing this after I installed Morrowind with Wine, but I don't think that's the cause of this behavior. Does anyone have any ideas?

I'm on a macbook if it matters, and it doesn't look like my processor load or memory is spiking during this, although for some reason the system is constantly using about 428 MB of memory with only firefox, nautilus, pidgin, and the system monitor open.

Edit: sometimes even clicking within the application doesn't work. Also, it doesn't seem to let me close applications or do anything in their window bar.

Oh, and I forgot to mention, I'm on Intrepid, running gnome. I have desktop effects set to custom, which is the same as full for me, plus a hot corner

For some reason it's not even letting me click toolbars either

---

### Post by gettinoriginal on 2008-12-11
open terminal and type > xkill  or you can do alt f2 and type the same thing

---

### Post by Spartan22x on 2008-12-11
> **gettinoriginal said:**
> open terminal and type > xkill  or you can do alt f2 and type the same thing

Thanks. Is there any way to prevent it from happening? Settings I should check, stuff like that?

---

### Post by heathlair on 2008-12-11
Try disabling desktop effects then turn them on one at a time until the problem reappears.

---

### Post by pgdave on 2008-12-12
I have the same problem, and wine is the cause. When switching tasks back to the wine task, the system seizes - it runs so slowly that turning the mains off is the only practicable solution. I'd like to know what to do about it. The upgrade to Intrepid is what started the problem - under Gutsy, it was fine. (Wine 1.1.9)

---

### Post by donkyhotay on 2008-12-12
My recommendation is to not alt-tab out of wine if it's fullscreen. It does really odd things to your system especially if you have desktop effects running. I don't use wine very often (starcraft is the only reason it's even installed) but I've found it's best to either run it in a window if I need quick access to my other programs or be willing to quit the program entirely to do something else if I want fullscreen.

---

