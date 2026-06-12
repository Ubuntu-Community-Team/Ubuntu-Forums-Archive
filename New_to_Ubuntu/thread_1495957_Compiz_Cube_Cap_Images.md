---
title: "Compiz Cube Cap Images"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Lvcoyote on 2010-05-28
I've got compiz fusioon working well with 10.04 except for when I try and apply an image to the bottom cube cap.  I can get an image working for the top, but have not yet found a solution to applying an image to the bottom cube cap, in fact I can not even find an option to do so.

Anyone know how its done??

---

### Post by lsk3993 on 2010-05-28
> **Lvcoyote said:**
> I've got compiz fusioon working well with 10.04 except for when I try and apply an image to the bottom cube cap.  I can get an image working for the top, but have not yet found a solution to applying an image to the bottom cube cap, in fact I can not even find an option to do so.

Anyone know how its done??
EDIT:From [http://wiki.compiz.org/Plugins/Cube](http://wiki.compiz.org/Plugins/Cube)
Although the Desktop Cube plugin can place an image on  the top face of the cube, the *Cube Caps* implementation in this  plugin [cube reflection and deformation] provides more versatility, as well as allowing for correctly  shaped cube caps when using the *Cylinder* or *Sphere*  deformations. Unlike with the implementation in Desktop Cube,  both the top and bottom caps can be set. Different background colours  can also be set for each cap; the caps can even be disabled altogether.

---

### Post by Lvcoyote on 2010-05-28
Oh man..... that sucks.....LOL.  Maybe I can apply a more appealing solid color to it then..... thanks!

---

### Post by lsk3993 on 2010-05-28
> **Lvcoyote said:**
> Oh man..... that sucks.....LOL.  Maybe I can apply a more appealing solid color to it then..... thanks!
Sorry, edited it with some more updated info. Seems it can be done
[IMG]http://i47.tinypic.com/py5hj.png[/IMG]

---

### Post by Lvcoyote on 2010-05-28
The problem is I dont have that option in the settings manager.....

---

### Post by lsk3993 on 2010-05-28
> **Lvcoyote said:**
> The problem is I dont have that option in the settings manager.....
Hmm that's odd, I have all of these: 
[IMG]http://imgur.com/00s9c.png[/IMG]
To be honest if an Ubuntu novice so I'm not sure if I'm right but could it be the version of CCSM you're using?

EDIT: Here we go, this seems to solve the problem
> sudo apt-get install compiz-fusion-plugins-extra

(Seems they left out the extras in 10.04 but since I updated as opposed to doing a fresh install I still had them from 9.10)

---

### Post by Lvcoyote on 2010-05-28
I needed compiz-fusion-plugins-extra package, installed that and everything is working perfectly now..... thanks for the help!

---

### Post by lsk3993 on 2010-05-28
> **Lvcoyote said:**
> I needed compiz-fusion-plugins-extra package, installed that and everything is working perfectly now..... thanks for the help!
No problem :)
You can mark thread as solved now...

---

