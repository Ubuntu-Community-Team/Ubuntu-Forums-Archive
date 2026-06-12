---
title: "Laptop - need to disable touchpad"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Winterdream on 2010-11-29
I bought a Laptop (HP G72-B60US) with Ubuntu 10.10 installed.  This laptop has a touchpad and I'm having a terrible problem with accidentally moving my cursor/caret with it when I pause typing, and then when I start typing again I'm in a different place and I can't see where I am !

I need to disable the touchpad.  Does anyone know how I can accomplish this?  A keyboard shortcut would be acceptable; I've tried to do that but so far I have failed.

Help ?!

---

### Post by mstearns on 2010-11-29
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
There is a section about temporarily disabling it there.

---

### Post by Winterdream on 2010-11-29
> **mstearns said:**
> [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
There is a section about temporarily disabling it there.

Thank you !!!!!!

I needed the section about installing SHMConfig and gsynaptics.  Once I did that, I now have a new graphical interface:
System -> Preferences -> Pointing devices
And there is a tab for the touchpad and a checkbox to disable it !!
And it works !!:D

---

### Post by c00lwaterz on 2010-11-29
> **Winterdream said:**
> Thank you !!!!!!

I needed the section about installing SHMConfig and gsynaptics.  Once I did that, I now have a new graphical interface:
System -> Preferences -> Pointing devices
And there is a tab for the touchpad and a checkbox to disable it !!
And it works !!:D

you can use terminal by typing 

```
sudo modprobe -r psmouse
```

then type your password.

to enable again the touchpad use again the terminal

```
sudo modprobe psmouse
```

then type your password

hope this help

---

### Post by craftyguise on 2010-11-30
I am a brand newbie using Ubuntu and I'm having a heck of a time trying to get some sort of control over this touchpad!

I installed an application to give me GUI control, but it won't work without shmconfig turned on.  I've tried to do so via the instructions given on the linked page above.  When I edit xorg.conf as written, then reboot, I still get the message:
[FONT=monospace]
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

[/FONT]So, I tried setting to true as stated in the error message and I when trying to save xorg.conf I get:

[FONT=monospace]Could not find the file home/jsg/etc/X11/xorg.conf[/FONT]

So, what's next?  Any ideas?  I'm running 10.04 Lucid Lynx on a brand-spanking new ASUS laptop.  I'm a partial geek but more of a super user who is trying to become geekier so really, talk to me like I'm a 2 yr old, please.  ;)

---

### Post by c00lwaterz on 2010-11-30
> **craftyguise said:**
> I am a brand newbie using Ubuntu and I'm having a heck of a time trying to get some sort of control over this touchpad!

I installed an application to give me GUI control, but it won't work without shmconfig turned on.  I've tried to do so via the instructions given on the linked page above.  When I edit xorg.conf as written, then reboot, I still get the message:
[FONT=monospace]
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

[/FONT]So, I tried setting to true as stated in the error message and I when trying to save xorg.conf I get:

[FONT=monospace]Could not find the file home/jsg/etc/X11/xorg.conf[/FONT]

So, what's next?  Any ideas?  I'm running 10.04 Lucid Lynx on a brand-spanking new ASUS laptop.  I'm a partial geek but more of a super user who is trying to become geekier so really, talk to me like I'm a 2 yr old, please.  ;)

as stated above try this

to disable touchpad, you can use terminal by typing

```

sudo modprobe -r psmouse
```

then type your password.

to enable again the touchpad use again the terminal



```
sudo modprobe psmouse
```

then type your password

hope this help

---

### Post by craftyguise on 2010-11-30
Yes, that works to disable the touchpad, but I was really trying to make the disable when typing function working so that I can still use the touchpad when not typing without having to use terminal each time.

Any ideas why I can't seem to enable shmconfig?

Thanks!

---

