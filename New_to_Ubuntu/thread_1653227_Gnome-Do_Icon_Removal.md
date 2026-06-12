---
title: "Gnome-Do Icon Removal"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by Apv507 on 2010-12-26
Hi all,

I installed Play-On-Linux w/ Wine of course and a few old games (Starcraft and AOE2). I didn't really like they way they ran and Virtualbox makes it so easy I just abandoned any hope of using Wine. However when I type in starcraft the icon is still present in the Gnome-DO menu. It really is not a big deal, but part of the appeal of Ubuntu is not having extra stuff I don't need. I am sure the icon files take up almost no space, but its the principle of the thing. Any help?

Wine is lazy and leaves some files behind when you remove it. I found them and deleted them and that took care of it. 

Here is where I found what I needed: 
[http://ubuntuforums.org/archive/index.php/t-1004337.html](http://ubuntuforums.org/archive/index.php/t-1004337.html)

And to save you some trouble reading that here are the locations that site told me to look:

/home/yourhome/.local/share/applications
 /home/yourhome/.config/menus/applications-merged/

---

