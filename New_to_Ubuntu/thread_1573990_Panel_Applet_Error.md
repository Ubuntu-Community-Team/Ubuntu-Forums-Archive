---
title: "Panel Applet Error"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Information Overload on 2010-09-13
I have customized my system a lot, downloading software, customizing themes, and other such things. And I have had my panel destroyed several times forcing me to reinstall Ubuntu. I still have my panel, but it is missing the shutdown options and whenever I first login it gives me this error:

The panel encountered a problem while loading.
"OAFIID:GNOME_FastUserSwitchApplet".

And then it asks me if I want to delete the applet. I have said yes and no on several occasions but the applet error doesn't seem to go away. Nothing else seems wrong with my system except when I go into the panel preference program it doesn't load. Can anyone tell me whats wrong or how to delete the applet so I don't see this error again? I don't wanna have to reinstall Ubuntu again. Any help is greatly appreciated!

---

### Post by kerry_s on 2010-09-13
you don't have to reinstall just reset the panel.

open your file manager & press "ctrl+h" to see hidden folders/files go to->
.gconf-> apps
delete the folder "panel"

log out & back in

---

### Post by Information Overload on 2010-09-14
Okay I'll try that.

---

### Post by Information Overload on 2010-09-14
Okay I tried that only one problem: my gconf doesn't have an apps file...

Heres a screenshot of my gconf file.

---

### Post by kerry_s on 2010-09-14
> **Information Overload said:**
> Okay I tried that only one problem: my gconf doesn't have an apps file...

Heres a screenshot of my gconf file.

wrong place, it's in your home folder.

---

### Post by Information Overload on 2010-09-15
My home folder just has the username folder in it that just contains documents and such. Sorry if i'm missing the point here but I'm a little new to Linux and I think the folders are named differently on the different Ubuntu systems. So my home folder might not be the folder you're thinking of. I'll keep looking for the right folder though and hopefully this will all be resolved soon. I like Ubuntu and Linux despite having it crash on me five times. ><

---

### Post by Information Overload on 2010-09-15
I looked in my etc file and found a gconf file but no luck on the apps folder. ](*,)

EDIT: Found it!!! I had to hit ctrl+h in my home folder but I found the right one.

Sorry for being thick when it comes to Linux.

Thanks so much for your help!

---

