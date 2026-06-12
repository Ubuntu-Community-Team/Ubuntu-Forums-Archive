---
title: "xServer error"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by navaneethan on 2009-08-24
I run my ubuntu hardy in my desktop,i ve updated my system using
apt-get upgrade <Upgrading packages>

It shows also error,some lib_modules have been upgraded

Finally i had restarted

It doesn't enter into gdm <after providing username and password>

xinit: Resource temporaily unavailable
(error11) :unable to connect xserver

xinit:no such process
 error3 : server error

how to start gdm?



[http://ubuntuforums.org/images/smilies/guitar.gifUbuntu](http://ubuntuforums.org/images/smilies/guitar.gifUbuntu) Hardy is safetyhttp://ubuntuforums.org/images/smilies/smiley-faces-75.gif

---

### Post by Diabolis on 2009-08-25
[http://www.google.com/webhp#hl=en&source=hp&q=(error11)+%3Aunable+to+connect+xserver&aq=f&aqi=&oq=&fp=35e5f905b5e4329b](http://www.google.com/webhp#hl=en&source=hp&q=(error11)+%3Aunable+to+connect+xserver&aq=f&aqi=&oq=&fp=35e5f905b5e4329b)

---

### Post by NightwishFan on 2009-08-25
Try to run this command in a command line. Press ctrl+alt+f5 to reach one.

```
sudo dpkg-reconfigure xserver-xorg
```

---

