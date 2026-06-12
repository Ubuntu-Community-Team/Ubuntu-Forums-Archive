---
title: "apt-get moo problems"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by BslBryan on 2009-04-08
This may sound pretty stupid, but I was a little unhappy with the way the cow looked when I typed ```
apt-get moo
``` so I decided to run this code in my terminal:
```
$ sudo su -
[passwd]
# dpkg-divert --divert /usr/bin/apt-get.real --rename /usr/bin/apt-get
# cat > /usr/bin/apt-get
#!/bin/sh
#
if [ "$1" = "moo" ]
then
 /usr/bin/apt-get.real moo | sed -e 's/-\\\//(__)/'
else
 /usr/bin/apt-get.real $@
fi
^d
# chmod +x /usr/bin/apt-get
# exit
```

Unfortunately, it never could process the cat command.  You see, the code basically says that if I type ```
apt-get.real moo
``` it would show my new cow, but for anything else, such as package manager, I would just type ```
apt-get package
``` Since it never processed the whole code, however, I now have to type in ```
apt-get.real package
``` which really annoys the heck out of me!  To add to this, I never got to redesign my Super Cow!  :p  I tried ```
dpkg-divert --divert /usr/bin/apt-get --rename /usr/bin/apt-get.real
``` but it clashed with the previous like command.  When I get this resolved, I'm sticking with the regular cow.  :-)  Any suggestions?

---

### Post by BslBryan on 2009-04-08
oops.

---

### Post by BslBryan on 2009-04-09
oops.

---

### Post by overdrank on 2009-04-09
Please do not create multiple threads on the same issue, also please do not bump so quickly as once a 24 hr is enough. Threads merged

---

### Post by ibuclaw on 2009-04-09
It works fine for me.
I don't think you are using apt-get properly...

try
```
sudo apt-get install build-essential
```
You don't need to accept the installation of it, of course ;)

Regards
Iain

---

### Post by juancarlospaco on 2009-04-09
*There's a Bug on Moo ?*

---

### Post by ibuclaw on 2009-04-09
> **juancarlospaco said:**
> *There's a Bug on Moo ?*

Patched!
```

diff -Naur apt-0.7.14ubuntu6/cmdline/apt-get.cc apt-0.7.14ubuntu6-moo/cmdline/apt-get.cc
--- apt-0.7.14ubuntu6/cmdline/apt-get.cc	2008-08-06 13:00:25.000000000 +0100
+++ apt-0.7.14ubuntu6-moo/cmdline/apt-get.cc	2009-04-09 16:21:42.000000000 +0100
@@ -2583,7 +2583,7 @@
    cout << 
       "         (__) \n"
       "         (oo) \n"
-      "   /------\\/ \n"
+      "   /-----(__) \n"
       "  / |    ||   \n" 
       " *  /\\---/\\ \n"
       "    ~~   ~~   \n"

```

:)

---

### Post by BslBryan on 2009-04-09
> **overdrank said:**
> Please do not create multiple threads on the same issue, also please do not bump so quickly as once a 24 hr is enough. Threads merged

Apologies, but I had a rather slow internet connection, so it double posted on its own.  I'm familiar with forum etiquette. ):P  Anyway, it wasn't a bug...  Necessarily. :p  Basically, as I said, I attempted a redesign of the cow, which was poorly written on my part as it did not work with Hardy.  I do not think, however, that you have an understanding of my problem.  What I've done is completely clear the meaning of apt-get.  I've created an executable file that replaces apt-get called apt-get.real.  It's the exact same thing, but now I have to type in apt-get.real install audacity, or whatever it is that I am attempting to fetch and install.  The code I'd written was meant only to provide a variable cow design, so I could type apt-get moo and produce the original cow or apt-get.real moo and produce my new cow.  It was only a silly joke, and in executing it, I've replaced apt-get.  I'm only asking here how exactly I can recover apt-get.  APT-GET IS NO LONGER A WORKING EXECUTABLE.  Please, understand this.  :-)  Apt-get, effectively, has been replaced with a file that I'VE CREATED.  apt-get.real.  I'm not using apt-get incorrectly.  Please do not flame, bash, or respond with things that you do not understand, as I do not have the time for that.  I appreciate help, friendly comments, and humor, though. :p  Anyway, now that I've hopefully made everything clearer, any suggestions?

---

### Post by BslBryan on 2009-04-10
Finally solved!  :-) One bad line in workaround. :-)

---

