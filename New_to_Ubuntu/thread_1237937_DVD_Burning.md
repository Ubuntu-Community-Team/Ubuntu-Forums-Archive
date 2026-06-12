---
title: "DVD Burning"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-08-11
I'm using the built-in DVD burner that comes with the OS. I am burning a DVD and to a DVD+R DL. When I add my files, click burn, and then select my options, the Burn button is grayed out, it won't let  me select it!!!

So either 1, I need to fix this problem, or 2. I need a different piece of software (freeware) recommended to me.

Thanks.

---

### Post by x33a on 2009-08-11
give k3b a try.

to install, open a terminal
```
sudo aptitude install k3b
```

---

### Post by kakashi_12 on 2009-08-12
hmmm, this program won't see that i put a dvd in either. it says no media (or medium) present. one or the other.

must be a prob with the way my os isn't seeing the drive. or not seeing it as a burn drive or something. do i have to mount the drive???? it shows in "computer" xwindow.

---

### Post by DarkSaga70 on 2009-08-12
> **x33a said:**
> give k3b a try.

to install, open a terminal
```
sudo aptitude install k3b
```

k3b is the best burn program on Linux.

---

### Post by DarkSaga70 on 2009-08-12
> **kakashi_12 said:**
> hmmm, this program won't see that i put a dvd in either. it says no media (or medium) present. one or the other.

must be a prob with the way my os isn't seeing the drive. or not seeing it as a burn drive or something. do i have to mount the drive???? it shows in "computer" xwindow.

I had that same issue and had to switch from +R dvds to -R it was my burner. It just didn't like the +R. I would try the opposite of what your using and see if that fixes it.

---

