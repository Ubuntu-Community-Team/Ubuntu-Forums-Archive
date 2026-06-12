---
title: "Cursor Disappeared! But still there? Help!"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by tombepa on 2010-04-30
I am a newbie, just upgraded to Lynx this morning from Koala. The problem is when I close the lid on my laptop (Dell Inspiron 1501), then open it, my cursor is invisible. It is there and it works but I can't see it. I was able to navigate to enable show where mouse is by pressing ctrl but it will not show me the actual cursor unless I reboot. Any ideas?

---

### Post by tombepa on 2010-04-30
> **tombepa said:**
> I am a newbie, just upgraded to Lynx this morning from Koala. The problem is when I close the lid on my laptop (Dell Inspiron 1501), then open it, my cursor is invisible. It is there and it works but I can't see it. I was able to navigate to enable show where mouse is by pressing ctrl but it will not show me the actual cursor unless I reboot. Any ideas?


Forgot to mention, I am not using an external mouse, just the touchpad if that makes a difference. Thanks for any help.

---

### Post by Babuloseo on 2010-04-30
I have a simliar problems.. My wireless mouse and keyboard stops working just after x starts..... I am able to move it before my desktop appears but then it stops....

---

### Post by jmatties on 2010-04-30
At first I had a cursor, then when I changed the frequency of my monitor from 60Hz to 75Hz it disappeared. I changed it back to 60Hz but it was still gone. It came back later, but now is gone again.

---

### Post by jmatties on 2010-04-30
> **jmatties said:**
> At first I had a cursor, then when I changed the frequency of my monitor from 60Hz to 75Hz it disappeared. I changed it back to 60Hz but it was still gone. It came back later, but now is gone again.

I figured out how to temporarily get the cursor back: I opened users-admin, and tried to change my password to something that was too short. When the warning dialogue came up, my cursor came back.

---

### Post by tombepa on 2010-05-03
New development. I played around and found that if the lock screen comes on, the cursor comes back. I had disabled the lock screen upon waking up by going in to gconf-editor. I don't know what it does but I set it back to lock screen when waking and everything is fine now. Except for the fact that I had to put the password in every time again.:sad:

---

### Post by specialk1st on 2010-07-13
I just posted this on another thread, but having had this problem myself I figured I would spread the word. :)

You can use this as a workaround to get back the missing cursor after opening your laptop lid ...

Try switching desktops via:
Ctrl+Alt+LeftArrow OR Ctrl+Alt+RightArrow

It is a reported bug.

Resource:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/552058)

---

