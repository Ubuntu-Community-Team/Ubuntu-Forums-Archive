---
title: "BURG classes."
date: 2010-10-20
forum: New to Ubuntu
---

### Post by fslezak on 2010-10-20
Hello.

I installed Puppy Linux on my machine (using FRUGAL). I made a BURG entry for it and I want the icon to show up.

I noticed that the Puppy Icons already exist, and I would like that icon to link to my entry. I also noticed that there already is a class set up in the "/boot/burg/themes/icons/hover" file. That hover file is also set as an include in my Sora theme. I do not know whether the "$$" links to the current folder, or the icons folder where the hover file lives in. 

So what would be proper command to set a class in the below code statement?

Thank You!

```
  -puppy { image = "$$/grey_puppy.png:$$/large_puppy.png" }
```Code from the "hover" file.

---

### Post by M!K3_$ on 2010-10-20
[http://www.puppylinux.org/wikka/ForumsPuppy]("http://www.puppylinux.org/wikka/ForumsPuppy")

you might have better luck on one of those.

---

### Post by funicorn on 2011-05-31
the answer is quite simple, burg chooses os logo in terms of the menuentry content in burg.cfg. To be specific, there is a class declaration in each menuentry with keyword  "--class"

for example , for each Ubuntu menuentry, class of ubuntu is defined with key word "--class ubuntu". Hence burg would display the logo related to class of ubuntu, which is defined in the files $burgdir/themes/small, large and hover. 

If u want puppy logo to be properly displayed, just add the keyword "--class puppy" to head of the puppy menuentry. like this

menuentry 'Puppy' --class puppy --class gnu-linux --class gnu --class os {
}

---

