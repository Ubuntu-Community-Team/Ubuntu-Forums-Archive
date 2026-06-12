---
title: "ATI graphics card driver issues"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-03-15
Earlier today i was browsing the forums for ways to fix the lag/slow fps from my ati card. I came across this thread that suggested installing a package that'd let you compare the latest/recommened version of drivers mainly video cards. Also in the same thread there was this guide to how to make your own video driver. Well i tried it and now my video cards messed up so i need to know how to install the old video card driver the propitary one from the command prompt as i can still do the shell prompt from the recovery prompt i'm on the live cd and any help would be greatly appareciated. Also if anyone knows what that program is that'd be great since it's very nice to have in such a issue as this.

---

### Post by zvacet on 2009-03-15
First remove packages you installed with 

```
 dpkg --remove --force-remove-reinstreq package_name
```

and after that install your old driver.

---

### Post by lvleph on 2009-03-15
You can use envyng to install the ati driver.

---

