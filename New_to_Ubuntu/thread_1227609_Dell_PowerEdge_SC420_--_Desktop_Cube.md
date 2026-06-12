---
title: "Dell PowerEdge SC420 -- Desktop Cube"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by NuKMaN on 2009-07-30
I am completely new to linux and ubuntu, that being said I am having problems trying to get the Cube Effect to work.  I have Ubuntu 9,04 installed on a PowerEdge SC420.  The options to enable the Cube are simply not there.  Then I started digging around and relized that I can not set the desktop to 3D.  I am wondering if this is due to a wrong video driver installed.  I can seem to find where to look in ubuntu or I may be on the wrong track all together.


Any Help?:confused:

---

### Post by overdrank on 2009-07-30
> **NuKMaN said:**
> I am completely new to linux and ubuntu, that being said I am having problems trying to get the Cube Effect to work.  I have Ubuntu 9,04 installed on a PowerEdge SC420.  The options to enable the Cube are simply not there.  Then I started digging around and relized that I can not set the desktop to 3D.  I am wondering if this is due to a wrong video driver installed.  I can seem to find where to look in ubuntu or I may be on the wrong track all together.


Any Help?:confused:

Hi and welcome, you may use the command ```
lspci | grep VGA
``` in the terminal located under applications, accessories.
This will identify your graphics card. You may also look at the FAQ's link in my signature for help. :)

---

### Post by nhasian on 2009-07-30
your right, by default ubuntu doesnt come with the compiz configuration manager to enable the desktop cube.  even though compiz itself is installed.  you can easily remedy this in a terminal with the command:

```
sudo apt-get install compizconfig-settings-manager
```

now make sure you have set Visual Effects to EXTRA in System->Preferences->appearance preferences

then you should be able to go to System->Preferences->Compiz Config Settings and enable the desktop cube.

---

### Post by NuKMaN on 2009-07-30
Thanks!!!!


It worked!!

---

