---
title: "help installing ImageMagick"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by CleveRuse on 2011-06-28
can someone please help me install ImageMagick on Ubuntu Natty? I went to the site and and tried typing:

"$magick> identify -version" 

to see if if already installed, but it says "magick" is not a command... then says something bout "identify", and that "-version" is not a command.

Then every other command to install it after that begins with "magick", which is not a command... So how the hell do i install it?

Soooooooooooooo FRUSTRATED, Lol.....

---

### Post by wolfen69 on 2011-06-28
```
sudo apt-get install imagemagick
```

---

### Post by CleveRuse on 2011-06-28
> **wolfen69 said:**
> ```
sudo apt-get install imagemagick
```

thnx man, thats it. I actually tried that but i was hyphenating image-magick. i shouldve thought of that tho.

i shouldve already had the packages but i un-installed almost all kde packages trying to remove kde desktop.

thnx again bro.

---

### Post by sam_delta on 2011-06-28
when you are unsure of the name, and you wish to use the terminal, you could always do a search.

```
apt-cache search keyword
```

sam

---

### Post by dFlyer on 2011-06-29
You can start synaptic and in the filter enter imagemagick and install from there or you can also use Ubuntu Software Center, just enter imagemagick and click install.

---

### Post by mcduck on 2011-06-29
> **CleveRuse said:**
> can someone please help me install ImageMagick on Ubuntu Natty? I went to the site and and tried typing:

"$magick> identify -version" 

to see if if already installed, but it says "magick" is not a command... then says something bout "identify", and that "-version" is not a command.

Then every other command to install it after that begins with "magick", which is not a command... So how the hell do i install it?

Soooooooooooooo FRUSTRATED, Lol.....

like others said, *sudo apt-get install imagemagick* works.

What comes to the command you tried to run, the problem is that the "$magick>" isn't part of the command, that's just there to represent the command prompt. So the command to check Imagemagick version is *identify -version*

---

### Post by CleveRuse on 2011-06-30
thnx guys, i install with "apt-get" but now when i type in the command to adjust the hue of the some images i placed in a folder on my desktop, i get this:

ab@CleveRuse-LT20:~$ cd '/home/ab/Desktop/magick' 
ab@CleveRuse-LT20:~/Desktop/magick$ mogrify -modulate 100,100,140 *.*
mogrify: no decode delegate for this image format `btn_check_on_disable_focused.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_check_on_disable.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_check_on_pressed.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_check_on_selected.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_circle_disable_focused.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_circle_pressed.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_circle_selected.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_close_pressed.png' @ error/constitute.c/ReadImage/532.
mogrify: no decode delegate for this image format `btn_close_selected.png' @ error/constitute.c/ReadImage/532.
ab@CleveRuse-LT20:~/Desktop/magick$ 

i can be more specific if anyone thinks they can help. I just get so frustrated, lol. All i wanna do is theme my android device without having to edit 300+ images individually. I tried Phatch but apparently there is no Hue option.

---

### Post by pqwoerituytrueiwoq on 2011-06-30
[http://www.imagemagick.org/www/mogrify.html](http://www.imagemagick.org/www/mogrify.html)
that may help

---

### Post by mcduck on 2011-06-30
works fine for me, running the Imagemagick version from Natty's repositories.

Try using the image file type in the command ("*.png" instead of "*.*")

edit:
If that doesn't work, then please run "convert -list configure" in a terminal and post the output here. The most interesting part is the "DELEGATES" line, although I can't really see how you could miss any if you are using the Imagemagick from repositories instead of trying to compile it yourself or something...

---

### Post by CleveRuse on 2011-07-01
[QUOTE=mcduck;10998827]works fine for me, running the Imagemagick version from Natty's repositories.

Try using the image file type in the command ("*.png" instead of "*.*")

edit:
If that doesn't work, then please run "convert -list configure" in a terminal and post the output here. The most interesting part is the "DELEGATES" line, although I can't really see how you could miss any if you are using the Imagemagick from repositories instead of trying to compile it yourself or something...[/QUOTE=mcduck;10998827]

thnx guys. ok hold on.....

---

### Post by CleveRuse on 2011-07-01
Nope, didn't work. Here's my output from terminal:

ab@CleveRuse-LT20:~/Desktop/magick$ convert -list configure

Path: /usr/lib/ImageMagick-6.6.2/config/configure.xml

Name          Value
-------------------------------------------------------------------------------
CC            gcc -std=gnu99 -std=gnu99
CFLAGS        -I/usr/include/lqr-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -fopenmp -g -O2 -Wall -pthread
CONFIGURE     ./configure  '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--with-modules' '--with-gs-font-dir=/usr/share/fonts/type1/gsfonts' '--with-magick-plus-plus' '--with-djvu' '--with-perl' '--enable-shared' '--without-dps' '--without-fpx' '--with-perl-options=INSTALLDIRS=vendor' '--x-includes=/usr/include/X11' '--x-libraries=/usr/lib/X11' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
COPYRIGHT     Copyright (C) 1999-2010 ImageMagick Studio LLC
CPPFLAGS      -I/usr/include/ImageMagick
CXX           g++
CXXFLAGS      -g -O2 -pthread
DEFS          -DHAVE_CONFIG_H
DELEGATES     bzlib djvu fontconfig freetype gvc jpeg jng jp2 lcms lqr openexr png rsvg tiff x11 xml wmf zlib
DISTCHECK_CONFIG_FLAGS 'CFLAGS=-g -O2' 'CPPFLAGS=' 'LDFLAGS=-Wl,-Bsymbolic-functions' --disable-deprecated --with-quantum-depth=16 --with-umem=no --with-autotrace=no --with-dps=no --with-fpx=no --with-gslib=no --with-fontpath= --with-gs-font-dir=/usr/share/fonts/type1/gsfonts
EXEC-PREFIX   /usr
HOST          i686-pc-linux-gnu
LDFLAGS       -L/usr/lib -Wl,-Bsymbolic-functions -L/usr/lib/X11
LIB_VERSION   0x662
LIB_VERSION_NUMBER 6,6,2,6
LIBS          -lMagickCore -llcms -ltiff -lfreetype -ljpeg -llqr-1 -lglib-2.0 -lfontconfig -lXext -lSM -lICE -lX11 -lXt -lbz2 -lz -lm -lgomp -lpthread -lltdl
NAME          ImageMagick
PCFLAGS       -fopenmp
PREFIX        /usr
QuantumDepth  16
RELEASE_DATE  2011-03-16
VERSION       6.6.2
WEBSITE       [http://www.imagemagick.org](http://www.imagemagick.org)

Path: [built-in]

Name          Value
-------------------------------------------------------------------------------
NAME          ImageMagick
ab@CleveRuse-LT20:~/Desktop/magick$

---

### Post by augr on 2011-08-14
Decided to go into IRC channel to sort this out. Cheers.

---

### Post by augr on 2011-08-21
Sorted.... all done. Cheers.

---

### Post by CleveRuse on 2011-11-10
> **augr said:**
> Sorted.... all done. Cheers.


...4 months later:

         Huh? Well i just installed Ubuntu LTS cuz 11.04 was too buggy ...and i'm having the same exact issue here. i installed IM from the repository, but i still am receiving the same error about the "delegates".

---

