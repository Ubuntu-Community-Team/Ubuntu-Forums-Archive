---
title: "gconftool/editor for Unity ?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by yc2 on 2011-04-30
Hello,

As I understand, Gnome will be replaced by a new desktop environment called Unity in v. 11.04.

In Gnome you could control the behavior of the desktop using the following programs:
gconf-editor (graphical)
gconftool (non graphical)

Using Unity, what are the corresponding programs? How do I control the desktop environment in Unity?

Thanks

---

### Post by cobolt01 on 2011-04-30
As far as I understand it, Unity is a plugin for compiz so you can change some settings buy installing ccsm and finding the Unity plugin settings on there.

Let me know if you need more detail.

---

### Post by yc2 on 2011-04-30
OK, thanks, that gave me a start where to look.

I have sometimes used the gconftool over SSH to help beginners.
Is there any similar tool for Unity?
I have only used ccsm for "clicking the settings of my compiz-fusion". Is there any way to use ccsm over SSH or is there another tool for this?

Thanks

---

### Post by Quackers on 2011-04-30
You should also be able to press ctrl + F2 and then type in gconf and it will appear

---

### Post by wojox on 2011-04-30
```
sudo apt-get update; sudo apt-get install dconf-tools
```

Then to use it call **dconf-editor**

---

### Post by mcduck on 2011-05-01
Also Unity still runs on top of Gnome, so gconf-editor and gconftool work just like before, changing the settings of any applications that use gconf.


(Unity isn't a desktop environment. It's a shell running on top of Gnome 2. So Ubuntu 11.04 is still using Gnome just like before.)

---

### Post by yc2 on 2011-05-01
Thanks everyone, I wasn't aware of dconf, for example

Much here for me to learn, thanks:
> **mcduck said:**
> 
Unity isn't a desktop environment. It's a shell running on top of Gnome 2. So Ubuntu 11.04 is still using Gnome just like before.

---

### Post by hakermania on 2011-05-01
> **mcduck said:**
> Also Unity still runs on top of Gnome, so gconf-editor and gconftool work just like before, changing the settings of any applications that use gconf.


(Unity isn't a desktop environment. It's a shell running on top of Gnome 2. So Ubuntu 11.04 is still using Gnome just like before.)

Yeah, but in 11.10 gnome won't be there :/
Do you know where can I download a 'sample' iso of 11.10 so as to test my application (which is working with gcontool2) ?
Thx

---

### Post by mcduck on 2011-05-01
> **hakermania said:**
> Yeah, but in 11.10 gnome won't be there :/
Do you know where can I download a 'sample' iso of 11.10 so as to test my application (which is working with gcontool2) ?
Thx

Yes, it will. Only that's going to be Gnome 3, not the old Gnome 2 since it's not developed any more. :)

---

### Post by hakermania on 2011-05-01
> **mcduck said:**
> Yes, it will. Only that's going to be Gnome 3, not the old Gnome 2 since it's not developed any more. :)

Nice, so i'll maybe just change to gconftool3 xD

---

