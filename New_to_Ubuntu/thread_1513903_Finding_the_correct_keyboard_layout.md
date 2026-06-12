---
title: "Finding the correct keyboard layout"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Nr90 on 2010-06-20
Hello guys,
I have a dell inspiron 510m laptop.
It uses the Fn key to type for example SysRq and Scroll Lk.
However with the keyboard layout that ubuntu picked those do not function, because it does not exactly match my keyboard layout.

I tried most of the keyboard layouts in the dell section but none matched my keyboard.

Is there any keyboard layout that should work for me?
If not, are there alternatives to get the desktop selecting key and SysRq to work?

Thanks in advance

---

### Post by simosx on 2010-06-20
> **Nr90 said:**
> Hello guys,
I have a dell inspiron 510m laptop.
It uses the Fn key to type for example SysRq and Scroll Lk.
However with the keyboard layout that ubuntu picked those do not function, because it does not exactly match my keyboard layout.

I tried most of the keyboard layouts in the dell section but none matched my keyboard.

Is there any keyboard layout that should work for me?
If not, are there alternatives to get the desktop selecting key and SysRq to work?

Thanks in advance

The problem you describe is probably not a 'keyboard layout' issue but rather a 'udev' issue related to the keyboard hotkeys.
Have a look at
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)
and tell us whether it helps (or not).

---

### Post by Nr90 on 2010-06-20
That did help,
I narrowed the problem down to it not picking up SysRq and CRT/LCD as keypresses.
However I am not sure how to proceed. Any advice?

(BTW this is the same for me in 3 different kernels, in both lucid and maverick)

---

### Post by simosx on 2010-06-20
> **Nr90 said:**
> That did help,
I narrowed the problem down to it not picking up SysRq and CRT/LCD as keypresses.
However I am not sure how to proceed. Any advice?

(BTW this is the same for me in 3 different kernels, in both lucid and maverick)

In the URL I gave above it mentions how to 'fix udev keyboard issues'.
Specifically, 

> # if the key code is wrong, or there is no keypress event, or the key only works once and then the desktop gets "stuck", exercise the "Fixing broken keys" section in /usr/share/doc/udev/README.keymap.txt (Ubuntu 9.10 and later).

   1. If that was successful, file a bug against udev ("ubuntu-bug udev") and attach your newly created keymap and rule.
   2.

      If udev's keymap tool shows a correct key symbol, look up the symbolic name in /usr/include/linux/input.h. If it is mapped to a code over 255 (over 0x0ff), then it is outside X's range see bug 313514. In this case, if it is important to have the key mapped, the key should be remapped to an appropriate value < 256. 

---

