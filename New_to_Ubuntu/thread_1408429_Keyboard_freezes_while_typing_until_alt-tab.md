---
title: "Keyboard freezes while typing until alt-tab"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by xsnipersgox on 2010-02-16
I've just started ubuntu recently and i am updated to the latest kernal/version? I've already remove the older kernals but now i realize that while i am typing, occasionally the keyboard will freeze and resulting in me not able to type anything else.

currently i am working around it by alt-tabbing twice, which unfreezes it somehow and allow me to continue typing or i can right click on the screen and that also unfreezes it.  This happens in all kinds of text field but most often while i am editing codes in Quanta.

Any suggestions on what i should do to tackle this problem? perhaps start some sort of log?

Thanks


-xsnipersgox

---

### Post by Lightstar on 2010-02-16
I have a problem that is not the same as yours, but also weird, maybe they are distant cousin and related.

For me, it's the other way around, sometimes after alt-tabbing, I cannot type at all, i have to alt-tab a few times, switch windows with the mouse, and then the keyboard works again.

This keyboard is fine, works perfectly in other OSs, it's not wireless, so there is no battery problems.

I think the problem appeared when I installed additional languages.  (like japanese input with SCIM )

Maybe it's related to SCIM, do you have it installed also?

---

### Post by xsnipersgox on 2010-02-16
hmm, i think you are unto something. Yes i do have SCIM installed, chinese pinyin.  it's probably something to do with the shortcut on it?  I also have times when the internet's auto fill make it seem like it's refusing to type.

---

### Post by Lightstar on 2010-02-17
The internet's autofill would probably be more of a browser or website problem.

I'm disabling all shortcuts except ALT+`  (grave i think?) in SCIM, I'll see if I still get the alt-tab problem.  if I do i'll change the ALT+` shortcut to something else and retry.

Let me know if you figure something out on your side.

---

### Post by xsnipersgox on 2010-02-18
just confirmed and recreated multiple times, the using of the auto fill currently is causing the keyboard to lock on my browser until i do the "fix". i am going to check the other programs.

[update] i killed the scim and was able to stop the freezing, at least with the autofill freeze.


try these fixes, i think it will solve the problem 

[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/293001](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/293001)

[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/163325](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/163325)

---

### Post by syed.rakib.al.hasan on 2011-06-27
could anyone find any solution to this yet??? this is VERY frustrating while coding.... i can't even do Ctrl+Z more than once at a time.... i have to do Ctrl+Z.... Alt+Tab (twice).... Ctrl+Z.... Alt+Tab (twice).... Ctrl+Z.... Alt+Tab (twice).... Ctrl+Z.... Alt+Tab (twice).... Ctrl+Z.... Alt+Tab (twice).... :mad:

additionally, my problem occurs in eclipse but not in gEdit.... and yes i do have SCIM installed... is that a problem?

-------

okay... it got solved RIGHT after i uninstalled scim from my system... but i need to keep scim because all my work is done bangla... and scim is necessary for that.

---

