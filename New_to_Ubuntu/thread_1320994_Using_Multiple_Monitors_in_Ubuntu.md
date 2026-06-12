---
title: "Using Multiple Monitors in Ubuntu"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by JimmyJoeBob on 2009-11-09
I just installed Ubuntu (64 bit, version 9.10), and everything is looking good except for one thing.  I have a dual monitor set up, and I can't get Ubuntu to use both monitors.  I went into the nVidia X Server settings and tried to get it to do DualView, but it is unable to write to /etc/X11/xorg.conf.  I get an error saying "Failed to parse existing X config file 'etc/X11/xorg.conf'!"

I have looked around some, and it seems that several people have been having this problem.  However, none of the suggested solutions I have seen work.  I have tried deleting the existing xorg.conf and created a new, blank one.  This didn't work.

Any ideas?  My system specs are in my sig.

---

### Post by bodhi.zazen on 2009-11-09
> **JimmyJoeBob said:**
> I just installed Ubuntu (64 bit, version 9.10), and everything is looking good except for one thing.  I have a dual monitor set up, and I can't get Ubuntu to use both monitors.  I went into the nVidia X Server settings and tried to get it to do DualView, but it is unable to write to /etc/X11/xorg.conf.  I get an error saying "Failed to parse existing X config file 'etc/X11/xorg.conf'!"

I have looked around some, and it seems that several people have been having this problem.  However, none of the suggested solutions I have seen work.  I have tried deleting the existing xorg.conf and created a new, blank one.  This didn't work.

Any ideas?  My system specs are in my sig.

On that screen I believe there is an option to merge with the existing xorg.conf ?

unslect that option.

Also you need to be running nvidia-settings as root :

```
gksu nvidia-settings
```

---

### Post by wojox on 2009-11-09
May also need this

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

Then:
gksudo nvida-settings

Then go to X server display configuration adjust to the desired resolution>apply>svae to xconfig

Now write this on the save X box:
/etc/X11/xorg.conf

---

### Post by JimmyJoeBob on 2009-11-09
Great, that worked.  Thanks for the help.

I have another question though.  I was hoping to get the two displays to behave like Windows XP: windows can be dragged between them, but maximizing a window one maximizes it on one of the screens.  Any way to do that?

---

### Post by bodhi.zazen on 2009-11-09
> **JimmyJoeBob said:**
> Great, that worked.  Thanks for the help.

I have another question though.  I was hoping to get the two displays to behave like Windows XP: windows can be dragged between them, but maximizing a window one maximizes it on one of the screens.  Any way to do that?

This is the way it behaves for me. I find some window managers are better or more mulit monitor aware then others.

IMO XFCE is "best", KDE is #2 , gnome has a ways to go yet.

So try Xubuntu or Kubuntu, see if you have better luck.

And if you have a chance, post which of the two solutions helped you, as these are forms, and specifying the solution that helped you will help others as well.

---

### Post by JimmyJoeBob on 2009-11-12
I managed to solve this, sorry I didn't post it quicker.

I used wojox's solution above, and then set the nVidia control to "TwinView"  after restart, everything worked just fine.  Thanks for the help!

---

### Post by pablolie on 2009-11-24
> **wojox said:**
> May also need this

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

Then:
gksudo nvida-settings

Then go to X server display configuration adjust to the desired resolution>apply>svae to xconfig

Now write this on the save X box:
/etc/X11/xorg.conf

Thanks everybody - between the few tips in this thread I was able to solve this issue for an Nvidia card with 2 monitors, each running their own X-screen.

Just as a piece of advice - do *NOT* delete panels on one of your monitors with such a configuration. Trust me.

---

