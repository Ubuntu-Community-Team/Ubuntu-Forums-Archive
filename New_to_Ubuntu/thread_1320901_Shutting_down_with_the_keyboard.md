---
title: "Shutting down with the keyboard"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by OllieGab on 2009-11-09
Somewhere I read that you can kill off processes and shut down the machine only by pressing various keys on the keyboard. I think it was Alt (or Ctrl) and several of the letters (but one at the time!) but it had to be done in a specific order to shut down things "logically".
Anyone knows what the sequence of key presses is?

---

### Post by Steve Roscio on 2009-11-09
I use 
  Ctrl+Alt+L to lock the desktop,
  Ctrl+Alt+Del to logout normally
  Ctrl+Alt+Backspace to kill the X-server (brutal logout)
  Ctrl+Alt+Arrows to move between workspaces
    etc...

These depend upon your layout settings and keyboard shortcut settings, see 
     System -> Preferences -> Keyboard Shortcuts
or
     System -> Preferences -> Keyboard -> Layout tab -> Layout Options

- Steve

---

### Post by sandyd on 2009-11-09
> **OllieGab said:**
> Somewhere I read that you can kill off processes and shut down the machine only by pressing various keys on the keyboard. I think it was Alt (or Ctrl) and several of the letters (but one at the time!) but it had to be done in a specific order to shut down things "logically".
Anyone knows what the sequence of key presses is?
hint: look in xmodmap
hint 2: ctrl+alt+backspace only works if you set dontzap

---

### Post by marshmallow1304 on 2009-11-09
Do you mean [REISUB]("http://kember.net/articles/231/reisub-the-gentle-linux-restart")?

---

### Post by Mariane on 2009-11-09
```

sudo shutdown now

```

```

sudo reboot now

```


Will do what you expect

If you are crashed you can

```

kill -9 -1 

```

but this is really brutal and should be avoided whenever possible. 

Mariane

---

### Post by niteshifter on 2009-11-09
Hi,

I think the OP is referring to the "Magic Keys":

```
Ctrl+Alt+SysRq+
 R
 E
 I
 S
 U
 B

```
aka the kernel request or kernel control keys. Useful when the system goes locker on you. See [this page]("http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html").

Although that article says alt+[R E I S U B] on every version of Ubuntu from 6.10 onward I've used Ctrl+Alt+SysRq has been needed.

---

### Post by OllieGab on 2009-11-10
> **Mariane said:**
> ```

sudo shutdown now

```

```

sudo reboot now

```


Will do what you expect

If you are crashed you can

```

kill -9 -1 

```

but this is really brutal and should be avoided whenever possible. 

Mariane

Well, I meant as what niteshifter and marshmallow1304 are referring to (I think!):), ie when there is no access to any other means of controlling the computer, including being able to open up a terminal!

---

