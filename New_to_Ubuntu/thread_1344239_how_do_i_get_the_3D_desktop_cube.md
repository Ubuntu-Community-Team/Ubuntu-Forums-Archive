---
title: "how do i get the 3D desktop cube?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by blake7 on 2009-12-02
Thanks

---

### Post by NinjaNumberNine on 2009-12-02
You're welcome ;)

 Go to General Options -> Desktop Size. If you want your standard 4 sided cube these should be your settings
Horizontal Virtual Size -> 4
Vertical Virtual Size -> 1
Number of Desktops -> 1

To rotate your cube you just do CTRL + ALT and use your mouse to move it around. You can also layout the cube by pressing CTRL + ALT + DOWN and if you have Expo enabled you can view them all at once with Super (normally Windows Key) + E

Oh and make sure Desktop Cube and Rotate Cube are enabled.

---

### Post by Ylon on 2009-12-02
Terminal:
[b]sudo apt-get install compizconfig-settings-manager
ccsm[/b]



PS: fusion-icon can come handy if you need quick way to enable/disable compiz effect at all.

---

### Post by Johnny19734 on 2009-12-02
Just go to the new UBUNTU store and install Compiz You will see the new Icon in the setting menu :

[IMG]http://www.fsckin.com/wp-content/uploads/2007/10/compiz_settings_menu_location.jpg[/IMG]

---

### Post by Hribar74 on 2009-12-03
Hi,
I tried to install on that on the command line and I got the following message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

Now it says that compiz is installed on this computer, so what is missing?

Thanks!

---

### Post by plucky on 2009-12-03
> **Hribar74 said:**
> Hi,
I tried to install on that on the command line and I got the following message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

Now it says that compiz is installed on this computer, so what is missing?

Thanks!

Do have the **universe** repository enabled?

**System > Administration > Software Sources** and make sure the 4 repositories on the first page are ticked.Then ```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```


Good Luck

---

### Post by Hribar74 on 2009-12-03
Thanks!  it appears there were some files that needed to be downloaded when I exited the software sources app.  Now everything works. :D

---

### Post by Miroslav011 on 2009-12-04
> **NinjaNumberNine said:**
> You're welcome ;)

 Go to General Options -> Desktop Size. If you want your standard 4 sided cube these should be your settings
Horizontal Virtual Size -> 4
Vertical Virtual Size -> 1
Number of Desktops -> 1

To rotate your cube you just do CTRL + ALT and use your mouse to move it around. You can also layout the cube by pressing CTRL + ALT + DOWN and if you have Expo enabled you can view them all at once with Super (normally Windows Key) + E

Oh and make sure Desktop Cube and Rotate Cube are enabled.

  Installed Compiz and followed your instructions.  No cube :S  Anything else that I might be missing out on?

---

### Post by plucky on 2009-12-04
> Installed Compiz and followed your instructions. No cube :S Anything else that I might be missing out on? 


Go to **System > Preferences > Appearance > Visual Effects** and select **Custom** to enable Desktop Effects.Does you video card support 3D effects?

Good Luck

---

### Post by murderslastcrow on 2009-12-04
I think the easiest way to do it is to install Simple Compiz Config Manager, which automatically gets you CCSM in the process and is in the Software Center. Then just go to the dialog in System/Preferences and you have a simple dialog for the most popular functions without having to muss around a ton.

---

### Post by spiderbatdad on 2009-12-04
There is a bit of a learning curve for getting compiz to look pretty. Once you have compizconfig-settings-manager installed, Open it via System>>Preferences>>Compiz... You'll have to enable the cube and rotate cube features by checking the appropriate boxes...then clicking on the rotate cube for example, you'll want to configure different aspects. For example a thing called Bindings>>Rotate Cube, then the down arrow to expand the choices on how you want to initiate cube rotation...cube rotate requires at least a mouse button...not all actions require a mouse button, some can be initiated just by moving to a screen corner with the cursor: expo for example. For cube rotate you may want to set a zoom...so the cube zooms out a little on rotate. There is an almost endless amount of tinkering that can be done in compiz.Have fun.

---

### Post by raymondh on 2009-12-04
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

Have fun.

---

### Post by Miroslav011 on 2009-12-04
> **plucky said:**
> Go to **System > Preferences > Appearance > Visual Effects** and select **Custom** to enable Desktop Effects.Does you video card support 3D effects?

Good Luck

That did it.  Thanks.

> **raymondh said:**
> [http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

Have fun.

Thanks for the help.  This should come in handy :)

---

### Post by raymondh on 2009-12-04
> **Miroslav011 said:**
> 
Thanks for the help.  This should come in handy :)

Happy ubuntu-ing.

---

