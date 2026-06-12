---
title: "How to set a web page as a desktop background?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-03-01
I'm using Gnome and was wondering if there was a way to set a webpage as a desktop background? I don't want to just take a screen shot and use that, rather have something that refreshes every five minutes or so.

Thanks for all your help

---

### Post by rharriso on 2009-03-01
Did you just want the image of the website to be your background. If so you could write a script to to open up the browser go to the website and take a screen shot of it, then make that your background. And set it as a cron job to run every five minutes.

---

### Post by Sup3r3g0 on 2009-03-01
Actually I was thinking of something that I could actually click on links. I was looking at xwinwrap? I don't know much about it, but it seems like something I could use to get an interactive desktop? 

BTW, is this something that can be done in KDE? If so, I wouldn't mind downloading KDE to get a web page desktop background. Using it in Gnome is peferrable though.

---

### Post by dzark on 2009-03-01
xwinwrap is the way to go. check out this blog

[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

---

### Post by munishvit on 2009-03-02
> **Sup3r3g0 said:**
> I'm using Gnome and was wondering if there was a way to set a webpage as a desktop background? I don't want to just take a screen shot and use that, rather have something that refreshes every five minutes or so.

Thanks for all your help

The same question occurred to me, as I used to have web page as desktop background in Windows. 
[http://ubuntuforums.org/showthread.php?t=1082031](http://ubuntuforums.org/showthread.php?t=1082031)

---

### Post by Sup3r3g0 on 2009-03-02
Thanks

---

### Post by munishvit on 2009-03-02
> **dzark said:**
> xwinwrap is the way to go. check out this blog

[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

I tried, but getting errors:
E: Couldn't find package libxll-dev
The program 'cvs' can be found in the following packages:
 * cvsnt
 * cvs

---

### Post by munishvit on 2009-03-02
> **dzark said:**
> xwinwrap is the way to go. check out this blog

[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

> $ sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
$ cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
$ cd xwinwrap
$ make
$ sudo cp xwinwrap /usr/bin

till here, all commands worked, then
to run glmatrix screensaver as your desktop background:
nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID
didn't work as expected.

a key was given, to change the setting:
xwinwrap [-g] [-ni] [-argb] [-fs] [-s] [-st] [-sp] [-a] [-b] [-nf]
[-fl] [-o OPACITY] &#8212; COMMAND ARG1&#8230;
where,
-g geometry
-ni no input
-argb argb ?? Alpha, Red, Green, Blue ??
-fs fullscreen
-s sticky
-st skip taskbar
-sp skip pager
-a above
-b below
-nf noFocus
-o opacity=# Between 0 and 1

so, instead of /usr/lib/xscreensaver/glmatrix I gave path of html file /home/username/webpage1.html, but it shows error. 
any idea on this?

---

