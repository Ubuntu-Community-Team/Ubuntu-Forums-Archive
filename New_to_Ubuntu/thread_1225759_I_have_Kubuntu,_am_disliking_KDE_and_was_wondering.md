---
title: "I have Kubuntu, am disliking KDE and was wondering if i could replace it with Gnome"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by FreezWay on 2009-07-28
I just got a new computer... It came with vista, i installed Kubuntu and am regretting not sticking with ubuntu. I like Gnome a lot more. So anyway, is there a way to switch without deleting all my files?

---

### Post by llamabr on 2009-07-28
I've never tried it, but should be as simple as:

```
sudo apt-get install gnome
```

and then choose it at the gdm login prompt.

---

### Post by Bigtime_Scrub on 2009-07-28
You want to run 

```
sudo apt-get install ubuntu-desktop
```

After that log out. Select Gnome under sessions and set it to default. 

Then log back in.

---

### Post by FreezWay on 2009-07-28
cool, how do i get rid of kde (is it something like sudo apt-get remove kde)?

---

### Post by Bigtime_Scrub on 2009-07-28
> **FreezWay said:**
> cool, how do i get rid of kde (is it something like sudo apt-get remove kde)?

You can try ```
sudo apt-get purge kubuntu-desktop
```

Follow it up by ```
sudo apt-get autoremove
```

Now if you want to remove KDE 100% and get a pure Gnome follow this link. 
[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

---

### Post by eriqjaffe on 2009-07-28
You can run

```
sudo apt-get remove kubuntu-desktop
```

...but that might remove things that would be better off sticking around.  It won't harm anything to leave the Kubuntu stuff there, though.

---

### Post by Ji Ruo on 2009-07-28
There is a tutorial on the Pyschocats website for putting the KDE desktop on ubuntu -

[http://psychocats.net/ubuntu/kde]("http://psychocats.net/ubuntu/kde")You should be able to adapt this very easily to do it the other way around. Install ubuntu-desktop (instead of kubuntu-desktop) in synaptic package manager, which you get to from Kmenu>Applications>System>Package Manager (Synaptic Package Manager). You'll be able to follow the rest of the tutorial from there.

The author has another helpful page for removing all of the kde stuff - [http://psychocats.net/ubuntu/puregnome]("http://psychocats.net/ubuntu/puregnome")Press <Alt>+<F2> and type in "terminal". Then copy and paste the long string in the 'remove kubuntu' section (you have to press <Ctrl>+<Shift>+<V> to paste into the terminal). Press enter and all the kubuntu programs will be removed.

Post back if you get stuck.

---

### Post by RomeReactor on 2009-07-28
> **Bigtime_Scrub said:**
> Now if you want to remove KDE 100% and get a pure Gnome follow this link. 
[http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce)

I think the link should be to [Pure Gnome]("http://psychocats.net/ubuntu/puregnome"), as FreezWay wants the Ubuntu desktop, not Xubuntu.

---

### Post by FreezWay on 2009-07-28
wait, found instuctions.... thx anyway!

---

### Post by Bigtime_Scrub on 2009-07-28
> **RomeReactor said:**
> I think the link should be to [Pure Gnome]("http://psychocats.net/ubuntu/puregnome"), as FreezWay wants the Ubuntu desktop, not Xubuntu.

#-o My mistake 	#-o

The  earlier command I'm pretty sure gets rid of KDE.

---

### Post by KermitTensmeyer on 2009-07-28
Apt-get is a nice command line method for managing software packages.

 You might get more mileage from using the Graphic version of the  tool (System -> Administration -> Synaptic Package Manger)  The standard available repositories have many sets of packages to enhance your options.
  It also makes it easier to safely remove packages. (It'will warn you if removing package A will cause problems by also removing Packages D, E, F

---

