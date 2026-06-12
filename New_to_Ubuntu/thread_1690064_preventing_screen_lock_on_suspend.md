---
title: "preventing screen lock on suspend"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by s1wood on 2011-02-17
Is there any way of stopping the screen from locking when I use 'suspend'? No-one uses this computer but me and I get fed up with having to use the password every time I come back to it. (Ubuntu 10.10)

Susan

---

### Post by Stephann on 2011-02-17
You'll go to System->Preferences->Screensaver and uncheck "Lock screen when screensaver is active"

Warm regards.

---

### Post by s1wood on 2011-02-19
I'd already done that - it's suspend that is the problem not screensaver.

I just found another post with this question and the answer given was:

>Look in gconf-editor > Apps > Gnome Power Manager > lock > is "use screensaver setting" box checked?<

I've tried that and several combinations of boxes checked and ended up unchecking every box in Lock - I'm still getting it. What am I doing wrong?

Susan

---

### Post by justinjstark on 2011-07-12
> **s1wood said:**
> I'd already done that - it's suspend that is the problem not screensaver.

I just found another post with this question and the answer given was:

>Look in gconf-editor > Apps > Gnome Power Manager > lock > is "use screensaver setting" box checked?<

I've tried that and several combinations of boxes checked and ended up unchecking every box in Lock - I'm still getting it. What am I doing wrong?

Susan

I have the same issue.  That checkbox doesn't seem to do anything.  :-(

---

### Post by wep940 on 2011-07-12
Did you reboot after checking the option and prior to testing to see if it worked?

---

