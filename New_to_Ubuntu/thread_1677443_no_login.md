---
title: "no login"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by ben889 on 2011-01-28
i just installed a video driver and now when the computer boots i have no login i can hit enter type my password and i can hear the system start.
 
 
im using 10.10
 
how do i get it back?

 
video = 7000m
 
thanks ben

---

### Post by fabricator4 on 2011-01-28
Go to a bash terminal and log in (ctrl-alt-F2 for the second terminal)

From another thread elsewhere:

```

sudo rm -f /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

```

The xorg.conf is becoming less relevant as xorg gets more sophisticated (I still need one for sync rates through a monitor switch) but you should be able to reconfigure it anyway with:

```

sudo dpkg-reconfigure xserver-xorg

```

Chris

---

### Post by ben889 on 2011-01-28
ok so how do i get to the bash terminal?


thanks ben

---

### Post by fabricator4 on 2011-01-28
> **ben889 said:**
> ok so how do i get to the bash terminal?


thanks ben

<ctrl>-<alt>-<F2>

[Google hits for switching terminal]("http://www.google.com.au/#hl=en&source=hp&biw=1024&bih=464&q=switching+terminals+in+linux&aq=f&aqi=g1&aql=&oq=&fp=e82ce623fc56ad5b")

---

### Post by ben889 on 2011-01-28
thanks for the quick reply i got the terminal and typed what you told me but nothing happend im sure it me im typing in somthing wrong.
 
 
 
thanks ben

---

### Post by fabricator4 on 2011-01-29
> **ben889 said:**
> thanks for the quick reply i got the terminal and typed what you told me but nothing happend im sure it me im typing in somthing wrong.
 
 
 
thanks ben


While holding down the Alt and ctrl keys, press F2

You don't need to log into the graphical environment for this to work, it just has to boot.  If it doesn't work then maybe the system hasn't booted at all.

---

### Post by ben889 on 2011-01-29
thanks for the reply. i did get to the terminal and typed the code but nothing happened so me being impatient did a reinstall.

but every time i installed the recommended driver i have no gui so what do you recommend for drivers for the nvidia 7000m? not using the lap top screen as it is busted.

thanks ben

---

### Post by fabricator4 on 2011-01-29
> **ben889 said:**
> 
but every time i installed the recommended driver i have no gui so what do you recommend for drivers for the nvidia 7000m? not using the lap top screen as it is busted.

thanks ben

I don't know, I don't run any GeForce cards at all.  At this point you should probably ask a new question, stating the problem in the title and telling what you've tried so far and the results.

Chris

---

