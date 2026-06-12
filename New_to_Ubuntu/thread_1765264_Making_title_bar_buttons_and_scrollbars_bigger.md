---
title: "Making title bar buttons and scrollbars bigger"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by bday_cs on 2011-05-22
I'm just trying out ubuntu 11.04 with the unity desktop.

I don't have fine motor control of my head mouse, and would like to know if it's possible to increase:

1. The size of title bar buttons. I can see where to increase the font size of the text of the title bar, but it does not increase the size of the buttons. I'm using the default ambience theme.
2. The size of the scrollbar when it appears. I keep slipping off the bar before I have a chance to move it.
3. The thickness of window border to resize windows.

Thank you in advance for the help. I did try searching for a number of hours on this... but perhaps I wasn't using the correct search terms.

Also... in case the answer is the unity desktop isn't a good match for what I would like to do, can you suggest an alternative such as kubuntu, etc.

---

### Post by kaldor on 2011-05-22
Well, one thing I can recommend is how to fix the scrollbars. The new scrollbars seem very counter-intuitive to me. You can remove them easily. Remove the *overlay-scrollbars* package in the Software Centre or run this command:

```
sudo apt-get remove overlay-scrollbars
```

After that, relogin.

Edit: Just noticed I forgot to answer your Unity alternative question.

You don't need Unity in 11.04. Log out of your session, and click your Username in the login screen. Do not enter password/log in yet. On the bottom of the screen. Change Session from "Ubuntu Desktop" to "Ubuntu Classic". NOW log in. You will be back on the regular Panel'd desktop.

---

### Post by Sef on 2011-05-23
Moved to ABT.

---

### Post by bday_cs on 2011-05-23
Thank you for the tip on removing the overlay scrollbars... I do like the old ones better.
However I would like to still increase the width of those scrollbars.

Any other help on these questions?

---

### Post by wildmanne39 on 2011-05-23
> **bday_cs said:**
> Thank you for the tip on removing the overlay scrollbars... I do like the old ones better.
However I would like to still increase the width of those scrollbars.

Any other help on these questions?
Hi, these links have a lot of tweaks and fixes you can see if  the answer is there.
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)  [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)  [http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)  Also you can right click the desktop and go into fonts and change the size of the text, that is what I do.:)

---

