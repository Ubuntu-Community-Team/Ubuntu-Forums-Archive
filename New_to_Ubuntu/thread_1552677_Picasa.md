---
title: "Picasa"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Segofam on 2010-08-14
After installing Picasa for Linux, I get 
scott@scott-laptop:~$ /opt/picasa/bin/picasa
/opt/picasa/bin/picasa: line 139:  5944 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/opt/picasa/bin/picasa: line 175:  6047 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
scott@scott-laptop:~$  /usr/bin/picasa
/usr/bin/picasa: line 139:  6269 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  6372 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
scott@scott-laptop:~$ picasa
/usr/bin/picasa: line 139:  6594 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so

and it won't run!

Any helpful suggestions would be much appreciated!

Regards,

Scott

---

### Post by wojox on 2010-08-14
You downloaded it for Linux [picasa]("http://picasa.google.com/linux/") ? That looks like Windows.

---

### Post by Segofam on 2010-08-14
> **wojox said:**
> You downloaded it for Linux [picasa]("http://picasa.google.com/linux/") ? That looks like Windows.

Your link is where I got it from. I will uninstall it and try again.

---

### Post by Segofam on 2010-08-14
This was my download link [SIZE=-1][Free Download (.deb)             - for Debian/Ubuntu x86 (32-bit)]("http://picasa.google.com/linux/thanks-deb.html")

So I would be downloading the same again!
[/SIZE]

---

### Post by wojox on 2010-08-14
> **Segofam said:**
> This was my download link [SIZE=-1][Free Download (.deb)             - for Debian/Ubuntu x86 (32-bit)]("http://picasa.google.com/linux/thanks-deb.html")

So I would be downloading the same again!
[/SIZE]

Yeah. It even comes packaged in a .deb

Don't know what the problem would be. 

You are running 32 bit Ubuntu correct?

---

### Post by wojox on 2010-08-14
Uninstall yours and try my link. Yours is 2.7 while mine is 3.0 so may work better.

---

### Post by Segofam on 2010-08-14
Yep, I am running 32 bit.

---

### Post by Segofam on 2010-08-14
> **wojox said:**
> Uninstall yours and try my link. Yours is 2.7 while mine is 3.0 so may work better.

Ok, let me uninstall and try yours, I am not quick at this so grab a coffee..and bickies ;-)

---

### Post by Segofam on 2010-08-14
Ok, I am on this page...
[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30) 
and half way down I am think of downloading this link...
[SIZE=-1][http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)[/SIZE]
Is that the right one?

---

### Post by wojox on 2010-08-14
> **Segofam said:**
> Ok, I am on this page...
[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30) 
and half way down I am think of downloading this link...
[SIZE=-1][http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb)[/SIZE]
Is that the right one?

That's the one. ;)

---

### Post by Segofam on 2010-08-14
Thank you wojox, it is up and running :)

Have a great day!

Kind regards,

Scott

---

### Post by wojox on 2010-08-14
Your Welcome :)

---

