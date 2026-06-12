---
title: "startx command hangs system"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by sylvainrb on 2010-06-26
Hello,

Since last night I am unable to access my X window server after booting and typing the "startx" command. I can login fine and ran the updates to see if it'll fix the issue, but "startx" still freezes the system. I can't even change to another tty... But pressing the power button will show the shutdown output on the terminal

I have a dual-boot W7/10.04 (both 64-bit) and an ATI radeon 4870 (my guess is there's a problem with the GPU)

Has anyone run into the same issue and found a solution? Thanks!!

---

### Post by stmiller on 2010-06-26
Just use gdm?

```
sudo /etc/init.d/gdm start
```

---

### Post by sylvainrb on 2010-06-26
> **stmiller said:**
> Just use gdm?

```
sudo /etc/init.d/gdm start
```

I can't try it 'til I'm home but what would be the difference compared to startx?

---

### Post by corncob on 2010-06-26
I don't know if this has anything to do with it but will [CTR][ALT][F7] do what you want?

---

### Post by nhasian on 2010-06-26
> **stmiller said:**
> Just use gdm?

```
sudo /etc/init.d/gdm start
```

i believe the same can be accomplished now with

```
sudo service gdm start
```

---

### Post by sylvainrb on 2010-06-26
Trying to start using the gdm command gives me the same issue: no X server and system hanging...

---

### Post by llamabr on 2010-06-26
post:
```
cat ~/.xinitrc
```

---

### Post by sylvainrb on 2010-06-27
> **llamabr said:**
> post:
```
cat ~/.xinitrc
```

File doesn't exist...

```
@system-pc cat ~/.xinitrc
cat: /home/ihavenoname/.xinitrc: No such file or directory
```

---

### Post by nhasian on 2010-06-27
yeah i checked as well and the file .xinitrc does not exist for me either though my X and gnome run fine.

---

### Post by sylvainrb on 2010-06-27
So the next thing I want to try is to revert back to the open source driver for my ATI graphic card... But not too sure how to go about it. Anyone knows?

---

