---
title: "Cursor is a black X, and window controls are gone"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by djm227 on 2011-03-09
Hey everybody.

I just bought a dell mini 10 off my buddy for 50 bucks, which I think was a pretty good deal.  I immediately installed Ubuntu 10.10 on it.  Besides Unity not working (I don't think it's compatible with my netbook :( ), everything has been working pretty well.

However, I booted her up today and had a black X as the cursor.  In addition to that, all the Minimize, maximize, and close buttons are gone from the windows.  

I thought it may be because I switched the window controls to the right side, but I changed it back today with no avail.  Any ideas?

Thanks!

---

### Post by wep940 on 2011-03-09
> **djm227 said:**
> Hey everybody.
 
I just bought a dell mini 10 off my buddy for 50 bucks, which I think was a pretty good deal. I immediately installed Ubuntu 10.10 on it. Besides Unity not working (I don't think it's compatible with my netbook :( ), everything has been working pretty well.
 
However, I booted her up today and had a black X as the cursor. In addition to that, all the Minimize, maximize, and close buttons are gone from the windows. 
 
I thought it may be because I switched the window controls to the right side, but I changed it back today with no avail. Any ideas?
 
Thanks!
 
It sounds like you need a video driver.  When you get to the black X cursor, try CTRL/ALT and press F1 and see if you can open a terminal window.  If so, do the following and post back the output:
 
lspci | grep VGA

---

### Post by djm227 on 2011-03-09
Here's the output:

```

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

```

While doing that I also noticed a couple of other problems:

-The window switchers are blank, when scrolled over they are outlined, but show nothing.
-Show desktop button pops up an error message "Your window manager does not support the show desktop button, or you are not running a window manager"

Could this have something to do with me installing compiz, but then removing it because it was too much for my computer?  Maybe I removed something important in the process...

---

### Post by wep940 on 2011-03-10
> **djm227 said:**
> Here's the output:
 
```

00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

```
 
While doing that I also noticed a couple of other problems:
 
-The window switchers are blank, when scrolled over they are outlined, but show nothing.
-Show desktop button pops up an error message "Your window manager does not support the show desktop button, or you are not running a window manager"
 
Could this have something to do with me installing compiz, but then removing it because it was too much for my computer? Maybe I removed something important in the process...
 
I really don't know, but if  you did delete somethings dealing with compiz it is quite possible you delete more than or at least something you shouldn't have.  It's really hard for me at this point to know what.
 
Are you at a point where re-installing Ubuntu is an option?

---

### Post by djm227 on 2011-03-10
Turns out all I had to do was reinstall compiz.  It's good too, because getting Ubuntu into this crappy little netbook was a bitch...I did not want to try a reinstall.

---

### Post by wep940 on 2011-03-10
Glad you got that working!  Good job!

---

### Post by Green_Grenade on 2011-03-10
Im having the same problem but with my Acer.. How did you reinstall compiz?! maybe thats what my problem is...

---

### Post by djm227 on 2011-03-10
> **Green_Grenade said:**
> Im having the same problem but with my Acer.. How did you reinstall compiz?! maybe thats what my problem is...

Search for "Compiz" in the software center, and it's first on the list. If there is no green check mark next to it, you need to install it.

---

