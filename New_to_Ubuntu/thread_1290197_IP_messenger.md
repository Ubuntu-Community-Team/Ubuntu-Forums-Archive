---
title: "IP messenger"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by bindu arya on 2009-10-13
How to install IP messenger?
Please help me..

---

### Post by s.fox on 2009-10-13
Hello,

Do you mean to use instant messaging protocols like MSN, Yahoo or AIM? If that is the case you can use Pidgin which comes with gnome by default.  :)

Hope this helps,

-Silver Fox

---

### Post by wobin77 on 2009-10-13
[http://www.ipmsg.org/index.html.en](http://www.ipmsg.org/index.html.en)

There s a download link to the tar.gz files

---

### Post by mimor on 2009-10-13
Mail them. There is an email adress if you scroll down

---

### Post by 3rdalbum on 2009-10-13
You need to compile it from source code. If you've only been using Ubuntu since last month, this might be very alien to you. If you can live without IP Messenger until you've found your feet a little better, then do it. Maybe get your friends to switch to something a little more mainstream. Something you can use with Pidgin.

Anyway, to compile software you need the "build-essential" package from Synaptic. Uncompress the archive and put it somewhere you can find it.

Open up a terminal and change to the directory containing the source code; you do this by typing "cd " (without the quotes and with the space at the end) and then dragging the folder icon onto the terminal, and running the result.

Now type:

```
./configure
```

Pretty soon you'll get a message on screen that you're missing a required library. It's then up to you to go into Synaptic Package Manager and download it. You need the "development headers"; these are special packages that tell the compiler how to link the real libraries to the new program you're compiling. The packages usually end with "-dev". When you have found and installed the development library that the configure script complained about, run:

```
./configure
```

again. Repeat the process until the script finishes with no errors.

Then type:

```
make
sudo make install
```

This compiles and installs the software.

I think you have to run it initially from the terminal, and it puts an icon into your notification area.

I did once build a Debian package for it, but apparently the package didn't work, which is why I'm not providing you with it. I never tested it properly apart from running it; I don't know anyone who uses IP Messenger.

Note that this is old software and it might not work on today's Linux systems!

---

