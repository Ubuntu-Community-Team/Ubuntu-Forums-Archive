---
title: "AWN won't show after dual screen display"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2009-03-08
So I figured I'd see what dual screen display would look like with my laptop and found that its just not for me. However, the problem that I am having now is that my laptop seems to be running much slower graphics and I can't seem to get AWN started. I am able to go back to my 1200x800 resolution but compiz seems to be off line (just tried to run compiz from terminal and my window borders disappeared and I can't minimize or look at terminal to see what was the output). 

I am running Intrepid on a Lenovo 3000 V100. Thanks in advanced for the help

---

### Post by TadeoDiaz on 2009-03-08
A little more information. I tried to restart compiz using

```
compiz --replace
```

and got this output in the terminal:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

---

### Post by TadeoDiaz on 2009-03-08
Just found the solution ([http://ubuntuforums.org/archive/index.php/t-1033255.html](http://ubuntuforums.org/archive/index.php/t-1033255.html)). Everything went back to normal after running this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Sorry for the extra thread, I guess I freaked out a little

---

### Post by TadeoDiaz on 2009-03-08
I would mark it as solved but the option is not under Thread Tools, sorry

---

