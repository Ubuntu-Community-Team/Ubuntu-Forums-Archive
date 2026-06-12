---
title: "installing pidgin plugin...."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ninja senses on 2009-01-19
I am trying to install this plug-in:  [http://bla.thera.be/archives/20](http://bla.thera.be/archives/20) . 

-I placed the .tar in my home folder and unzipped.
-changed to the directory of unzipped folder

```
./configure

```

bash: ./configure: No such file or directory


```
make

```

```
ackage pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc  -fPIC -c logstatus.c -o logstatus.o   -DHAVE_CONFIG_H
logstatus.c:18:18: error: glib.h: No such file or directory
logstatus.c:22:28: error: glib/gi18n-lib.h: No such file or directory
logstatus.c:24:36: error: libpurple/conversation.h: No such file or directory
logstatus.c:25:31: error: libpurple/signals.h: No such file or directory
logstatus.c:27:30: error: libpurple/plugin.h: No such file or directory
logstatus.c:28:31: error: libpurple/version.h: No such file or directory
logstatus.c:33: error: expected ‘)’ before ‘*’ token
logstatus.c:66: error: expected ‘)’ before ‘*’ token
logstatus.c:105: error: expected ‘)’ before ‘*’ token
logstatus.c:114: error: expected ‘)’ before ‘*’ token
logstatus.c:125: error: expected ‘)’ before ‘*’ token
logstatus.c:131: error: expected ‘)’ before ‘*’ token
logstatus.c:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
logstatus.c:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘prefs_info’
logstatus.c:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
logstatus.c:202: error: expected ‘)’ before ‘*’ token
logstatus.c: In function ‘PURPLE_INIT_PLUGIN’:
logstatus.c:207: error: expected ‘{’ at end of input
make: *** [logstatus.o] Error 1
```


I also tried extracting in the pidgin folder and trying make, still no luck, can someone help?

Im on hardy heron and running Pidgin 2.5.2

gracias

---

### Post by yeats on 2009-01-19
have you tried to see what directories ARE in the pkg-config search path?

try

```
echo $PKG_CONFIG_PATH
```

and then see if those programs are in that directory

---

### Post by kevdog on 2009-01-20
I tried installing the plugin -- no success.

You just do a make (and not ./configure).  Then its 
sudo make install.

But I can't get the plugin listed in the plugin list--Wierd!

---

### Post by jrusso2 on 2009-01-20
You will need the source of the version of pidgin your using if you want to compile the plugin.  At least that's what I had to do.  Unless you find it binary.

---

### Post by kevdog on 2009-01-20
I got it installed --

Its simply

make 
sudo make install

I'm writing up a how to for this as we speak.

---

### Post by ninja senses on 2009-01-21
> **kevdog said:**
> I got it installed --

Its simply

make 
sudo make install

I'm writing up a how to for this as we speak.

come back and post the link when your done, im sure other people will find it helpful also...gracias hombre@!!:D

ps what dir did you unzip to and what dir did you install too?

---

### Post by kevdog on 2009-01-23
Here is the link (your specific plugin is about halfway down in the plugin section): [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by ninja senses on 2009-01-28
> **kevdog said:**
> Here is the link (your specific plugin is about halfway down in the plugin section): [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

I still cant get it working....Im not really sure what directory I should be installing too, your walkthrough says cd /~src.  Now i dont know if that means the actual src directory or the source of where pidgin is or what.  I am still getting the same errors as before

---

### Post by kevdog on 2009-01-29
cd ~/src can be any directory.  (That is where I put all the sources I am going to compile)

What errors are you getting?

---

### Post by ninja senses on 2009-01-31
> **kevdog said:**
> cd ~/src can be any directory.  (That is where I put all the sources I am going to compile)

What errors are you getting?

still the exact same as i first posted

---

### Post by kevdog on 2009-01-31
Did you compile pidgin from source or are you just trying to compile the plugin only?  By your error message, it states something about missing gtk-2.0 which implies you are missing some dependency libraries.  Im just wondering if you re-consult this thread:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

and install the name dependencies mentioned at the top of the thread, if this error disappears?

---

### Post by ninja senses on 2009-01-31
> **kevdog said:**
> Did you compile pidgin from source or are you just trying to compile the plugin only?  By your error message, it states something about missing gtk-2.0 which implies you are missing some dependency libraries.  Im just wondering if you re-consult this thread:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

and install the name dependencies mentioned at the top of the thread, if this error disappears?

I walked through step by step and this is the errors im getting
```
Fetched 25.6MB in 38s (662kB/s)                                                
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-dev_2.22.3-0ubuntu2_i386.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-dev_2.22.3-0ubuntu2_i386.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-dev_2.22.3-0ubuntu2_i386.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-dev_2.22.3-0ubuntu2_i386.deb  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
E: Failed to process build dependencies
```

```
configure: error: The intltool scripts were not found. Please install intltool.
 make
make: *** No targets specified and no makefile found.  Stop.
```

```
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc  -fPIC -c logstatus.c -o logstatus.o   -DHAVE_CONFIG_H
logstatus.c:18:18: error: glib.h: No such file or directory
logstatus.c:22:28: error: glib/gi18n-lib.h: No such file or directory
logstatus.c:24:36: error: libpurple/conversation.h: No such file or directory
logstatus.c:25:31: error: libpurple/signals.h: No such file or directory
logstatus.c:27:30: error: libpurple/plugin.h: No such file or directory
logstatus.c:28:31: error: libpurple/version.h: No such file or directory
logstatus.c:33: error: expected ‘)’ before ‘*’ token
logstatus.c:66: error: expected ‘)’ before ‘*’ token
logstatus.c:105: error: expected ‘)’ before ‘*’ token
logstatus.c:114: error: expected ‘)’ before ‘*’ token
logstatus.c:125: error: expected ‘)’ before ‘*’ token
logstatus.c:131: error: expected ‘)’ before ‘*’ token
logstatus.c:137: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘plugin_load’
logstatus.c:152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘prefs_info’
logstatus.c:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘info’
logstatus.c:202: error: expected ‘)’ before ‘*’ token
logstatus.c: In function ‘PURPLE_INIT_PLUGIN’:
logstatus.c:207: error: expected ‘{’ at end of input
make: *** [logstatus.o] Error 1

```

---

