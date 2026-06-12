---
title: "Add Bitdefender Scan Option to Nautilus?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-11
I fired off an email to bitdefender a few minutes ago asking how to add a scan option to the right click menu in nautilus before realising that tomorrows Sunday and then Monday is also a bank holiday so the likelihood of me getting any kind of response before Tuesday was non existent...

so I just thought I'd ask here as well and see if anyone could help me?

---

### Post by lfaraone on 2009-04-11
Please see [http://www.techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/](http://www.techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/)

---

### Post by kamitsukai on 2009-04-11
OK tried the above and it looks like a bit of a pain... but I've discovered in the recesses of the BitDefender "Tip of the day box" that the integration files are stored in "/opt/BitDefender-scanner/share/integration" and that I have to build them from source so it requires the following packages:

    - gcc
    - GNU LibC
    - GNU Make
    - GNU Autotools
    - libgnome 2.0
    - libnautilus-extension

But my problem is what are these packages called in synaptic?

I've also included the README file below

---

### Post by binbash on 2009-04-11
I am also interested in this

---

### Post by gandaran on 2009-04-11
> **kamitsukai said:**
> OK tried the above and it looks like a bit of a pain... but I've discovered in the recesses of the BitDefender "Tip of the day box" that the integration files are stored in "/opt/BitDefender-scanner/share/integration" and that I have to build them from source so it requires the following packages:

    - gcc
    - GNU LibC
    - GNU Make
    - GNU Autotools
    - libgnome 2.0
    - libnautilus-extension

But my problem is what are these packages called in synaptic?

I've also included the README file below
well, I could never get this to work so what I use instead is nautilus actions, very simple, make the bitdefender entry (gnome-terminal -x bdscan) in nautilus actions configuration, to use right click the file  choose bitdefender from the drop-down menu, scan starts in command line terminal.

---

### Post by kamitsukai on 2009-04-11
> **gandaran said:**
> well, I could never get this to work so what I use instead is nautilus actions, very simple, make the bitdefender entry (gnome-terminal -x bdscan) in nautilus actions configuration, to use right click the file  choose bitdefender from the drop-down menu, scan starts in command line terminal.

Ok done that but the Icon doesn't show up and I'm not sure if it's actually working? I see a quick flash of terminal across the taskbar but that's it..

PS: I'd still Like to do it the other way if anyone knows about the package names?

---

### Post by gandaran on 2009-04-11
> **kamitsukai said:**
> Ok done that but the Icon doesn't show up and I'm not sure if it's actually working? I see a quick flash of terminal across the taskbar but that's it..

PS: I'd still Like to do it the other way if anyone knows about the package names?
you have to set the terminal profile to stay open after executing  in terminal preferences.
and no the icon doesn't show up since ubuntu 8.04, it must be some bug that hasn't been fixed, used to work nicely in ubuntu 7.10.

---

### Post by kamitsukai on 2009-04-11
> **gandaran said:**
> you have to set the terminal profile to stay open after executing  in terminal preferences.
and no the icon doesn't show up since ubuntu 8.04, it must be some bug that hasn't been fixed, used to work nicely in ubuntu 7.10.

Brilliant thanks):P

---

### Post by kamitsukai on 2009-04-11
Oh....

it appears I just get a blank terminal =[

---

### Post by lfaraone on 2009-04-11
> **kamitsukai said:**
> OK tried the above and it looks like a bit of a pain... but I've discovered in the recesses of the BitDefender "Tip of the day box" that the integration files are stored in "/opt/BitDefender-scanner/share/integration" and that I have to build them from source so it requires the following packages:

    - gcc
    - GNU LibC
    - GNU Make
    - GNU Autotools
    - libgnome 2.0
    - libnautilus-extension
Try:
```
sudo apt-get install build-essential libgnome2-dev libnautilus-extension-dev libnautilus-extension1 
```

---

### Post by gandaran on 2009-04-12
> **kamitsukai said:**
> Oh....

it appears I just get a blank terminal =[
did you enter the right start command **[B]gnome-terminal -x bdscan**[/B]
```
sudo apt-get install build-essential libgnome2-dev libnautilus-extension-dev libnautilus-extension1
```
did this work for compiling the gnome extension?

---

### Post by kamitsukai on 2009-04-12
Nope I get the following build error...

```
config.status: creating icons/16x16/Makefile                                                                                                                         
config.status: creating icons/22x22/Makefile                                                                                                                         
config.status: creating icons/32x32/Makefile                                                                                                                         
config.status: creating icons/48x48/Makefile                                                                                                                         
config.status: creating icons/64x64/Makefile                                                                                                                         
config.status: creating icons/128x128/Makefile                                                                                                                       
config.status: executing depfiles commands                                                                                                                           
Making all in src                                                                                                                                                    
make[1]: Entering directory `/home/carl/Desktop/nautilus-bitdefender-1.0.0/src'                                                                                      
if /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"nautilus-bitdefender\" -DPACKAGE_TARNAME=\"nautilus-bitdefender\" -DPACKAGE_VERSION=\"1.0.0\" -DPACKAGE_STRING=\"nautilus-bitdefender\ 1.0.0\" -DPACKAGE_BUGREPORT=\"http://www.bitdefender.com\" -DPACKAGE=\"nautilus-bitdefender\" -DVERSION=\"1.0.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_LIBNAUTILUS_EXTENSION=1 -DHAVE_NAUTILUS_MENU_PROVIDER_EMIT_ITEMS_UPDATED_SIGNAL=1 -DLOCALEDIR=\"/usr/local//locale\"  -I. -I. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/nautilus -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT nautilus-bitdefender.lo -MD -MP -MF ".deps/nautilus-bitdefender.Tpo" \
          -c -o nautilus-bitdefender.lo `test -f 'nautilus-bitdefender.c' || echo './'`nautilus-bitdefender.c; \
        then mv ".deps/nautilus-bitdefender.Tpo" ".deps/nautilus-bitdefender.Plo"; \
        else rm -f ".deps/nautilus-bitdefender.Tpo"; exit 1; \
        fi
mkdir .libs
 gcc -DPACKAGE_NAME=\"nautilus-bitdefender\" -DPACKAGE_TARNAME=\"nautilus-bitdefender\" -DPACKAGE_VERSION=\"1.0.0\" "-DPACKAGE_STRING=\"nautilus-bitdefender 1.0.0\"" -DPACKAGE_BUGREPORT=\"http://www.bitdefender.com\" -DPACKAGE=\"nautilus-bitdefender\" -DVERSION=\"1.0.0\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1-DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_LIBNAUTILUS_EXTENSION=1 -DHAVE_NAUTILUS_MENU_PROVIDER_EMIT_ITEMS_UPDATED_SIGNAL=1 -DLOCALEDIR=\"/usr/local//locale\" -I. -I. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/nautilus -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -g-O2 -MT nautilus-bitdefender.lo -MD -MP -MF .deps/nautilus-bitdefender.Tpo -c nautilus-bitdefender.c  -fPIC -o .libs/nautilus-bitdefender.o
nautilus-bitdefender.c:274: fatal error: opening dependency file .deps/nautilus-bitdefender.Tpo: Permission denied
compilation terminated.
make[1]: *** [nautilus-bitdefender.lo] Error 1
make[1]: Leaving directory `/home/carl/Desktop/nautilus-bitdefender-1.0.0/src'
make: *** [all-recursive] Error 1
carl@carl-desktop:~/Desktop/nautilus-bitdefender-1.0.0$

```

---

### Post by kamitsukai on 2009-04-13
Anyone able to help me compile? (see above...)

---

### Post by kamitsukai on 2009-04-14
<bUMP>

---

### Post by kamitsukai on 2009-04-16
After contacting the BitDefender for Unices team via email I was very kindly sent back some instructions for how to build the extension from source which I've included below although this option for some reason didnt work for me and I was then sent a deb package installer for amd 64:D

_How to build from source (copied straight from email)_
```
prerequisites:
 1. you need root privileges for this small tutorial:

    # sudo su -
    <your-password>

    or
    # su -
    <root-password>

    or directly log in as root.

 2. you need to install the development packages for nautilus:

    # aptitude install libnautilus-extension-dev

    this package should automatically pull in the development packages for
    gnome (libgnome-dev) and GNU C library (libc-dev). If you are using a
    distribution that is not based on Debian, you might need to manually
    install some other tools (like gcc, make, autoconf, automake etc). But
    hopefully your package manager does this for you. :)

building and installing:
 1. unpack gnome.tar.gz:

    # cd /opt/BitDefender-scanner/share/integration
    # tar xjf gnome.tar.gz

 2. build the extension:

    # cd gnome/nautilus-bitdefender-1.0.0
    # ./configure --prefix=/usr && make

 3. install the extension:

    # make install

 4. log off and log back into Gnome. This is needed in order to restart
    nautilus. On some systems is enough to just tell nautilus to terminate:

    # killall nautilus

This should be it. If you encounter problems with building the extension, you
could try to regenerate the autotools scripts:

 # aclocal && autoconf && automake

If this does not help, drop us another e-mail and tell us your distribution so
we can have a look.
```

And **_AMD 64_** deb package is below

---

### Post by binbash on 2009-04-17
That is not the only dep requirement : 

checking for 	 glib-2.0 >= 2.4.0                	 libgnome-2.0 >= 2.7.0		 libnautilus-extension >= 2.8.0... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found
configure: error: Library requirements (	 glib-2.0 >= 2.4.0                	 libgnome-2.0 >= 2.7.0		 libnautilus-extension >= 2.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by au6u5t on 2009-05-13
here this is the deb package for integrating BitDefender into nautilus for intel i386 device, i just got it from BitDefender for unice Developer team. and if there is still not work fell free to contack BitDefender for unice developer team in [email]unices@bitdefender.com[/email]
i beliefe they will try to help.

---

### Post by ENigma885 on 2010-02-03
[SIZE="3"]Here are the official Nautilus-Bitdefender integration .deb packages[/SIZE]:-

[[COLOR="Blue"]ubuntu 8.04 i386[/COLOR]]("http://unices.bitdefender.com/wp-content/uploads/2009/06/ubuntu-8_04_nautilus-bitdefender_100-1_i386.deb")
[URL="http://unices.bitdefender.com/wp-content/uploads/2009/06/ubuntu-8_10-nautilus-bitdefender_100-1_amd64.deb"]
[COLOR="Blue"]ubuntu 8.10 amd64[/COLOR][/URL]

[[COLOR="Blue"]ubuntu 9.04 i386[/COLOR]]("http://unices.bitdefender.com/wp-content/uploads/2009/06/ubuntu-9_04-nautilus-bitdefender_100-1_i386.deb") 

[[COLOR="Blue"]ubuntu 9.04 amd64 ]("http://unices.bitdefender.com/wp-content/uploads/2009/06/ubuntu-9_04-nautilus-bitdefender_100-1_amd64.deb")[/COLOR]

[[COLOR="Blue"]ubuntu 9.10 i386[/COLOR]]("http://unices.bitdefender.com/wp-content/uploads/2009/06/ubuntu-9_10-nautilus-bitdefender_100-1_i386.deb")
________________

- Originally posted on [[COLOR="Blue"]Bitdefender's unices website[/COLOR]]("http://unices.bitdefender.com/2009/06/01/let-there-be-nautilus-extension-packages/")
- There's a comment field there as well where you can ask them to provide you with a specific .deb package if none of the above suits your environment.

---

