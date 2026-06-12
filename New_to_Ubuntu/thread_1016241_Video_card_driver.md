---
title: "Video card driver?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by eloboro on 2008-12-19
Hello, I recently installed Ubuntu on my pc and this is my first time using linux. I've had no troubles so far but now I am trying to install the driver for a Matrox G400 video card and I am getting no where fast. I downloaded the latest driver from their website but I have no idea what to do now. I've read the readme.txt file but it's not much help to someone as ignorant to linux as me. I've been searching the internet for answers for hours but have gotten no where. Any help would be much appreciated.

   Thank You

---

### Post by donkyhotay on 2008-12-19
It's usually easier to install directly from ubuntu if you are capable of doing so. Goto system > administration > hardware drivers and see if you video card is listed. If so just install from there. If you have further problems let us know.

---

### Post by Michael.Godawski on 2008-12-19
hi,

if you want that we help you with the drivers from the Matrox website, please post the link to the download location and the exact name of the drivers you have downloaded. 

thx

---

### Post by eloboro on 2008-12-19
Thanks for the speedy replies guys, but unfortuanetly the driver is not available from Ubuntu's hardware drivers. 

The driver I downloaded is from, 

[http://www.matrox.com/graphics/en/support/drivers/latest/](http://www.matrox.com/graphics/en/support/drivers/latest/)

and the name of the file is, 
  
matrox_driver-x86_32-4.4.0.tar.gz


  Thank You

---

### Post by Kareeser on 2008-12-19
Oookies.

Terminal, navigate to the directory of the file:

```

tar xzvf matrox_driver-x86_32-4.4.0.tar.gz

```

Navigate into the directory, and see if there's a readme file to help you out.

---

### Post by donkyhotay on 2008-12-19
I downloaded the file I think you have there. Kind of stupid that they don't have a readme file. Anyways for this one you need to extract the files. Then bring up a terminal prompt:
```
cd /path-to-file/matrox_driver-x96_32-4.4.0
sudo sh ./install.sh
```
that will at least start the installer.

---

### Post by eloboro on 2008-12-19
OK, so I tried the command you suggested and it says it cant open?

steve@steve-desktop:~$ sudo sh ./install.sh
sh: Can't open ./install.sh

---

### Post by igknighted on 2008-12-19
It is installed by default.  If you want to confirm that you are using it, run that command 'cat /etc/X11/xorg.conf | grep Driver'

---

### Post by eloboro on 2008-12-19
I typed in the command below as you suggested,

cat /etc/X11/xorg.conf | grep Driver

   But nothing shows up at all... it just goes back to a fresh input line. The reason I was thinking I need the driver is becuase I am experiencing very low frame rates while at armorgames.com and such.

   The screen resolution and refresh rate is at the recommended settings, it's just the frame rates are waaay slower than they should be.

---

### Post by igknighted on 2008-12-19
> **eloboro said:**
> I typed in the command below as you suggested,

cat /etc/X11/xorg.conf | grep Driver

   But nothing shows up at all... it just goes back to a fresh input line. The reason I was thinking I need the driver is becuase I am experiencing very low frame rates while at armorgames.com and such.

   The screen resolution and refresh rate is at the recommended settings, it's just the frame rates are waaay slower than they should be.

Hmm, that's right... 8.10 auto-configs everything.

Try 'ls /usr/lib/xorg/modules/drivers | grep mga'.  If it returns 'mga_drv.so' you have the driver installed.

As for whether the driver is in use, try the command 'cat /var/log/Xorg.0.log | grep mga' and see if it looks like xorg is using it while loading.

The linux driver for matrox isn't very good, so you might simply not be able to get great performance from it.

---

### Post by eloboro on 2008-12-19
Hmmm, it looks like it is in fact already 
installed and in use like you said. I guess 
I just won't be able to get the same performance 
out of it as I was getting on windows :(  .
  Anyways... thanks for the help guys.

---

