---
title: "Can't play cd's or dvd's"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by brimorse on 2009-10-18
Greetings all- I've encountered a situation I don't know how to fix.

If I put a music cd (commercial release) in the drive and close it, the screen goes garbled and pixelated and no longer responds.  I have to restart the machine and open the tray before Ubuntu boots to get it out.  No error messages or anything to give me a clue.

Also I tried to open/play a dvd (again commercial release) with no avail.  I tried Movie Player- it though about it for a couple minutes then the program terminated itself, no error message.  I tried dvd::rip and got:

An internal exception was thrown!
The error message was:

Can't call method "project" on an undefined value at /usr/share/perl5/Video/DVDRip/GUI/Project/Title.pm line 436.

So I tried xine next and got:

The source can't be read.  Maybe you don't have enough rights for this or source doesn't contain data.  (Error reading NAV packet).

Do I need to configure the cd/dvd drive in some way?

Any help would be appreciated!

Best regards,

Bri

P.S.  I have an Emachines with an AMD Athlon X2 chip, and have Jaunty 9.04 installed

---

### Post by PorkyPie on 2009-10-18
Could you please give me your full system specs? What os did it run before ubuntu?

---

### Post by jmszr on 2009-10-18
brimorse, 

First, if you have not already, install:

```
sudo apt-get install ubuntu-restricted-extras
```

Then you need to install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) 

As part of installing Medibuntu, be sure to install:

```
sudo apt-get install libdvdcss2
``` 

also:

 ```
sudo apt-get install w64codecs
```

That should get you going.

Edit: Also, I would suggest installing the VLC media player:

```
sudo apt-get install vlc
```

---

### Post by brimorse on 2009-10-22
> **PorkyPie said:**
> Could you please give me your full system specs? What os did it run before ubuntu?

Exactly what specs do you need?  It ran Windows Vista before Ubuntu.

---

### Post by ccook1962 on 2009-12-08
The error message was:

Can't call method "project" on an undefined value at /usr/share/perl5/Video/DVDRip/GUI/Project/Title.pm line 436.

Hi, 

I got this error with DVD::rip too, and I have found a solution.

You have probably fixed it for yourself now, but in case anybody else wants to know then here it is.

Install libdvdcss2 and reboot. (you also have to have libdvdread4 and libdvdnav4 installed, but they probably already are).

I found this fix on a German ubuntu forum. It worked for me.

Chris.

---

### Post by cartisdm on 2009-12-08
> **ccook1962 said:**
> The error message was:

Can't call method "project" on an undefined value at /usr/share/perl5/Video/DVDRip/GUI/Project/Title.pm line 436.

Hi, 

I got this error with DVD::rip too, and I have found a solution.

You have probably fixed it for yourself now, but in case anybody else wants to know then here it is.

Install libdvdcss2 and reboot. (you also have to have libdvdread4 and libdvdnav4 installed, but they probably already are).

I found this fix on a German ubuntu forum. It worked for me.

Chris.

ccook is right, the error you are seeing is likely from not having the extra libraries installed (they can't come bundled with ubuntu because of legal reasons).  There is another post above his that gives a little bit more detailed instructions on how to do that but if you need more help just ask.

---

