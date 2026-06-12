---
title: "graphical problem?"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by ubunoobie on 2009-06-10
Hi guys,
It's been a while since I've posted here asking for help...I've been mostly trouble free for the 2 or so years since I discovered Ubuntu. It's been great!

However, I do seem to have a problem now that I would like to get other opinions about. I've recently added a hard drive and upgraded to 9.04 and have been using both for about a week. I think it's safe to say that this is coincidental, because it has been happening when I boot into 7.10 (and even XP). I think this is a video card problem (or perhaps my monitor), but I'm not sure, as I don't know what the grub screen means. What's with the letters and numbers around the bootloader?
[IMG]http://i42.tinypic.com/20p1pwm.jpg[/IMG]
Has anyone ever seen this? Or know what it means?
[IMG]http://i40.tinypic.com/2e37rdf.jpg[/IMG]
One last pic of the grub screen:
[IMG]http://i42.tinypic.com/2055clk.jpg[/IMG]

Here is a pic of what my screen looks like if I do choose to boot into 7.10 (or 9.04...it does the same thing with both):
[IMG]http://i39.tinypic.com/1ampy.jpg[/IMG]

I have an GeForce 8400GS running DVI into a Samsung SyncMaster 22 in. LCD. I've had this setup for a couple of years now (since 7.10, however long ago that was :)) with no problems.

Anyone have any thoughts?

---

### Post by nandemonai on 2009-06-10
Looks like your video card is dying. If it were the monitor, likely it wouldn't display anything. Certainly looks like video card artifacts which usually means either it's overheating or on its way out. Do you get the same sort of distortion on the first screen as you boot up? The Vendor / POST information before the machine boots grub?

You could try checking the video card fan is running and whether it is clogged. Also check the capacitors on the video card, they're usually the first thing to go if not the fan.

Here is what popped capacitors look like:

[http://lh4.ggpht.com/_gD187Hi8fmw/SSe9Ztx2DaI/AAAAAAAAADM/BTjpCLEiLCY/s800/blowncaps.jpg](http://lh4.ggpht.com/_gD187Hi8fmw/SSe9Ztx2DaI/AAAAAAAAADM/BTjpCLEiLCY/s800/blowncaps.jpg)

---

### Post by Sarai the Geek on 2009-06-10
> **nandemonai said:**
> Looks like your video card is dying. If it were the monitor, likely it wouldn't display anything. Certainly looks like video card artifacts which usually means either it's overheating or on its way out. Do you get the same sort of distortion on the first screen as you boot up? The Vendor / POST information before the machine boots grub?

You could try checking the video card fan is running and whether it is clogged. Also check the capacitors on the video card, they're usually the first thing to go if not the fan.
+1 on this EXCEPT I assume that there isn't a problem when you boot into XP, or else you would have mentioned that...?

If so, does it happen when you boot into a live CD?

[EDIT: Agh, never mind, re-read your post and apparently it doesn't work when you boot XP. So, back to dying graphics card-]

---

### Post by ubunoobie on 2009-06-10
> **nandemonai said:**
> Looks like your video card is dying. If it were the monitor, likely it wouldn't display anything. Certainly looks like video card artifacts which usually means either it's overheating or on its way out. Do you get the same sort of distortion on the first screen as you boot up? The Vendor / POST information before the machine boots grub?

You could try checking the video card fan is running and whether it is clogged. Also check the capacitors on the video card, they're usually the first thing to go if not the fan.

Here is what popped capacitors look like:

[http://lh4.ggpht.com/_gD187Hi8fmw/SSe9Ztx2DaI/AAAAAAAAADM/BTjpCLEiLCY/s800/blowncaps.jpg](http://lh4.ggpht.com/_gD187Hi8fmw/SSe9Ztx2DaI/AAAAAAAAADM/BTjpCLEiLCY/s800/blowncaps.jpg)

First, thank you very much. I was also thinking perhaps it could be an overheating problem... so I opened up the case and took a look at the vid card fan, and it's still running. The vendor (ASUS) screen does seem slightly out of focus... I just noticed that, now that you mentioned it. I went ahead and bought a can of air from the store, and have been blowing all sorts of dust out of the case. However, even after hooking it all back up, I was still getting the same problem.

---

### Post by ubunoobie on 2009-06-10
> **Sarai the Geek said:**
> +1 on this EXCEPT I assume that there isn't a problem when you boot into XP, or else you would have mentioned that...?

If so, does it happen when you boot into a live CD?

[EDIT: Agh, never mind, re-read your post and apparently it doesn't work when you boot XP. So, back to dying graphics card-]

Yea, even looking at it myself, I would say dying vid card... I just didn't want to conclude anything too quickly and ask here first. Again, thanks!

---

