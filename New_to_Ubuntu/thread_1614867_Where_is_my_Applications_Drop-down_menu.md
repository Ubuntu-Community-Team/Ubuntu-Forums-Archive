---
title: "Where is my Applications Drop-down menu?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-06
Hi,

My drop down menu for applications has disappeared. Places and System are still there. I have tried searching for this problem but most solutions either don't work or are for earlier versions of Ubuntu. I have 10.10.

One solution recommended that I look at /home/username/.config/panel/applications.menu.

When I view hidden files I only get as far as .config folder. There is no panel folder. Where is it?!

Please help!

Jamie

PS: I am running very low on disk space (I'm just testing Ubuntu - it's to be reinstalled properly at some point). Is this related?

---

### Post by Verbeck on 2010-11-06
> **demonboy said:**
> Hi,
One solution recommended that I look at /home/username/.config/**panel**/applications.menu.
Jamie
its /home/username/.config/**menus/**applications.menu

by default, the contents should look like 
```

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
    <Name>Applications</Name>
    <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

```

---

### Post by demonboy on 2010-11-06
Thanks, Verbek. My applications doc was empty so I copied your code into it and all is sorted.

But how did this happen in the first place? I swear I never touched that file guv!

---

### Post by Verbeck on 2010-11-06
i would guess playing with the menu preferences  ;)

---

### Post by demonboy on 2010-11-06
I understand that computers don't do anything without the operator's intervention, but I swear I did nothing. Last night I logged out of Ubuntu and turned the machine off. I then went in to Windows XP and did some stuff, then turned it off. None of the stuff I did in Windows could have impacted on this menu file, I am certain.

This morning I booted up Ubuntu and that's when my menu disappeared.

Anyway, it's working now so thanks once again.

---

