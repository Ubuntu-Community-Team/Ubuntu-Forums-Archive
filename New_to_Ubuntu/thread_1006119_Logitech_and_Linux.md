---
title: "Logitech and Linux"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Judy Mac on 2008-12-09
Is there a driver available to enable me to use my new Logitech mini optical mouse on a Linux OS, or do I need to buy a different mouse?

---

### Post by jbrown96 on 2008-12-09
I've used several Logitech wireless mice and have had no problems. Does it not work if you plug it in? Is the mouse wireless? I think hotplugging should work, but could you give some info? I assume it's USB (even if wireless). Right after you plug it in do the following command ```
lsusb
``` and post the output here. See if ```
xev
``` gives you any input. It will create a small window; move the pointer into it and try moving the logitech mouse and using it's buttons. The output is not important; just whether there is any. If there is, then it should just be a matter of finding a configuration guide.

---

### Post by slammed87d21 on 2008-12-09
What model is it?

---

### Post by 3rdalbum on 2008-12-09
Mice are one of those things that work, at least their essential functions, out-of-the-box on any USB-compatible operating system.

If the mouse doesn't move your arrow cursor, then there's something wrong with it and you should return it for a refund.

EDIT: I've even just realised that I have a Logitech mouse too.

---

### Post by jimmy the saint on 2008-12-09
I also use logitech.  The only thing that doesn't seem to work is side scrolling (moving middle buttone side to side).  xev doesn't even detect input, so I doubt there is much hope for that.

---

### Post by Judy Mac on 2008-12-09
> **jbrown96 said:**
> I've used several Logitech wireless mice and have had no problems. hankDoes it not work if you plug it in? Is the mouse wireless? I think hotplugging should work, but could you give some info? I assume it's USB (even if wireless). Right after you plug it in do the following command ```
lsusb
``` and post the output here. See if ```
xev
``` gives you any input. It will create a small window; move the pointer into it and try moving the logitech mouse and using it's buttons. The output is not important; just whether there is any. If there is, then it should just be a matter of finding a configuration guide.

Thank you for your reply! I have discovered that a cordless mouse works MUCH better when you insert the battery correctly!:lolflag: My mouse is now functional!

---

