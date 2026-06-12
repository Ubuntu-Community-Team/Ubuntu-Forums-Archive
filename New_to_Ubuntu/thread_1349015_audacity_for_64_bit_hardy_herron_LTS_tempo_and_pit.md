---
title: "audacity for 64 bit hardy herron LTS: tempo and pitch change"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-12-07
Hi Ubuntu Community:

I am using Audacity and want with a 64 bit Hardy Herron LTS.

I want to change pitch and to change tempo.

Those buttons are available in the Mac and Windows under effects > change tempo and effects > change pitch.

How do I do this?

Thanks,
Phil Smith
Duluth, GA

ps. There seems to have been a similar query in 2008: [http://ubuntuforums.org/showthread.php?t=915587]("http://ubuntuforums.org/showthread.php?t=915587") but nobody replied.

---

### Post by tgalati4 on 2009-12-07
sudo apt-get install sox
man sox

---

### Post by dearingj on 2009-12-07
Your problem, if I'm not mistaken, is that Hardy's main repository has an old version of Audacity (1.3.4), and you want features that were added in a later version. The post you linked to asks about version 1.3.5, which is available in Hardy's backports repository. See [this page]("https://help.ubuntu.com/community/UbuntuBackports") for information about what the backports repository is and how to install packages from it.

Or, you can install a different sound editor such as sox, as tgalati4 suggested.

---

### Post by tgalati4 on 2009-12-07
You can also download the latest audacity source and compile it from scratch.

[http://ubuntuforums.org/showthread.php?t=1169537&highlight=audacity](http://ubuntuforums.org/showthread.php?t=1169537&highlight=audacity)

---

### Post by Old Jimma on 2009-12-08
Thanks to tgalati4 (**[COLOR="Blue"]w/ the very cool icon reminiscent of the classic movie, "Space Balls"[/COLOR]**) and dearingj. 

I will try both suggestions.

I installed sox. It doesn't have a gui front-end, does it? I need an "editor" that allows me to loop for the purposes of teaching segments of music... so that students can hear them over and over... and slowly, if necessary (therefore I need change tempo).

Thanks, and best wishes for a Joyful Holiday Season.
Phil Smith
Duluth, GA

---

### Post by tgalati4 on 2009-12-08
The icon is the business end of an F16 fighter.  

Let us know  if it compiles in 64-bit.  If so, please post a tutorial.   I suspect issues with the soundtouch libraries.  I'm guessing they are either 32-bit, or binary blobs.

Spaceballs is a classic.  Mildly disturbing--like Ubuntu.

---

### Post by Old Jimma on 2009-12-08
Hi tgalati4:

I read your instructions for compiling audacity. I will follow them to the T... so first, I need to run out to the package store to get a few 6-packs (I think this is a part of our instructions). I hope your program runs if I get Mickey's and not Bud lite lime. 

Please stay tuned... I'll let you know how it goes.

Thanks,
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2009-12-08
Yo, Spaceballs:

Well, the Mickey's worked, but the compile didn't. Lots of undefined references, and not too much beer.

I'm gonna take a few aspirins and a nap.

Later...

P from D


zzzzz.....

---

### Post by tgalati4 on 2009-12-09
Cut and paste the errors.  We'll work it out.

---

### Post by Old Jimma on 2009-12-16
Hi tgalati4:

Here is what I've done:

Downloaded audacity from [http://audacity.sourceforge.net/download/source#recdown]("http://audacity.sourceforge.net/download/source#recdown")

The documentation on that page says: 

> The wxWidgets library is required. Audacity 1.2 needs wxGTK 2.4, compiled without the unicode options. The next stable version of Audacity will support newer wxWidgets and GTK libraries.

The wxWidgets library is found at: [http://wxwidgets.org/downloads/]("http://wxwidgets.org/downloads/")

So, I went there and clicked on wxGTK. It began the download for wxGTK-2.8.10 ... NOT the wxGTK 2.4 that was indicated as being required...

After unpacking, there is a readme-gtk.txt file that recommends the following sequence of commands:

[PHP]
    mkdir build_gtk
    cd build_gtk
    ../configure
    make
    su <type root password>
    make install
    ldconfig
[/PHP]

I figured that this meant to move all of the contents of the unpacked directory into the "build_gtk" directory, and proceed with executing the commands.

The ../configure did not work.

So, I tried, ./configure and got the following error:

[HTML]*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
[/HTML]

You must know by now that I have no idea whatsoever what all of that meant!

:)

Any help you might offered will be awarded by the first of the 3 wishes I got from a genie that I found in an old bottle last night.

:idea:

Thanks,
Phil Smith
Duluth, GA

---

### Post by tgalati4 on 2009-12-18
No worries.

apt-cache is your friend:

apt-cache search wxGTK

sudo apt-get install (a bunch of stuff from the above command)

I would probably install the plain 2.4 widgets first.  Always, Always, Always install the -dev packages when building from scratch.

In this case: (on a Jaunty machine)

sudo apt-get install libwxgtk2.4-1 libwxgtk2.4-1-contrib libwxgtk2.4-contrib-dev libwxgtk2.4-dbg libwxgtk2.4-dev

I always use apt-cache search first for required packages.  When you download newer versions of framework packages (such as 2.8 for wxgtk widgets) you can get in trouble.  This is called "dependency file hell".  Always remember to install the -dev packages for anything that your are going to compile against.

Good luck and try again.  I'm too tired to compile it myself this evening.

Don't forget to pull in the basic dependencies: (After enabling source repositories in synaptic)

sudo apt-get build-dep audacity

---

