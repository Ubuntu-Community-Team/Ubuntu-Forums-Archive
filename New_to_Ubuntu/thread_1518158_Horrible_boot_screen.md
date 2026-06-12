---
title: "Horrible boot screen"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by Tahakki on 2010-06-26
In Lucid, I'm not getting the purple boot screen at any resolution. I get a black screen with the following on it:

```
ERROR: Mount none on /dev: no such device
```

This stays for a short amount of time, some more text flashes down the screen and then the login screen appears.

Is there any way to get rid of this first line, or at least cover it all with the nice purple screen?

Cheers.

---

### Post by Evanescence on 2010-06-26
With your mention of the purple screen, I believe that you are using the gnome desktop on Lucid. Once you login, do this:

ALT+CTRL+F1 then enter your username and password as oriented.

Then after successfully login, run the following command:

$ sudo dpkg-reconfigure gnome-desktop

When that is done, do this: ALT+CTRL+F7 to exit

If all goes well, please restart your computer and hopefully the message won't be there.

If you recently upgraded your Ubuntu, then please refer to documentation in this forum about removing old kenel entries.

I hope I've been of help

---

### Post by Tahakki on 2010-06-26
Trying that, I get the error message 'gnome-desktop is not installed'.

---

### Post by Tahakki on 2010-06-28
Bump!

---

### Post by Tahakki on 2010-06-29
Bump again.

---

### Post by CharlesA on 2010-06-29
What happens when you run this from a terminal?

```
sudo apt-get install gnome-desktop
```

---

### Post by Tahakki on 2010-06-29
The package doesn't exist.

---

### Post by laithbsoul on 2010-06-29
That's interesting never had such a problem what desktop environment are you using ie: gnome, kde, xfce

---

### Post by Tahakki on 2010-06-29
GNOME. Standard Lucid install. Realtime kernel.

---

### Post by laithbsoul on 2010-06-29
huh, and what Evanescence said gave you the error that you don't have gnome-desktop installed. thats very odd

if you do what Evanescence said again does it throw the same error at you?

---

### Post by Tahakki on 2010-06-29
You can't reconfig a package you don't have. :)

---

