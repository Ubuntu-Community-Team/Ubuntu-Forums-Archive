---
title: "[SOLVED] Installation partially failed, missing lots of packages"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-01-07
I installed Intrepid from the alternate CD, so I could setup software RAID. However, the process went a little haywire, and I got stuck with a system that is missing most of its applications. I was dumped at the terminal. Fortunately, I know my way around pretty well, and I was able to at least get the basic Gnome desktop running with ```
sudo apt-get install gnome-desktop-environment
``` However, it's still missing a lot of packages and the theme looks awful. 

Is there a meta-package that can install all the default packages or some other way to get me to a vanilla install?

I would just reinstall, but setting up RAID was a huge pain.

---

### Post by taurus on 2009-01-07
Maybe the 

```
sudo apt-get install ubuntu-desktop
```

---

### Post by jbrown96 on 2009-01-08
Awesome, worked perfectly.

---

