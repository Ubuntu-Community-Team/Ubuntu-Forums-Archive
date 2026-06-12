---
title: "trying to install xmms"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by newsonp on 2009-11-18
Hello all this is my first post, ):P but I've skulking about for some time now.
Any ways I'm looking to install xmms-1.2.11 on my newly installed ubuntu 9.10 Karmic koala. As your about to find out I'm a total beginner.

I can't find xmms with the package manager, but I did find a tar.bz file
I used the cd commands and did the ./configure and noticed and error. It needed glib. So I downloaded glib-2.12.12 and tried to ./configure that and noticed another error. So I checked the dependencies list and went about downloading these dependencies even though I'm not sure what they do. examples: (gettext-0.17, ncurses-5.7, libiconv-1.11.1) and each one of them ./configures and usually make without error but when I make install they all get denied the permissions they need to install in my folders. 

can I fix this? Am I over complicating it?   :confused:

---

### Post by kanikilu on 2009-11-18
Here's a step-by-step guide (hint: **sudo make install**):

[http://tuxarena.blogspot.com/2009/04/how-to-compile-and-install-xmms-in.html](http://tuxarena.blogspot.com/2009/04/how-to-compile-and-install-xmms-in.html)

---

### Post by Temposs on 2009-11-18
```
sudo make install
```

---

### Post by Temposs on 2009-11-18
Also, xmms is in the repositories. Open System->Administration->Synaptic Package Manager. Type Ctrl-F and search for xmms. Look for the gxmms2 package and install it. Much easier than compiling from source :-)

---

### Post by Cheesemill on 2009-11-18
```
aptitude search xmms
```
will give you the correct package name.

---

### Post by LowSky on 2009-11-18
This works too

```
apt-cache search *Name Of Application*
```

---

### Post by newsonp on 2009-11-18
Thanks for the help.

I was able to find gxmms2 with package manager. It opens the skin but the app isn't running. Not sure, I'll have to keep messing with it.

---

### Post by Spantiznik on 2010-01-16
As with "newsonp", I have installed Gxmms2 player on my machine and it just keeps saying that "Xmmsd2 is not running." And when I click on the "open Playlist Editor" Nothing happens.

---

### Post by Sargalus on 2010-02-26
I just installed gxmm2 through the package manager but I can't find where to open up gxmms or even  start it from the command line


this site is awesome, I would say 90% of the answers im looking for are on this site

---

### Post by comsparks on 2010-02-27
Personally I would scrap 9.10 (too many bugs) and go back to 9.04 which seems to work much better for me. Then you can go to [https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2) and run the program and you will have XMMS up and running with all icons.

---

### Post by DeadSuperHero on 2010-02-27
Try giving:

> sudo apt-get install xmms2

a shot

---

### Post by Sargalus on 2010-02-27
I got it intalled finally but it doesn't work, go figure. xmms just isn't what it use to be. it opens up the mp3 file but just doesn't play it, no error nothing either.

---

### Post by ingridj on 2010-05-28
Are you looking for the 'old' version of xmms?  (Not xmms2, that is.)  If so, you should be able to visit

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2) 

and click on



xmms_1.2.10+20070601-1build2_i386.deb
 
to download and install it.  If I remember correctly, this is what I've done to get things working in 8.04 and 9.04.  


(10.04 is missing some of the packages on which xmms depends.  I skipped from 9.04 to 10.04, so this might be a problem with 9.10 as well.  I've posted details and links of how I got everything working in 10.04 at 
[URL="http://www.shicho.net/lamp/?p=88"]
http://www.shicho.net/lamp/?p=88[/URL]

if it helps.)

 Of course, if you're happy with the newer version of xmm2 or you're  okay with audacious, ignore all this!

---

