---
title: "Ctrl+Shift+Enter enables fullscreen Terminal?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Salahare on 2010-10-30
Today is the second time I have found myself mistyping, hitting multiple keys accidentally, and finding an unusual reaction - I am logged out of my session and Gnome appears to become disabled, leaving only a fullscreen Terminal-like interface that asks for my login and password. I am able to log in successfully and process commands - if I knew any. This time around I discovered that I can return to the graphical log-in screen if I hit Ctrl+Shift+Enter.

I have made some attempt at researching this key combination online, but have not found anything specifically related to either the Terminal or Ubuntu, not even in the documentation. It's not listed in the Keyboard Shortcuts either. Has anyone else encountered this key combination and know more about why it's there?

I recently upgraded to Maverick Meerkat (10.10) on  my Gateway Media Center 2005, but I don't believe that has too much affect in this particular case.

EDIT: I am unable to re-create the effect of being logged out with the key combination, but I remembered that both times this has happened I was in the process of renaming a file/folder. Perhaps it's just the result of a minor crash?

---

### Post by realzippy on 2010-10-30
...the keys you hit  must have been:

Ctrl+Alt+F1,F2,F3,F4,F5,or F6

which opens a shell (tty1 -6).
Usually Ctrl+Alt+F7 brings you back to the X session.
Ctrl+shift+enter
doesn't do anything here....

---

### Post by Rinzwind on 2010-10-30
control alt f1 = tty1
control alt f2 = tty2 
...
control alt f7 = gnome


You can even control this by adding another desktop environment (DE; like kde) to your system and have control alt f6 show you that DE and control alt f7 show you gnome ;)

---

### Post by Verbeck on 2010-10-30
> **Salahare said:**
> Today is the second time I have found myself mistyping, hitting multiple keys accidentally, and finding an unusual reaction - I am logged out of my session and Gnome appears to become disabled, leaving only a fullscreen Terminal-like interface that asks for my login and password. I am able to log in successfully and process commands - if I knew any. This time around I discovered that I can return to the graphical log-in screen if I hit Ctrl+Shift+Enter.

I have made some attempt at researching this key combination online, but have not found anything specifically related to either the Terminal or Ubuntu, not even in the documentation. It's not listed in the Keyboard Shortcuts either. Has anyone else encountered this key combination and know more about why it's there?

I recently upgraded to Maverick Meerkat (10.10) on  my Gateway Media Center 2005, but I don't believe that has too much affect in this particular case.
alt+ctrl+F1-F6 would take you to the 'full-screen terminal'. to revert just press alt+ctrl+F6/F7

---

### Post by coffeecat on 2010-10-30
What probably happened is that you accidentally managed to get into one of the virtual consoles by pressing ctrl-alt-F1 (or F2, etc). They are there for a purpose, and if you want to get back to the GUI, you simply press ctrl-alt-F7. Or if you are in non-GUI console, alt (minus ctrl) plus the F-key will also switch you to whatever console you want. More here:

[http://en.wikipedia.org/wiki/Virtual_console](http://en.wikipedia.org/wiki/Virtual_console)

I don't know about crtl+shift+enter though. That doesn't work for me.

---

### Post by Salahare on 2010-10-30
No, my fingers were nowhere near the function keys when this happened. And it wasn't just like opening a new terminal. I edited my first post to include that I was also renaming files when I seem to have been kicked out.

Great to learn those new key commands, though. Thanks! After I tried Ctrl+Shift+F1 screen did look like what happened when I got kicked out, but the ctrl+shift+enter didn't work... I don't know if it may be for a specific shell now or not. I'm going to try and recreate what happened on purpose by renaming a file and hitting shift+enter, which is what I'm pretty sure what I did...

---

### Post by coffeecat on 2010-10-30
> **Salahare said:**
>  I'm trying to recreate the effect on purpose now to learn more about it.

That would be a good idea. If you've uncovered a bug that causes the whole of the GUI to crash when renaming a file, then that needs to be investigated. And I wouldn't call that a 'minor' crash. :|

---

### Post by Salahare on 2010-10-30
> **coffeecat said:**
> That would be a good idea. If you've uncovered a bug that causes the whole of the GUI to crash when renaming a file, then that needs to be investigated. And I wouldn't call that a 'minor' crash. :|
Well, nothing seems to really get hurt, so I consider it minor, haha. The files I were modifying all seem to stay intact AND renamed the way I want them to. :)

---

### Post by DooM55 on 2010-10-30
[SIZE=3] ubuntu 10.10 [B]fullscreen Terminal

press F11

:guitar:
[/B][/SIZE]

---

### Post by realzippy on 2010-11-07
@ salahare

...so you can set thread as "solved" (threadtools).

---

### Post by Salahare on 2011-05-14
Sorry for not checking on this thread since I last posted; haven't been using my home computer much since getting back to college.

I don't think I can put this as "Solved" because I know I have my hands nowhere near the Function keys when it kicks me into the fullscreen Terminal. F11 did nothing, hitting ctrl+F*n* has done nothing, and the instance has emerged during any long use of my keyboard to type in my browser, in OpenOffice, and in Text Editor.

Now I'm upgrading to 11.04 and will surely find new issues there. Thanks for the support though.

---

