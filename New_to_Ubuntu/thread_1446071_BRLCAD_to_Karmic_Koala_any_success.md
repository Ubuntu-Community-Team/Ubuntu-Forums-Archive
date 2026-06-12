---
title: "BRLCAD to Karmic Koala: any success?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by The Pilgrim on 2010-04-03
Hi folks, 

I need a CAD software on Ubuntu Karmic Koala 9.10. After a relatively good search, it seems BRLCAD might be the one. But again, seems that noone installed it successfuly on Linux. Someone tells me I'm wrong?

Thank you.

Stefan

---

### Post by patchwork on 2010-04-03
I have it running on karmic.  I chose to install from the source code available [here]("http://sourceforge.net/projects/brlcad/files/BRL-CAD%20Source/").  Installing from the prebulit binary caused some dependency problems, so rather than chase my tail linking libraries from 64 to 32 bit, I decided the source install was the easier way to go.

---

### Post by The Pilgrim on 2010-04-04
Oh, faster than I would ever hope... :) Thank you patchwork. Please do not forget I'm an almost absolute beginner to both (Ubuntu & BRLCAD). Do I ask too much for a step by step install guide? I've been on that link you send a  week ago and got stuked into it. I'm only used - still - to win style of install. Please tell me the exact release of brl you have installed.

Thank you again.

---

### Post by patchwork on 2010-04-04
I am using brlcad-7.16.6

To install, download the source ( brlcad-7.16.6.tar.gz ), move it to the directory you want to install it in ( I chose /usr/local/bin, but you can use the default ), unpack the archive, then ./configure - make - make install
```
sudo cp brlcad-7.16.6.tar.gz /usr/local/bin
sudo tar xzvf brlcad-7.16.6.tar.gz
cd /usr/local/bin/brlcad-7.16.6
./configure
sudo make
sudo make install

```The README contains the full generic installation instructions.
Once installed, brl is started using the mged command ( you'll definitely want to work through the resources listed in the link below).
Also from the README:
> By default, the package is configured to install
entirely into /usr/brlcad/.

You will need to add /usr/brlcad/bin to your path (or whatever was
used as a --prefix during configure) in order for the BRL-CAD binaries
to be in your path.As far as the use of brlcad, I am new to it myself (not an expert ).  It certainly isn't intuitive, and will take some getting used to, but it seems quite powerful.  Some resources I've found useful thus far are from here:

[BRL Wiki]("http://brlcad.org/wiki/Mged")

---

### Post by The Pilgrim on 2010-04-04
Thank you. I did download the archive. I have no permission to move / copy it in "/usr/local/bin". I use gnome commander and also tryed with drag'n drop, but no way. Perhaps I should have admin rights, but no pass prompt apeared to me. So, I'm stuked :(.

Hope I won't be a pain in the ... with my lack of knowledge.

Thanks again for your time.

ps. Is any technical reason to alter the default place of install? You kinda confused me with that and I try not to mess alot with repeated bad installations.

---

### Post by patchwork on 2010-04-04
Only technical reason to alter either the place of install or your PATH variable would be to allow the mged command to be called without specifying the directory to it as well ( the directories in the $PATH variable are automatically searched for commands, other directories, such as your /home/user directory, are not.  Any programs you'd like to run from these other directories must be prefaced with the path to the program.

As far as not having privileges, do you have superuser or administrator rights?  Did you try copying the file in the terminal (with the sudo command) or did you just try to drag and drop in nautilus?  If you want to use nautilus, and you have superuser privileges,  you will need to start nautilus with ```
gksu nautilus
```  If you don't have superuser privileges on your account, you may still be able to install the program to your /home/user directory by specifying it during the 'make install' command, but I've never tried doing this.

---

### Post by The Pilgrim on 2010-04-05
I'm the one and only user of this computer, so the password is mine; but had no place to enter it :).
I suppose nautilus is a similar to gnome commander.
I'll try from command line to move the file.

This what I got trying to call nautilus from root terminal:

<<
root@compal:/home/stefan# gksu nautilus

(nautilus:5686): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension

** (nautilus:5686): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5686): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5686): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:5686): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
sys:1: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Shutting down nautilus-gdu extension
root@compal:/home/stefan# 

>>
perhaps something missing? No install for missing elements option though.

shall try further..

AND DONE!! 
from gnome commander  entered as root and installed BRLCAD. This is the result:

<<
Build Tcl ............................: yes
Build Tk .............................: yes
Build Itcl/Itk .......................: yes
Build IWidgets .......................: yes
Build tkhtml3 ........................: yes
Build tkImg ..........................: yes
Build libpng .........................: no (using system)
Build libregex .......................: no (using system)
Build zlib ...........................: no (using system)
Build termlib ........................: yes
Build Utah Raster Toolkit.............: yes
Build Template Numerical Toolkit......: yes
Build openNURBS.......................: yes
Build NIST STEP Class Libraries.......: no
Build jove ...........................: no

X11 support (optional)................: yes
OpenGL support (optional).............: no
librtserver JDK support (optional)....: no
Enable run-time debugging (optional)..: yes

Build 64-bit release .................: no (32-bit)
Build optimized release ..............: no
Build debug release ..................: auto
Build profile release ................: no
Build SMP-capable release ............: yes
Build static libraries ...............: yes
Build shared/dynamic libraries .......: yes
Print verbose compilation warnings ...: no
Print verbose compilation progress ...: no

Only build benchmark suite ...........: no
Only build librtserver ...............: no
Install example geometry models ......: yes
Install extra docs ...................: yes (man/html only)

Elapsed configuration time ...........: 1 minute, 38 seconds
---
./configure complete, type 'make' to begin building
>>

and a new question arrived: some points are marked "no" regarding installation. Should I search for them? Do they have to be also installed as this moment?

Thank you so far patchwork.

---

### Post by patchwork on 2010-04-05
No, I wouldn't worry about it, those options won't prevent your installation or use.

---

