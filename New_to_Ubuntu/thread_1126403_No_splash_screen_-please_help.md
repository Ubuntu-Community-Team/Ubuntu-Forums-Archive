---
title: "No splash screen -please help"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by newlinuxuser2008 on 2009-04-15
Just installed on a dell dimension 4600 and i have no splash screen during start or shutdown

on ubuntu on kubuntu

what's going on?

---

### Post by RedSingularity on 2009-04-15
What do you get?  A bunch of words on a black screen?

---

### Post by taurus on 2009-04-15
You mean the text scrolls up the screen during boot and shutdown?

---

### Post by newlinuxuser2008 on 2009-04-15
just a blank screen during loading then the login box

---

### Post by Jakey_TheSnake on 2009-04-15
Try: ```
sudo gedit /etc/usplash.conf
```

Then changing the resolution to your monitor resolution, then: 

```
sudo update-usplash-theme usplash-theme-ubuntu
```

I almost forgot, make sure you have a usplash set: ```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by newlinuxuser2008 on 2009-04-15
still no splash

after applying the 3rd code
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure

---

### Post by Jakey_TheSnake on 2009-04-15
I forgot this: ```
sudo update-initramfs -v -u -k all
``` run after you've edited your usplash.conf.

---

