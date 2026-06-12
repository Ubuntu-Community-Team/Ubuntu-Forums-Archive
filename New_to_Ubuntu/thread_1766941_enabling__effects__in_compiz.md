---
title: "enabling  effects  in compiz"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by quarkhirad on 2011-05-25
I have  installed ubuntu  11.04 on  my  system then  i installed compizconfig settings manager. Now if i   open the  compiz manager and enable any  of the following effects i loose my  menu bar on  the  desktop(see fig) :

1)Magnifier
2)widget layer
3)animations add-on

How can i enable the add-on and still have by menu bar.

[IMG]http://www.badongo.com/pic/13037308[/IMG]

[IMG]http://www.badongo.com/pic/13037316[/IMG]

---

### Post by urbietorbi on 2011-05-25
11.04 and compiz are not playing nice. You may need to return to Unity's default settings. Hope this helps:

[http://askubuntu.com/questions/38858/messed-up-with-unity-compiz](http://askubuntu.com/questions/38858/messed-up-with-unity-compiz)

---

### Post by wildmanne39 on 2011-05-25
> **quarkhirad said:**
> I have  installed ubuntu  11.04 on  my  system then  i installed compizconfig settings manager. Now if i   open the  compiz manager and enable any  of the following effects i loose my  menu bar on  the  desktop(see fig) :

1)Magnifier
2)widget layer
3)animations add-on

How can i enable the add-on and still have by menu bar.

[IMG]http://www.badongo.com/pic/13037308[/IMG]

[IMG]http://www.badongo.com/pic/13037316[/IMG]
Hi, this is the guide for setting up the cube in natty, I used it and it works it required logging out and back in a few times. [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html) :)

---

### Post by quarkhirad on 2011-05-25
> **urbietorbi said:**
> 11.04 and compiz are not playing nice. You may need to return to Unity's default settings. Hope this helps:

[http://askubuntu.com/questions/38858/messed-up-with-unity-compiz](http://askubuntu.com/questions/38858/messed-up-with-unity-compiz)

Thanks it did help. But if compiz and unity do  not gell.Thats  really  sad :( :( :( :(  :(. That means i cant have all my fancy effects which are   in the animations effects.  

This really makes me wounder if i should go back to 10.04. Anyway for the moment i shall use  11.04.

Thanks urbietorbi

---

### Post by wildmanne39 on 2011-05-25
> **quarkhirad said:**
> Thanks it did help. But if compiz and unity do  not gell.Thats  really  sad :( :( :( :(  :(. That means i cant have all my fancy effects which are   in the animations effects.  

This really makes me wounder if i should go back to 10.04. Anyway for the moment i shall use  11.04.

Thanks urbietorbi
Hi, I have all mine read my post.

---

### Post by ngubk on 2011-05-25
You can still keep some including the effects you mentioned above. In my case, i logout/restart and the screen returns to normal.

---

### Post by quarkhirad on 2011-05-25
> **wildmanne39 said:**
> Hi, I have all mine read my post.

hey i followed all the steps in  your link and got  some  of my  effects back. Then at the end i restarted the graphical  environment and  i  had my desktop cube. I then fired up compiz config and then tried enabling widget layer and  once again the menu bar vanished. I  restored it later. 

I then realised that you have to first enable all the plugins  and  then at the end enable unity plugin. Hence i suggest the following modification in you link.                 


Disable Plugins

1. Ubuntu Unity Plugin
2. Desktop Wall
3. OpenGL (Choose 'Disable these plugins' when it asks it would disable some other plugins too)
4. Composite

Enable Plugins

1. Composite
2. OpenGL
3. Desktop Cube
4. Rotate Cube
5. Animations
6. Enhanced Zoom Desktop
7. Expo
8. Fading Windows
9. Enable any  other  plugins  you wish like  widget   layer, magnifier, animations  add-on etc. 
10. Ubuntu Unity Plugin

Once all the above mentioned plug-ins have been enabled ............



Hence i think that the problem is that you cannot enable any extra effects when the  unity  plugin is  enabled.

---

### Post by wildmanne39 on 2011-05-25
> **quarkhirad said:**
> hey i followed all the steps in  your link and got  some  of my  effects back. Then at the end i restarted the graphical  environment and  i  had my desktop cube. I then fired up compiz config and then tried enabling widget layer and  once again the menu bar vanished. I  restored it later. 

I then realised that you have to first enable all the plugins  and  then at the end enable unity plugin. Hence i suggest the following modification in you link.                 


Disable Plugins

1. Ubuntu Unity Plugin
2. Desktop Wall
3. OpenGL (Choose 'Disable these plugins' when it asks it would disable some other plugins too)
4. Composite

Enable Plugins

1. Composite
2. OpenGL
3. Desktop Cube
4. Rotate Cube
5. Animations
6. Enhanced Zoom Desktop
7. Expo
8. Fading Windows
9. Enable any  other  plugins  you wish like  widget   layer, magnifier, animations  add-on etc. 
10. Ubuntu Unity Plugin

Once all the above mentioned plug-ins have been enabled ............



Hence i think that the problem is that you cannot enable any extra effects when the  unity  plugin is  enabled.
Hi, I did what it said, then I did enable some more effects I just logged out and back in and it fix the bar it did not require a reset.

---

### Post by quarkhirad on 2011-05-26
> **wildmanne39 said:**
> Hi, I did what it said, then I did enable some more effects I just logged out and back in and it fix the bar it did not require a reset.

Ok thanks for the tip. 

Though just one more thing i do remember having my cube transparent and then having the option of having a fish bowl in it with different fishes  in my ubuntu 10.04. Here there is an option to render gears  only. I dont remember how i did the fish bowl thing.Do you have any idea?

---

### Post by beew on 2011-05-26
> **quarkhirad said:**
> Ok thanks for the tip. 

Though just one more thing i do remember having my cube transparent and then having the option of having a fish bowl in it with different fishes  in my ubuntu 10.04. Here there is an option to render gears  only. I dont remember how i did the fish bowl thing.Do you have any idea?

That is called cube Alantis, it is not in the normal Compiz package, you must have installed the experimental or unsupported Compiz package in 10.04 (don't remember exactly what it is called) but that package was not around in 10.10. To get those you would then have to download a script and run it. But that no longer works on 11.04.

See this thread [http://forum.compiz.org/viewtopic.php?f=114&t=12012&start=40](http://forum.compiz.org/viewtopic.php?f=114&t=12012&start=40)

Anyhow I think transparent desktop uses a lot of cpu cycles and actually slows things down a lot, I played with it for maybe 10 minutes and never use it again. :)

Edited: screenshot is taken in 10.10.

---

### Post by wildmanne39 on 2011-05-26
> **quarkhirad said:**
> Ok thanks for the tip. 

Though just one more thing i do remember having my cube transparent and then having the option of having a fish bowl in it with different fishes  in my ubuntu 10.04. Here there is an option to render gears  only. I dont remember how i did the fish bowl thing.Do you have any idea?
Hi, when you chose the gears the one next to it says atlantis that is the one you need to use for the fish.:D

---

### Post by quarkhirad on 2011-05-28
> **wildmanne39 said:**
> Hi, when you chose the gears the one next to it says atlantis that is the one you need to use for the fish.:D

Sorry  no atlantis next  to  gears. Even when i tried using the search  box.I typed "atl" and it said sorry no match's found    

:(  :(

---

### Post by wildmanne39 on 2011-05-28
> **quarkhirad said:**
> Sorry  no atlantis next  to  gears. Even when i tried using the search  box.I typed "atl" and it said sorry no match's found    

:(  :(

Hi, now mine is gone to, I guess an update took it away.

---

