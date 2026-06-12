---
title: "Canon PIXMA iP1600 installation....again"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Rufus T. Firefly on 2009-09-10
I followed this tutorial:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

and everything seemed to be going swimmingly except I got a couple of warnings:

> Warning: Skipping conversion of scripts in package cnijfilter-ip2200: postinst postrm
and

> Warning: Use the --scripts parameter to include the scripts.otherwise everything seemed fine except I'm a little puzzled about the "library links".

My main point, however, is that, under point 9, the instruction is to click on the iP2200 but it isn't there!! Consequently (I assume) I'm getting an error message.

I would greatly appreciate any help and advice. Thanks.

R.

---

### Post by Rufus T. Firefly on 2009-09-11
Doesn't anyone know?

Or is my post unclear?

R.

---

### Post by cariboo on 2009-09-11
Is this [page]("http:///arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html") of any help? It is for an older version, but it should still work.

---

### Post by Rufus T. Firefly on 2009-09-11
Thanks for the reply. I'll try it and let you know.

R.

---

### Post by Rufus T. Firefly on 2009-09-11
Thanks for the attempt to help, Cariboo, but it proved to be a non-starter. On clicking the link for the download page I got 403 Forbidden. You don't have permission etc.. 

R.

---

### Post by nextwave on 2009-10-23
Ihave installed this printer on Mandriva 2009 32bit as well as my 64bit installations.
[http://software.canon-europe.com/software/0024301.asp](http://software.canon-europe.com/software/0024301.asp)

The IP2200 driver works with the IP1600.

The only issue I had was installing on 64bit.  I had to install libgtk-1.2.so.0  This might help.. i'm not sure with ubuntu [http://ubuntuforums.org/showthread.php?t=599032](http://ubuntuforums.org/showthread.php?t=599032)

The printer works wonderfully!

---

### Post by Aviendha09 on 2009-11-04
Dont want to piss anyone off but installation no longer works in Karmic...I'm in dependency hell. Right now I'm missing pstocanonij. Where is it ?!


EDIT: ok, I found it. Put it in it's place. Canon upgraded some of it's packages (e.g.: the "common" one, from ver 2 to 5.) How has this affected dependencies ? the package installer is not happy with it....
Edit2: still not working.... though it thinks it does....

---

### Post by Aviendha09 on 2009-11-14
Ack! I am never buying a Canon again! (being harsh).

I got the printer working, I was stuck with a corrupted updated "version 80" package. Followed the usual _[tutorial]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200?action=fullsearch&context=180&value=ip1600&titlesearch=Titles")_, but adapted it with the new drivers and libraries except for one teensy-weensy problem : 

> To perform maintenance on the printer, such as head cleaning, type in a terminal: cngpij -P iP2200-Ver.2.60

it's a real useful little interface when set-up as a launcher, but it needs :
```
~$ cngpij -P Canon-iP1600
printuiip2200: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
in order to work. Now, I was able to make simlinks to other newer libraries (ex: libpng, libtiff, etc...) but in this case, the new libgtk2 is a FOLDER, with many libraries and other...things. Which should I point to?

---

### Post by Oropher8598 on 2009-12-04
I found insructions for getting libgtk1.2 at [http://aimbots.net/enemy-territory-linux/19571-how-ubuntu-9-10-karmic-koala-libgtk1-2-a.html](http://aimbots.net/enemy-territory-linux/19571-how-ubuntu-9-10-karmic-koala-libgtk1-2-a.html).

---

