---
title: "Blender Error PLEASE HELP ME!!"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Penguin=) on 2010-12-04
OK, So i wanted to make a new animated title in OpenShot, but when i go to Title-->New animated title--> and choose one of the presets, it says EXACTLY this:

Blender, the free open source 3D content creation suite is required for this action ([http://www.blender.org](http://www.blender.org)).

Please check the preferences in OpenShot and be sure the Blender executable is correct.  This setting should be the path of the 'blender' executable on your computer.  Also, please be sure that it is pointing to Blender version 2.5 or greater.

Blender Path:
blender

Can anyone help me please?
thanks

---

### Post by Penguin=) on 2010-12-04
can anyone help?

---

### Post by jplo on 2010-12-04
Try installing blender from the Software Centre. OpenShot should just work when this is done :)

---

### Post by Penguin=) on 2010-12-04
> **gerbilschool said:**
> Try installing blender from the Software Centre. OpenShot should just work when this is done :)


Tryed it, diden't work =(

---

### Post by jplo on 2010-12-04
> **Penguin=) said:**
> Tryed it, diden't work =(
#

When Blender is installed, try typing ```
/usr/bin/blender-bin
``` in the dialogue box.

---

### Post by Penguin=) on 2010-12-04
> **gerbilschool said:**
> #

When Blender is installed, try typing ```
/usr/bin/blender-bin
``` in the dialogue box.

Nope i set it as the exectuable, but still no luck =(

---

### Post by Daveth on 2010-12-04
there is a ppa of the 2.53 beta here you might try

[HTML]http://www.webupd8.org/2010/07/blender-253-beta-3d-graphics.html[/HTML]

---

### Post by Penguin=) on 2010-12-04
> **Daveth said:**
> there is a ppa of the 2.53 beta here you might try

[HTML]http://www.webupd8.org/2010/07/blender-253-beta-3d-graphics.html[/HTML]


Hey,thanks for your reply.

I am doing the PPA thing now in terminal, are you sure this will work, and do i need to change the blender executable in OpenShot?

thanks

---

### Post by Penguin=) on 2010-12-04
> **Daveth said:**
> there is a ppa of the 2.53 beta here you might try

[HTML]http://www.webupd8.org/2010/07/blender-253-beta-3d-graphics.html[/HTML]


ok i got it, but its STILL showing that message!!! any ideas?

---

### Post by jplo on 2010-12-04
> **Penguin=) said:**
> ok i got it, but its STILL showing that message!!! any ideas? try just** usr/bin/blender **(*not blender-bin)*

---

### Post by Penguin=) on 2010-12-04
> **gerbilschool said:**
> try just** usr/bin/blender **(*not blender-bin)*


Still no luck, this is kinda complicated!

---

### Post by Daveth on 2010-12-07
does it show Blender as actually being installed in the software centre after you have run the ppa routine? Does it not show up in the menu options either? Seems odd you cannot get anything from the terminal command.

---

