---
title: "No scrolling in touchpad or middle click"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-30
Hey everyone,

I can no longer scroll with the sides of the touchpad any more, after upgrading to 9.10. I can't scroll with the middle mouse button either. In System -> Preferences -> Mouse, there is no option to enable scrolling with the touchpad. What should I do? 

Thanks! :)

---

### Post by ikt on 2009-10-30
system > admin > synaptic package manager

search for: touchpad

is xserver-xorg-input-synaptics installed?

---

### Post by asuastrophysics on 2009-10-30
> **ikt said:**
> system > admin > synaptic package manager

search for: touchpad

is xserver-xorg-input-synaptics installed?

Yup, it's checked in synaptic package manager and I also get the following:
```
jake@girdy-laptop:~$ sudo apt-get install xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jake@girdy-laptop:~$ 

```

Thanks for your reply. :guitar: Is there anything else I can try?

---

### Post by ikt on 2009-10-30
> **asuastrophysics said:**
> Yup, it's checked in synaptic package manager and I also get the following:
```
jake@girdy-laptop:~$ sudo apt-get install xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jake@girdy-laptop:~$ 

```

Thanks for your reply. :guitar: Is there anything else I can try?

Are you able to run the 9.10 release in LiveCD mode?

---

### Post by philinux on 2009-10-30
> **asuastrophysics said:**
> Hey everyone,

I can no longer scroll with the sides of the touchpad any more, after upgrading to 9.10. I can't scroll with the middle mouse button either. In System -> Preferences -> Mouse, there is no option to enable scrolling with the touchpad. What should I do? 

Thanks! :)

You need to enable "tap to click" in the mouse prefs.

---

### Post by asuastrophysics on 2009-10-30
> **philinux said:**
> You need to enable "tap to click" in the mouse prefs.

As weird as it may sound, there is no option in mouse preferences for "tap to click". Additionally, there are no settings for the touchpad at all. I have two tabs: General and Accessibility.  

Weird. As for the livecd suggestion, I'm going to burn a livecd and see how it runs. I'll let you know how it runs after I load it up.

Thanks again for all your help.

---

