---
title: "AdobeReader 9.1"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by khon on 2009-04-01
Can I install AdobeReader 9.1 on Ubuntu v8.10 
Dell 1525 Laptop

---

### Post by redbob on 2009-04-01
Khon, youre welcome to Ubuntuforums.
At a first glance, Adobe didn't release Reader 9 for Linux.
I'm using Jaunty (9.04), even for it I couldn't find any.

---

### Post by ibuclaw on 2009-04-01
[http://get.adobe.com/uk/reader/otherversions/](http://get.adobe.com/uk/reader/otherversions/)

Select "**Linux x86 .deb**" in the "Select an Operating System" dropdown menu.

If you are on 64bit, I will look into seeing if it can be ported.

Regards
Iain

---

### Post by RedSingularity on 2009-04-01
Yeah you can install it on 32bit and 64bit.  I have it on my 64bit system.

---

### Post by ibuclaw on 2009-04-01
Yep:

I just downloaded the [tarball of Adobe9.1]("http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.1/enu/AdbeRdr9.1.0-1_i486linux_enu.tar.bz2"), set the install directory as **/usr/share/acroread**


For 64bit users, I recommend you install [getlibs]("http://ubuntuforums.org/showthread.php?t=474790").
Then run the following:
```
getlibs -p gvfs libace-dev libbonobo2-dev libcurl3 libgnome-speech-dev libicu-dev libldap2-dev liborbit2-dev libssl-dev libbibutils0
```
```
sudo ln -s /usr/lib32/libbibutils.so.0 /usr/lib32/libbibutils.so
```

And hopefully that is all 32bit dependencies covered (at least, I get no errors on output when running acroread through the terminal).

Regards
Iain

---

### Post by khon on 2009-04-02
I have Installed AdobeReader 9.1 downloaded Deb file and auto inst with  Package Inst

---

### Post by ahmad noor on 2010-02-16
can I use A.Reader 9.1 with ubuntu 9.1 
my computer is lab.Fujtsu Siemens-Esprimo mobile

---

### Post by ahmad noor on 2010-02-16
Sorry, I think it will be better to submit my congratulations befor my previous Question .. thanks in advance..

---

