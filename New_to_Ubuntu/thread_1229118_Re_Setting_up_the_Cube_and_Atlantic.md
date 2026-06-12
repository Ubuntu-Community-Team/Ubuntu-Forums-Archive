---
title: "Re: Setting up the Cube and Atlantic"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by lyfenda on 2009-08-01
can som1 tell me how to get 3d cube and atlantic working on ubuntu linux

---

### Post by themusicalduck on 2009-08-01
First install simple-ccsm by typing this into a terminal ```
sudo apt-get install simple-ccsm
```

Then install atlantis (I guess you mean that by atlantic) with ```
sudo apt-get install compiz-fusion-plugins-unsupported
```

Once they have installed, go to System > Preferences > CompizConfig settings manager. This will bring up a control panel to enable and configure compiz features. You should be able to check Desktop Cube (Rotate Cube might also be useful) and Cube Atlantis from here.

It's worthwhile looking through the Desktop Cube and Rotate Cube settings or of anything else by clicking on the icons to customise them how you like.

```
sudo apt-get install compiz-plugins
``` will also give you a few extra useful addons if it isn't installed already.

---

### Post by misswham on 2009-08-01
Here is a visual tutorial on how to use the cube.

[http://www.youtube.com/watch?v=LGY9cwSjZsU](http://www.youtube.com/watch?v=LGY9cwSjZsU)

---

### Post by misswham on 2009-08-02
I tried the sudo command for unsupported and it says the following.  Why does it say couldnt be found?

aretha@aretha-desktop:~$ sudo apt-get install simple-ccsm
[sudo] password for aretha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
simple-ccsm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aretha@aretha-desktop:~$ sudo apt-get install compiz-fusion-plugins-unsupported
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fusion-plugins-unsupported
aretha@aretha-desktop:~$ sudo apt-get install compiz-plugins
Reading package lists... Done
Building dependency tree        
Reading state information... Done
compiz-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aretha@aretha-desktop:~$

---

### Post by tommah04 on 2009-08-02
you already have both installed, just try looking for it in System

---

### Post by misswham on 2009-08-02
I was actually looking at a tutorial video and with these commands the effect of snow was added to the extras in compiz.  it just never showed up.

---

