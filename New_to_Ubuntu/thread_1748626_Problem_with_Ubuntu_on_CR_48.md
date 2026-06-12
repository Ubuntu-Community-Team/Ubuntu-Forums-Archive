---
title: "Problem with Ubuntu on CR 48"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by kryptonite30 on 2011-05-03
Hey guys, I was on my cr 48 with ubuntu installed on it. I was setting some keyboard shortcuts until I accidentally pressed ctrl + alt + f8 (the mute button on the cr 48).
The screen then went from my desktop to what I think is called the console? (black screen with a bunch of text)

I didn't know what to do to get it back to my desktop, so I tried rebooting with no avail. Can anyone help me get back to my desktop? And this is ubuntu 11.04. Thanks!

---

### Post by kryptonite30 on 2011-05-03
Yes, it goes through the boot process and I can log in to it.

---

### Post by jramshu on 2011-05-03
I just tried ctrl+alt+f8 and the screen went black, so then I pressed ctrl+alt+f7 and that brought the desktop back up.

---

### Post by jramshu on 2011-05-03
> **kryptonite30 said:**
> Yes, it goes through the boot process and I can log in to it.
Still no desktop?
You do have the command prompt right? Type this:

```
unity
```

---

### Post by kryptonite30 on 2011-05-03
This is what comes up:
WARNING: no DISPLAY variable set, setting it to :0
unity-panel-service: no process found
compiz (core) - Fatal: Couldn't open display :0

---

### Post by kryptonite30 on 2011-05-03
When I press ctrl + alt + f7, the screen goes completely black with only a flashing bar on the top left of the screen.

---

### Post by jramshu on 2011-05-03
> **kryptonite30 said:**
> This is what comes up:
WARNING: no DISPLAY variable set, setting it to :0
unity-panel-service: no process found
compiz (core) - Fatal: Couldn't open display :0

Is that what comes up after typing "unity"?

EDIT: look here
[http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal)

---

### Post by kryptonite30 on 2011-05-03
> **jramshu said:**
> Is that what comes up after typing "unity"?

EDIT: look here
[http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal](http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal)

Yes, that is what comes up. I also tried everything from that link and no luck.

---

### Post by jramshu on 2011-05-03
I've been trying to simulate the problem you are having, with no luck. I can always get the desktop to come back. I'll keep on trying, until I have to go to work, and perhaps some of the more experienced users will jump in.

---

### Post by kryptonite30 on 2011-05-03
Problem solved, I think. I did sudo fsck and rebooted and it brought me back to my desktop. :D
Thanks for the help though guys!

---

### Post by jramshu on 2011-05-03
Glad to hear that. 
I was playing around with it some and on mine when I hit ctrl+alt+f8 I got the black screen, then I hit ctrl+alt+f7 and it would go back to the desktop. Same when I reversed it. The main difference is I didn't reboot, that may have been where an error occurred. 
Good that you got it working.

---

