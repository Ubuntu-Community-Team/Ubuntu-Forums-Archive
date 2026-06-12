---
title: "I can't get fullscreen to work"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-02-25
I reinstalled Ubuntu and updated to Intrepid from Hardy on my Dell Mini 9 and now the windows key doesn't act like F11 anymore.

I already tried this:

To remap the Windows key to F11 (which allows fullscreen in Firefox):
Code:

echo "keycode 115 = F11" > .Xmodmap

It doesn't ask me to load anything.

---

### Post by llamabr on 2009-02-25
> **greenleaves123 said:**
> 

echo "keycode 115 = F11" > .Xmodmap



I'm not sure why you would change an entire keymap to fix firefox.

you're talking about firefox in fullscreen, yes?

---

### Post by greenleaves123 on 2009-02-25
I'm not sure what the command does, I just followed it and it worked before. I can get fullscreen to work in firefox by picking it, but I would like a shortcut key. My Mini9 has no F11 or F12 key.

---

### Post by llamabr on 2009-02-25
Be aware of the necessary file permissions:
$ cat .Xmodmap
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
$ ls -l .Xmodmap
-rw-r--r-- 1 hs hs 135 2006-08-11 20:10 .Xmodmap
$ ls -l .kde/Autostart/
.directory   keyboard.sh
$ ls -l .kde/Autostart/keyboard.sh
-rwxr-xr-x 1 hs hs 42 2006-08-11 20:27 .kde/Autostart/keyboard.sh
$ cat .kde/Autostart/keyboard.sh
#!/bin/sh
/usr/bin/xmodmap $HOME/.Xmodmap

---

### Post by greenleaves123 on 2009-02-25
I'm sorry, I don't understand. Am I supposed to cut and paste all that?

---

### Post by llamabr on 2009-02-25
What's the output of 

```
ls -lh .Xmodmap
```

---

### Post by greenleaves123 on 2009-02-25
jenny@jenny:~$ ls -lh .Xmodmap
-rw-r--r-- 1 jenny jenny 18 2009-02-25 23:07 .Xmodmap
jenny@jenny:~$

---

### Post by llamabr on 2009-02-25
That looks right.  But try:

```
chmod 755 .Xmodmap
```

and log out and back in, just to see.

---

### Post by The-IRS on 2009-02-25
Why not just use F11?

---

### Post by greenleaves123 on 2009-02-25
I did that and restarted. It didn't work.

---

### Post by The-IRS on 2009-02-25
default F11 is fullscreen. Maybe a keymapping mistake when you were tinkering before?

---

### Post by greenleaves123 on 2009-02-26
Yeah, I'm not sure. I am just cutting and pasting stuff.

My Dell mini 9 has no F11 key. Previously that key with the windows symbol was F11, but not it doesn't work anymore.

The screen on my Mini 9 is small so being able to fullscreen is important.

---

### Post by greenleaves123 on 2009-02-26
I just got someone who knows a lot more than me to try to remap the key, he tried many ways, but it didn't work. 

Anyone have any ideas? Is it a hardware problem?

---

