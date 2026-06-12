---
title: "Browsers not allow going back to previous screen.."
date: 2010-05-14
forum: New to Ubuntu
---

### Post by ve1drg on 2010-05-14
I am running whatever the browser that comes with ubuntu?  Just forget the name.  Maybe firefox or something.
 
My question relates to being able to go back to a previous screen like you do in Windows, where you simply click the back arrow....
 
Can this be done in Ubuntu?  The only way I am able to do it is to make sure that additional windows that are opened in the existing window  happen in a NEW window. That way I am able to kill that new window and am right back in the start/original window.

---

### Post by cascade9 on 2010-05-14
Its firefox, and yes, it has 'back' buttons (and forward as well). 

BTW, you dont need to open a new window- firefox supports tabs, you can just open a new tab. Much easier to keep track of than new windows....

---

### Post by philinux on 2010-05-14
> **ve1drg said:**
> I am running whatever the browser that comes with ubuntu?  Just forget the name.  Maybe firefox or something.
 
My question relates to being able to go back to a previous screen like you do in Windows, where you simply click the back arrow....
 
Can this be done in Ubuntu?  The only way I am able to do it is to make sure that additional windows that are opened in the existing window  happen in a NEW window. That way I am able to kill that new window and am right back in the start/original window.

In the address bar type ```
about:config
``` 

In the filter type backspace. Double click the entry and change the value to 0, zero. I think it's set to -1 by default.

---

### Post by lovinglinux on 2010-05-14
EDITED: I should stop replying posts when I'm sleepy.

---

### Post by ve1drg on 2010-05-14
> **philinux said:**
> In the address bar type ```
about:config
```In the filter type backspace. Double click the entry and change the value to 0, zero. I think it's set to -1 by default.

Thanks guys for this wonderful tip.  It works!!  Now I wonder why the default setting was 2 and what did that do for us??   Certainly not allow for backspacing..

---

### Post by lovinglinux on 2010-05-14
> **ve1drg said:**
> Thanks guys for this wonderful tip.  It works!!  Now I wonder why the default setting was 2 and what did that do for us??   Certainly not allow for backspacing..

EDITED: I should stop replying posts when I'm sleepy.

---

