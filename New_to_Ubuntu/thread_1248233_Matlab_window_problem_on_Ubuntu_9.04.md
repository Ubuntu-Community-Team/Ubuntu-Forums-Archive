---
title: "Matlab window problem on Ubuntu 9.04"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by wirelinux on 2009-08-23
Hello Everyone

I have installed MATLAB 7.4 (R2007a) on Ubuntu 9.04.

I have problems with Matlab desktop, Editor window, figure window, array editor window.
The menu bars, toolbars etc on any of these windows are not visible, BUT if i _click_ on the menu bar items, toolbar items, then the relevant text/dialog box seems to pop-up.

But if i dock any of these windows, they become visible. If i undock them again, they become invisible .
I don't understand how this works.

I have attached the screenshots of Command window, Editor window, Figure window for better understanding of what's going on.

Please help me with this problem.

---

### Post by nhasian on 2009-08-24
do you have an intel video adaptor?

```
lshw -C display
```

I know jaunty had some problems with intel graphics adaptors.  they work much better in Karmic Koala 9.10

---

### Post by ad_267 on 2009-08-24
You could also try disabling compiz by going to System - Preferences - Appearance - Visual Effects - None.

---

### Post by wirelinux on 2009-08-24
Thanks for ur reply.
Yeah i have Intel video drivers

here is the output of lshw -C display

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

Karmic Koala 9.10 is this the next release in Oct 2009??
What should i do now to resolve this issue??
Any help will be greatly appreciated.

Thanks

---

### Post by wirelinux on 2009-08-24
Thank u very much.
Ur workaround works:):P
When u reduce the visual effects to a baseline mode as compared to normal mode, Advanced mode, i can understand that load on Graphics card is reduced. Can u explain to me how the solution worked.??
I am not into Computer Science, i am a Electrical Engg PhD student.

i have the command window, editor window, figure window screenshots attached.
they r fine now!!!

---

### Post by ad_267 on 2009-08-24
Well I don't really know exactly how the solution works, but with visual effects enabled you are actually using a different window manager called Compiz. This is a compositing window manager, meaning it can use transparency effects. It works very differently to the default window manager, called Metacity, and can be buggy on some video cards. I just guessed that disabling it could help with your situation. As nhasian said, upgrading to Karmic would upgrade the intel drivers to a more recent version so could also fix your problem, but Karmic is still in alpha so it's not recommended for most users.

---

