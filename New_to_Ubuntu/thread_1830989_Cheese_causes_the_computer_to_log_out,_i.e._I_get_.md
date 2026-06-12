---
title: "Cheese causes the computer to log out, i.e. I get kicked out to the login screen"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by woody1 on 2011-08-22
I can open Cheese and see the picture from my webcam, but as soon as I try to take a photo or even click the help tab the screen goes blank, then after a few seconds the login screen appears. I am using Ubuntu 11.04, and the version of cheese according to synaptic is 2.32.0ubuntu2. This also happens when I try to use video on skype. Any thoughts or possible lines of investigation would be much appreciated.

                                 Regards,
                                                    Colin

---

### Post by jfed on 2011-08-22
Well thats weird as anything, sounds like there is something wrong with your webcam drivers, or something of that nature. Try running cheese threw a terminal and seeing if it puts out any error reports while using it or upon crashing.

---

### Post by woody1 on 2011-08-27
I tried running cheese in a terminal as suggested. I could see the picture from the webcam, but as soon as I click on help, or any buttons or tabs onscreen I get logged out as before. Where would you suggest looking for error messages ?

Thanks, 
       Colin

---

### Post by CatKiller on 2011-08-27
Can't help specifically, since I don't use either of those applications, but it's not logging you out. Sounds like an X crash to me. Might help you find the right direction.

---

### Post by no2498 on 2011-08-27
in a terminal type

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 
click enter



i hope it helps

---

### Post by woody1 on 2011-08-27
Hmm, that seems to have changed the cheese problem . Now I can take two or three photos before I get kicked out to the login screen.
Thanks for your help,
                     Colin

---

### Post by no2498 on 2011-08-28
i use this program myself wxcam

if you browse all files you can get it in a deb file

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

