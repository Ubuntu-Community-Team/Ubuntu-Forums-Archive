---
title: "Unable to change monitor resolution.  What a nightmare!"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by randyleepublic on 2010-03-31
I cannot get the Hardware Driver application to work.  I downloaded a driver from Matrox's website, installed it per Matrox's instructions, the install completed without error, only nothing happens.  I still cant change the resolution on my monitor. I went to the Hardware Driver application, it searches and doesn't find anything.  How the is one supposed to use the Hardware Driver application?  Suggestion: A "Browse" button on the app! :p

---

### Post by uRock on 2010-03-31
Have you tried restarting after installing the driver?

Can you give us some specs for your hardware to help point you in the right direction?

And, if you're not using 6.06 any more, which are you using?;)

Cheers,
Ronnie

---

### Post by randyleepublic on 2010-04-01
Hi, thanks so much for posting.  

I have a Matrox M9140 connected by DVI to 4 Samsung 20" 1600x1200 LCDs.  

I installed Karmic Koala.  I tried using an xorg.conf file like the in the good old days of Dapper, but it's no go.  I can't get any configuration file to work - either they won't parse, don't find any devices, or just make the screen go blank.  

I'd like to convert my company to Ubuntu, but I can't even get my own workstation to work....  :sad:

Randy

---

### Post by mikewhatever on 2010-04-01
Have you done the following:

```
2) Make sure an X Server configuration file exists:

        # cat /etc/X11/xorg.conf [ENTER]

    If you get an error message (such as "No such file or 
    directory"), you'll need to create a new default X Server 
    configuration file. To do this, type:

        # cd /root
        # X -configure
        # mv /root/xorg.conf.new /etc/X11/xorg.conf

```
[ftp://ftp.matrox.com/pub/mga/archive/linux/2009/readme-1.2.0.txt](ftp://ftp.matrox.com/pub/mga/archive/linux/2009/readme-1.2.0.txt)

There is no xorg.conf in Ubuntu by default, but running 'X -configure' should create one. The Hardware Drivers application is intended for ATI/Nvidia drivers installation, so that I suggest you don't bother with it.

---

### Post by randyleepublic on 2010-04-01
Did that and spent about 4 hours trying everything I could think of to get the darn thing to work.  Even the stock file created by the -configure flag wouldn't work.  Modifying it as suggested by the Matrox read me didn't work either.

---

### Post by Martje_001 on 2010-04-01
What's the output of
```
xrandr
```
?

---

### Post by randyleepublic on 2010-04-01
I'll post that tonight.

---

