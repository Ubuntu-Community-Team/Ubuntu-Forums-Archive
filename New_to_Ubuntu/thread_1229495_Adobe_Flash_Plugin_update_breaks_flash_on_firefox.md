---
title: "Adobe Flash Plugin update breaks flash on firefox"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-08-02
The package "adobe-flashplugin" just updated today (to ver. 10.0.32.18-1) and now flash is no longer working in firefox (specifically youtube).

Any suggestions?

---

### Post by mike555 on 2009-08-02
Yup, I had the same problem ...... go to package manager and completely uninstall flash , then download flash from their site (not package manager),close Firefox then install flash ..... if that works just remember not to update flash in package manager ...

---

### Post by abhiroopb on 2009-08-04
when you say "completely uninstal flash", what packages should I uninstall? I uninstalled the updated adobe-flashplugin and installed the flash that is found on the adobe website. Now I get a process called "gtk-gnash" taking up 100% of my cpu cycles!

---

### Post by Ubun2 Us3r on 2009-08-05
gnash is an open-source flash player that has many errors. Go to your plugins and see if you have GNASH installed. If so get rid of it and that may fix your problem

---

### Post by mikodo on 2009-08-05
> **Ubun2 Us3r said:**
> gnash is an open-source flash player that has many errors. Go to your plugins and see if you have GNASH installed. If so get rid of it and that may fix your problem

Break:  Thanks for the tip. I had tried Gnash on You Tube to no avail, and am still reluctant to play with Adobe Flash Player (for a number of reasons), but will probably sometime regress to using it in the future. I've un-installed it, in preparation of Adobe Flash.

---

### Post by abhiroopb on 2009-08-05
Your suggestion worked...THANKS!

---

### Post by Soul-Sing on 2009-08-05
> **Ubun2 Us3r said:**
> gnash is an open-source flash player that has many errors. Go to your plugins and see if you have GNASH installed. If so get rid of it and that may fix your problem

Correct, gnash is open-source, but i am using gnash in jaunty with no problems at all. (youtube is playing fine)
Gnash as a project is very much under construction and active, older versions had several issue's, but the gnashproject is going strong. (and need some support also......)

---

### Post by mikodo on 2009-08-05
> **leoquant said:**
> Correct, gnash is open-source, but i am using gnash in jaunty with no problems at all. (youtube is playing fine)
Gnash as a project is very much under construction and active, older versions had several issue's, but the gnashproject is going strong. (and need some support also......)

HEY GREAT!!!!!

When I upgrade from Hardy, I can have an trustworthy Open Source Flash Player!!!

---

