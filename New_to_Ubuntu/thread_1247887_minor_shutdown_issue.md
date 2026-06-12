---
title: "minor shutdown issue"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Daniel1994 on 2009-08-23
I've been running ubuntu for almost half a year now, with very few bugs..but there is one that has been there from the beginning though, I just haven't bothered to post it yet.

When I turn the computer off, I have to press a button AFTER the shutdown to make the screen turn off.

It's not much of a problem, but it's really annoying.


Appreciate any help:)

Forgot to say, I'm using a Acer aspire 4520 laptop

---

### Post by Paddy Landau on 2009-08-23
I used to have that problem, and sadly I don't remember how I solved it. It was a post somewhere on this forum.

I found these two posts, and I hope they help.

[http://ubuntuforums.org/showpost.php?p=7833849&postcount=5](http://ubuntuforums.org/showpost.php?p=7833849&postcount=5)
[http://ubuntuforums.org/showpost.php?p=6176637&postcount=28](http://ubuntuforums.org/showpost.php?p=6176637&postcount=28)

---

### Post by Shazaam on 2009-08-23
Test this on your next boot...
1. When the grub screen shows up hit your ESC keyboard key. This will give you a list of os/kernels to boot.
2. Using your keyboard up and down arrows move to the entry you use.
3. Click the "e" key (without the quotes) which will allow you to edit the entry; move to the kernel line and hit "e" again.
4. At the end of the kernel line add a space then add this...
```
acpi=force
```
5. Hit the "b" (boot) key when you are done and it should boot to the desktop.
Now see if it will completely shut down. If it does edit /boot/grub/menu.lst and add acpi=force to the end of whichever kernel you use.

---

### Post by Daniel1994 on 2009-08-24
thanks for your replies, I haven't got I working yet, though. Guess I just got to keep trying.

---

### Post by sithclone on 2009-08-24
I had a similar issue where I would shut down, but the tower wouldn't power off and I had to hold the power button down to shut it off completely. This is what I did to fix it:

$sudo gedit /etc/init.d/halt

add this line to the top of the script:

rmmod snd-hda-intel

hope that helps

---

