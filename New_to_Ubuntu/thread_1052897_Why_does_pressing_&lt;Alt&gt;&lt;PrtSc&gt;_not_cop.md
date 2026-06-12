---
title: "Why does pressing &lt;Alt&gt;&lt;PrtSc&gt; not copy the window title?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by rod40cool on 2009-01-28
Pressing PrtSc grabs the whole screen ok but when I want to just grab the active window Alt-PrtSc seems to copy the active window but ignores the window title bar.

By the way I have Compiz running using the Window decorator command ```
/usr/bin/compiz-decorator
```

Does anyone know why this happens or if there is something I can check?

Thanks,
Rod

---

### Post by amauk on 2009-01-28
for the window borders
Applications > Take Screenshot

check "Include the window border"

---

### Post by marshall.robert on 2009-01-28
Im guessing its Compiz handling the screen shot operation and it hasnt been made to capture the window decorations.

it gets the title bars when you dont have compix enabled.

---

### Post by rod40cool on 2009-01-28
> **amauk said:**
> for the window borders
Applications > Take Screenshot

check "Include the window border"

I tried that but it's still missing the title bar. Any screenshot I try using that method is still missing the border. 

Could Compiz be causing it?

---

### Post by rod40cool on 2009-01-28
> **marshall.robert said:**
> Im guessing its Compiz handling the screen shot operation and it hasnt been made to capture the window decorations.

it gets the title bars when you dont have compix enabled.

Thank you, Yes you are correct. I just disabled compiz and Alt-PrtSc grabs the borders now.

Ok that's a reasonable workaround. I wouldn't mind knowing if it can be done with Compiz enabled though. Does anyone know if it can be done?

----------------------
Ok it looks like I found a [bug #74008]("https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/74008") and the fix is going to be in the the next release.

---

### Post by GhentK on 2009-03-26
First of all, thanks for the information, marshall.robert; you saved my guide. :-)

Second, I'm not aware of such a fix, but I haven't looked around. What I'm trying to say, is that personally, I'm not going to find a fix -- at least not for Intrepid. ;-) If it hasn't been fixed in Jaunty, though, it should definitely be bug-reported.

---

### Post by SamNSane on 2009-03-26
I use kind of a dumb workaround in HH. I use compiz fusion to switch the window manager from compiz to metacity, get the Alt-PrtScr shot, then revert to the compiz window manager.

---

### Post by MrWES on 2009-03-26
> **GhentK said:**
> First of all, thanks for the information, marshall.robert; you saved my guide. :-)

Second, I'm not aware of such a fix, but I haven't looked around. What I'm trying to say, is that personally, I'm not going to find a fix -- at least not for Intrepid. ;-) If it hasn't been fixed in Jaunty, though, it should definitely be bug-reported.

You might want to look into the fusion-icon, which sits in your notification area. Makes it quick and easy to turn compiz on and off.

[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/]("http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/")

Bill

---

