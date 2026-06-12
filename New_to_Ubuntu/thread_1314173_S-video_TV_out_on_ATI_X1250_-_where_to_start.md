---
title: "S-video TV out on ATI X1250 - where to start?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by AlHounos on 2009-11-04
Just took my first plunge into Linux with Ubuntu 9.10 - I have been amazed at how much works straight away on my Acer laptop.  

However, I really miss having the S-video on my ATI radeon mobility x1250.

I don't know where to begin...  should I try to get it working with the open drivers?  The problem with that is that when I ran a command looking at my video card specs, no S-video output came up, only the VGA.  

So maybe I need to install ATI drivers to recognize the S-video?  But it looks like that might cause a lot of new problems....

---

### Post by silo4321 on 2009-11-14
I was frustrated with the same problem with the same card had to edit xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

add
	> Option "ATOMTvOut" "TRUE"

to the device section and I could get s-video working.

---

### Post by cajunlibra on 2009-12-08
I have the Mobility X300.  Would this work for me as well?

Thanks

---

