---
title: "Touchpad Click"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by DeVoges on 2011-03-13
Hiya, wasn't sure where to post this question. So, I'll try here.

I just installed Xubuntu (I've had and tried a few other distros of Linux) and almost everyone has a default mouse control that when I touch the touchpad area (I have a laptop) it does a left click. I personally hate the feature, so I always have disabled it. However, in the Xubuntu settings- I don't see an option to change this setting.

So; how can I disable the touchpad click for my mouse in Xubuntu?

---

### Post by ajgreeny on 2011-03-13
The package **xserver-xorg-input-synaptics** contains synclient which will be able to do that for you with the command ```
synclient MaxTapTime=0
```  You can make a shell script and launch it at startup to do it automatically at session start.

I agree with you the "tap for click" is a real pain in the XXXX, and I had to search for a while to find this info when I tried lubuntu on an old laptop and kept executing things when I didn't mean to.  I think it works on all distros.

---

### Post by DeVoges on 2011-03-13
> **ajgreeny said:**
> The package **xserver-xorg-input-synaptics** contains synclient which will be able to do that for you with the command ```
synclient MaxTapTime=0
```  You can make a shell script and launch it at startup to do it automatically at session start.

I agree with you the "tap for click" is a real pain in the XXXX, and I had to search for a while to find this info when I tried lubuntu on an old laptop and kept executing things when I didn't mean to.  I think it works on all distros.

Worked like a charm.

---

### Post by neu5eeCh on 2011-08-03
> **ajgreeny said:**
>  You can make a shell script and launch it at startup to do it automatically at session start.

I agree with you the "tap for click" is a real pain in the XXXX, and I had to search for a while to find this info when I tried lubuntu on an old laptop and kept executing things when I didn't mean to.  I think it works on all distros.

Searching for info on this subject. I can make a shell script, but what directory do I put it in so that it's executed at startup?

---

