---
title: "Problem With Visual Effects in Jaunty"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by t4nv1r on 2010-02-17
Hi,
I just installed Ubuntu 9.04 a few days ago. Now after installing my graphics driver [ nvidia GeForce2 mx/mx 400 64mb AGP ] i enabled the visual effects. But after i enabled it my title bars go away, also the terminal doesnt run. But i set my visual effects to normal everythings back to normal. Any suggestions how to fix this?

---

### Post by Sealbhach on 2010-02-17
Sounds like the Window manager, Compiz, is not installed or not working properly. Check in Synaptic Package Manager  - search for compiz. You should have all of these installed:

[http://i.imgur.com/mJclO.png](http://i.imgur.com/mJclO.png)

If they are all already there, then if I were you I would try uninstalling them and reinstalling.

.

---

### Post by t4nv1r on 2010-02-17
Well it seems i have compiz,compiz-core,compiz-plugins,compiz-wrapper & compiz-gnome installed but all of them are upgradeable...so im goin to upgrade those and install the other ones and see what happens

---

### Post by t4nv1r on 2010-02-17
Okay  I installed & upgraded all those but the problem doesnt go away. If i deactivate and then reactivate my nvidia restricted driver it works . But if i restart  it then the problem comes back.


how do i COMPLETELY uninstall my nvidia display driver ? help plz

---

### Post by Sealbhach on 2010-02-17
> **t4nv1r said:**
> Okay  I installed & upgraded all those but the problem doesnt go away. If i deactivate and then reactivate my nvidia restricted driver it works . But if i restart  it then the problem comes back.


how do i COMPLETELY uninstall my nvidia display driver ? help plz

Again, you can do that from Synaptic, it would be called nvidia-glx....

But I don't think this would accomplish anything, it's to do with your window manager, not your graphics driver.

.

---

### Post by achase79 on 2010-02-17
I have had that problem with my Gforce 2 MX.  I have not found any information on how to fix this.  I believe that it is a driver issue and that driver version isn't maintained anymore.

---

### Post by t4nv1r on 2010-02-18
guess i'll have to use ubuntu with no visual effects then:cry:

thnx for your help guys.

---

### Post by gokulvarma on 2010-07-31
> **t4nv1r said:**
> guess i'll have to use ubuntu with no visual effects then:cry:

thnx for your help guys.

Try this.

Install Ubuntu-tweak by **sudo apt-get install ubuntu-tweak**

Go to[COLOR=DeepSkyBlue] [COLOR=Black]**Applications--> system tools-->Ubuntu tweak**[/COLOR] [/COLOR]look for** windows manager settings tab** and check **use metacity theme**


more how to's @  [http://www.aroundtheweb.info]("http://www.aroundtheweb.info/")

---

