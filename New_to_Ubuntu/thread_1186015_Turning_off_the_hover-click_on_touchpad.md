---
title: "Turning off the hover-click on touchpad"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by john wagner on 2009-06-12
Hello folks!  Me again!  I just did a new install of Jaunty (from Dapper, heh) and got several questions.

I'm running a 160 gig HD, 2 gig ram, HP Pavillion Laptop computer.
What I would like to do is to turn off the hover-click function of my touchpad.  I hate that.  If I want to open something I will click on it.  I hate the random files etc opening cuz I left the cursor on a file for half a second too long.  Sucks.

I had it off on my Dapper, but I don't remember how/what I did.  
Any and all help is appreciated!

john

---

### Post by keplerspeed on 2009-06-12
Try going to system>preferences>mouse, these should be a section for touchpad there.

---

### Post by john wagner on 2009-06-12
> **keplerspeed said:**
> Try going to system>preferences>mouse, these should be a section for touchpad there.

Thanks, did that first off.  Doesn't kill the hover-click of the touch pad.  Thanks tho.  For Dapper, I remember I had to do it via Terminal, just can't find the posting/answer or my notes on it....

john

---

### Post by keplerspeed on 2009-06-12
We can edit your xorg.conf file to disable to disable touchpad clicking. So:
```

sudo gedit /etc/X11/xorg.conf

```
Then find the section for your touchpad, and add this line:
```

Option "TapButton1" "0"

```

The "0" option is false, turning the TapButton1 off. Reboot for this to take effect. And remember to backup your xorg.conf!!!

---

### Post by keplerspeed on 2009-06-12
However, see the image here:

[http://mexpolk.wordpress.com/2008/07/21/ubuntu-disable-that-annoying-touchpad-click/](http://mexpolk.wordpress.com/2008/07/21/ubuntu-disable-that-annoying-touchpad-click/)

There is an option to disable mouse clicks. So your saying that option doesnt work? Doesnt take effect?

---

### Post by john wagner on 2009-06-12
> **keplerspeed said:**
> We can edit your xorg.conf file to disable to disable touchpad clicking. So:
```

sudo gedit /etc/X11/xorg.conf

```
Then find the section for your touchpad, and add this line:
```

Option "TapButton1" "0"

```

The "0" option is false, turning the TapButton1 off. Reboot for this to take effect. And remember to backup your xorg.conf!!!




Doing this just disables the hover function?  Keeps all the rest of the 
functions of the touchpad?

john

---

### Post by john wagner on 2009-06-12
> **keplerspeed said:**
> However, see the image here:

[http://mexpolk.wordpress.com/2008/07/21/ubuntu-disable-that-annoying-touchpad-click/](http://mexpolk.wordpress.com/2008/07/21/ubuntu-disable-that-annoying-touchpad-click/)

There is an option to disable mouse clicks. So your saying that option doesnt work? Doesnt take effect?



Okay, point your fingers at me and mock loudly.  On three, all together please. 

For some unknown reason (um, stupidity maybe?) I thought "disable mouse clicks" would disable the functionality of the entire pad.  
Mouse touch-pad click = hover-annoying-%$^#@^*!!-auto-self-selector-piece-of-crap!

Okay!  Got it!

Yes, it worked.  Quite well, and quite easily.  I shoulda jumped from Dapper to Jaunty a while ago!

Much easier wireless set up, easier everything so far!

Thank you keplerspeed for your rapid, effective help!

john

---

### Post by keplerspeed on 2009-06-13
Cheers. And there will be no fingers pointing. Some of the stuff ive done...

---

