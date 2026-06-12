---
title: "Photoshop and basics etc"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by sawfish62 on 2008-12-29
I'm at the stage of absolute beginner here, in fact I haven't even installed Ubuntu yet.

I just need to know if it will work with photoshop, flash, dreamweaver and other such programs as I need these for my work. I'm getting a new 64 bit laptop next month and would like to have Ubuntu as long as the learning curve isn't too enormous. 

Can anyone give me any really basic help?

---

### Post by Skripka on 2008-12-29
I can't speak for other Adobe CS apps-but Photoshop CS3 and CS4 have yet to really run on Linux.  You can get Photoshop CS3 to run but it takes doing more than a few less than legal things.  The problem is not the app itself-but the damn installer that won't run under Wine.


If you want to run Adobe CS you basically need a Windows install for it.  That is what I do, do thing in *nix until something requires Win to run then boot the other OS and get work done-then come back to the Linux drive.

---

### Post by blueridgedog on 2008-12-29
> **sawfish62 said:**
> I just need to know if it will work with photoshop, flash, dreamweaver and other such programs as I need these for my work

These are great windows programs and some people have gotten a few of them to work under Ubuntu with a great deal of tweaking, but the short answer is no, you will not be able to run these in Ubuntu.  Some users dual boot, some run a virtual box and some get accustomed to other tools.

---

### Post by Sealbhach on 2008-12-29
Photoshop no.

If you want to try out Ubuntu you could install it within Windows using the "patented" Wubi installation method:

[http://wubi-installer.org/](http://wubi-installer.org/)

Or you could dual boot by partitioning the hard drive.

It's probably your best solution if you want to try out Linux.

.

---

### Post by sawfish62 on 2008-12-29
thanks for all the help guys. What might the alternative to photoshop be?

---

### Post by clive littlewood on 2008-12-29
Hi and Welcome to Ubuntu and the community.   :D

Photoshop does not work in a native Linux system but people have had varing degrees of success using a program called WINE that will run windoze programs in Linux Distros.

My advice would be to keep windoze initially and run Ubuntu from a Live CD to try everthing without altering your setup.

You can also try using GIMP which is a similar program to photoshop and highly regarded.

Hope this helps       :D

Clive

---

### Post by evilkastel on 2008-12-29
Well, you have seen, is not easy to run windows apps in Ubuntu, but there are Free alternatives, they lack of *some* things but they are great and if you are a little recursive you can get almos everything done.

They are 
Photoshop-------> GIMP
Vector graphics creation and edition--------->Inkscape
Diagramation------------------------->Scribus
And so on... here you can find alternatives to most used widows apps.

[http://www.osalt.com]("http://www.osalt.com")

Cheers!

---

### Post by Sealbhach on 2008-12-29
It is said that GIMP lacks a few of the more advanced features of Photoshop - something that has prevented some people from adopting Linux. Hence, I think dual-booting would be a good option so you can evaluate whether Open Source applications will meet your needs.


.

---

### Post by philinux on 2008-12-29
> **sawfish62 said:**
> thanks for all the help guys. What might the alternative to photoshop be?

Gimp.

[http://www.gimp.org/](http://www.gimp.org/)

If you use the basic photoshop stuff then this app is fine.

---

### Post by mkvnmtr on 2008-12-29
It sounds like for you a dual boot or even better a wubi install would be the best for you. You can continue to use what you need in windows and in your own good time check out what is in Ubuntu. There is a learning curve. Many of us like it better but if your using your system to make money the pressure is too great to switch all a once.

---

### Post by MrWES on 2008-12-29
There is a dep package called GimpShop; made to look and feel more lile Photoshop:

[http://gimpshop.com/download.shtml]("http://gimpshop.com/download.shtml")

The .deb package is towards the bottom of the page.

Bill

---

### Post by sawfish62 on 2008-12-29
I've just installed wubi but I don't know how to get it started?

---

### Post by appi2012 on 2008-12-29
If you downloaded the .exe file, then just run it. It will ask for a few things such as how much space you want it to use, what your username and password should be, etc. After supplying it with the information, you can just hit next, and it will download and virtually install ubuntu, in a way that if you are having trouble with it, and want to remove it, you can simply go to Window's Add/Remove Programs and uninstall Ubuntu there. However, this method will not allow you to remove windows and keep ubuntu, and may run a tad slower. But for your needs, Wubi is the best bet.

Hope that helps!

---

### Post by sawfish62 on 2008-12-29
yes but its still just windows. There doesn't seem to be an Ubuntu icon to click on.

---

### Post by Lazerouth on 2008-12-29
Welcome to Ubuntu!

Even if you are working with graphics on a professional level, as I am, you should check the new GIMP 2.6 out, It takes some getting used to, but once you get the hang of it, I was surprised how much it competes with His Royal Majesty, Sir Photoshop.

---

### Post by albinootje on 2008-12-29
> **sawfish62 said:**
> I'm at the stage of absolute beginner here, in fact I haven't even installed Ubuntu yet.

I just need to know if it will work with photoshop, flash, dreamweaver and other such programs as I need these for my work. I'm getting a new 64 bit laptop next month and would like to have Ubuntu as long as the learning curve isn't too enormous. 

Can anyone give me any really basic help?

Depending on the specifications of your computer, if you prefer a 100 % Linux installation, then I recommend using VirtualBox, otherwise go for a dual-boot Linux/Windows installation.

If the versions of Photoshop that you have are not so new, see here for commercial software to run those inside Linux almost natively :
[http://www.codeweavers.com/compatibility/browse/name/?letter=all;sort](http://www.codeweavers.com/compatibility/browse/name/?letter=all;sort)[medal_id]=DESC

And concerning Gimp as alternative for Photoshop.
Through the years I've read a lot of comments from professionals using Photoshop who say that Gimp is not ready for them.
The thing is that Gimp is different, so you will need to learn a bit, and Ubuntu 8.10 features Gimp 2.6, from which I read is ready as a Photoshop replacement for some professionals already.

---

### Post by sawfish62 on 2008-12-29
no, not to make money, just a bit of web design. I might try the dual system thing. Get XP and Ubuntu. I hate Vista!

Still cant get Ubuntu to start up. What do I do?

thanks folks :-)

---

### Post by Sealbhach on 2008-12-29
> **sawfish62 said:**
> yes but its still just windows. There doesn't seem to be an Ubuntu icon to click on.

When you reboot, you should see an option to boot into Ubuntu. Wubi has added this option to your Windows MBR. 

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20select%20whether%20to%20run%20Windows%20or%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20select%20whether%20to%20run%20Windows%20or%20Ubuntu?)

Like this:

[IMG]https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=boot-screen.jpg[/IMG]

.

---

### Post by albinootje on 2008-12-29
> **sawfish62 said:**
> no, not to make money, just a bit of web design. I might try the dual system thing. Get XP and Ubuntu. I hate Vista!

Still cant get Ubuntu to start up. What do I do?


Instead of Wubi, try the 8.10 and/or 8.04 installation cdrom, and try a "live session" first to see how well your laptop is supported.
After you're happy with that, start installing :)

---

