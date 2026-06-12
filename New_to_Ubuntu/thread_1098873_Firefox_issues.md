---
title: "Firefox issues"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by ClaytonOT on 2009-03-17
[http://www.xbrothersforlifex.com/gallery/albums/userpics/10002/Screenshot.png](http://www.xbrothersforlifex.com/gallery/albums/userpics/10002/Screenshot.png)

As you can see from that picture, my firefox likes to launch without any toolbar. I have to hit F11 twice for the toolbar to comeback (that includes the minimize, maximize, and exit button)

This has happened before, but I had to reinstall Ubuntu so the issue went away. Now it's back, and I have no idea what the cause is. Hitting F11 twice isn't a big deal, but it's something I'd like to get fixed.

If you need any more details just ask, I'm on the 64-bit version.

---

### Post by fooman on 2009-03-17
open firefox and do the f11 thing twice to get to a normal looking screen.

click on the unmaximize button.

close firefox....then open firefox.

click the maximize button.

...should be fixed for good now.  :)

---

### Post by ClaytonOT on 2009-03-17
Awesome, thanks. :)

---

### Post by Crafty Kisses on 2009-03-17
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```
Once you've done that close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace

```
The other obvious fix as stated above is pressing F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal. The issue really only occurs when Firefox crashes and you reboot it, but those are the fixes and I've tested them myself and they do actually work.

---

