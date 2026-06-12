---
title: "umm, how do I install flash?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by aaron88_7 on 2011-02-02
yea stupid question, but I seem to be missing something here....


All I'm trying to do is install Flash so I can watch some video on the interwebz.  I already downloaded the tar file (flashplayer10_2_r2_32bit_linux_012611.tar.gz) and extracted it and I get a file named "libflashplayer.so".  

Now what?  Double clicking it just gives me an error, and I can't find an option to let me run this in terminal and because I'm too much of a noob I don't know any basic terminal codes to run this.  I already right clicked the file and set the permission to allow it to be executed, but still getting the same error.

Am I supposed to choose a specific action for this?

Please help so I can learn the elite linix skills of opening files ;)

P.S. I'm getting a book on Ubuntu, so hopefully I won't need this forum section too often :redface:

P.P.S. Is there a 64 bit version of Chrome by any chance?

---

### Post by _outlawed_ on 2011-02-02
This may help you:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by Ctrl-Alt-F1 on 2011-02-02
Open software center and search for flash.  Install the one called adobe flash plugin (not flashplayer 10 plugin).  It will install the 32bit version of flash (most OS's use 32bit flash).  If you're running a 64bit OS, it will download the necessary compatibility libraries and install them for you.  Flash should then work automatically in 32/64bit Firefox, Chrome, etc.  Flash will be automatically updated when necessary.

The terminal command to do this is:

> sudo apt-get install flashplugin-installer

Some people will tell you to use the 64bit flash plugin (I've used it before).  It isn't officially supported (by Adobe or Ubuntu), so I don't recommend it.

There is indeed a 64bit chrome package (it's what I use).  Go to the Google Chrome download site and choose the 64bit.deb.  It will install automatically.

---

### Post by aaron88_7 on 2011-02-02
Thanks, got it going now.

Now no more stupid questions I promise...at least not this week :p

---

### Post by Vaphell on 2011-02-03
> Some people will tell you to use the 64bit flash plugin (I've used it before). It isn't officially supported (by Adobe or Ubuntu), so I don't recommend it.

i am one of such people. For me 64bit beta is rock solid, which couldn't be said about a wrapped 32bit version i used for 1 week before giving up.

this firefox plugin helps install flash and keep things tidy, whichever version you choose. If you go with 32bit, it will install repo version, if 64 - you'll get latest beta from adobe webstite. It's up to you
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

---

### Post by Ctrl-Alt-F1 on 2011-02-03
flashplugin-installer downloads flash from adobe.com

my version of flash: 10.1.102.65
adobe.com flash: 10.1.102.65

---

### Post by Vaphell on 2011-02-03
but you get the overhead of the wrapper which introduces another point of failure, right?
my 64bit flash is 10.3 d162.

---

### Post by cascade9 on 2011-02-03
32bit flash on 64bit sucks. Big time. 64bit flash on 64bit is as good as 32bit flash on 32bit. 

Who wants to install annoying and possibly buggy wrappers, and 32bit libs when there is a 64bit native version? Not me....

---

### Post by Dutch70 on 2011-02-03
> **aaron88_7 said:**
> Thanks, got it going now.

Now no more stupid questions I promise...at least not this week :p

 No such thing as stupid questions...Only stupid answers! 
Glad you got it going.

Good luck,
Dave

---

