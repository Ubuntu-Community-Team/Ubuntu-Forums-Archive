---
title: "'make' command won't go thru, 'no makefile found'"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by leavitodeaver on 2010-08-13
is the error msg i get when trying to install gfm, an apparently necessary package for tilp2, calculator<->pc program.  i looked in the directory, i see makefile.am and makefile.in, i assume one of these is what it's looking for. i already configured and cd'd the directory, and got this;
checking for TICONV... configure: error: Package requirements (ticonv >= 1.0.4) were not met:

No package 'ticonv' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables TICONV_CFLAGS
and TICONV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jason@jason-desktop:~/Desktop/gfm-1.04$ make
make: *** No targets specified and no makefile found.  Stop.

helps?

---

### Post by Paul820 on 2010-08-13
Look in synaptics for > libticonv-dev
It won't make a makefile until all dependencies are met. Look in the readme file to see what is required to build the package.

---

### Post by Zeike on 2010-08-13
The configure script exited unsuccessfully.

You will have to install the ticonv-dev package before you can continue (and any other packages the ./configure script says you require).

I think ticonv is in the repos.

---

### Post by leavitodeaver on 2010-08-13
got libticonv-dev from synaptic, now i have:

checking for TICONV... configure: error: Package requirements (ticonv >= 1.0.4) were not met:

Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glib-2.0', required by 'TiConv', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables TICONV_CFLAGS
and TICONV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

now what?
unrelated note, how do you guys quote stuff on this forum?

---

### Post by Paul820 on 2010-08-13
So now you need to install libticonv3 and libglib2.0-dev
The normal libglib2.0-0 package should be installed, when you search in synaptics for libglib it should already be checked. But if it isn't get that as well.

---

### Post by patC42 on 2010-08-13
Tilp2 is in the Synaptic package manager. Wouldn't that be an easier way to go?

---

### Post by leavitodeaver on 2010-08-13
i got tilp2 from synaptic, but it told me i needed gfm to run it.  i installed a few other packages, ticalcs2, tifiles2, etc, now it spat this out:
> checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met:

No package 'gtk+-2.0' found

there's a lot in synaptic that it could be, which one do i get? i realize i'm riding the short bus right now, bear with me please.

---

### Post by Paul820 on 2010-08-13
Did you try patC42's suggestion of installing tILP2 through synaptic? I assumed you had already searched for it there.

---

### Post by leavitodeaver on 2010-08-13
i have indeed, and originally installed it from synaptic.  i'm only doing all this because while playing with it, i clicked some option, and an error msg popped up that said go to whatever site and install gfm, which turned into me beating my head on the desk in frustration.

---

### Post by Paul820 on 2010-08-13
Whenever it says > No package 'gtk+-2.0' found then look at the package between the quotes, in this case it's 'gtk+-2.0'. So you need to find the development headers for that. So in synaptics search for libgtk and get the libgtk2.0-dev.

---

### Post by Paul820 on 2010-08-13
Erm...gfm is also in synaptics

---

### Post by leavitodeaver on 2010-08-13
ok, got all the packages i need, got thru 'make' command, 'make install' brought this on:
> make[2]: Entering directory `/home/jason/Desktop/gfm-1.04/glade'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gfm/glade" || /bin/mkdir -p "/usr/local/share/gfm/glade"
/bin/mkdir: cannot create directory `/usr/local/share/gfm': Permission denied
make[2]: *** [install-dist_gladeDATA] Error 1
make[2]: Leaving directory `/home/jason/Desktop/gfm-1.04/glade'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jason/Desktop/gfm-1.04/glade'
make: *** [install-recursive] Error 1

am i done?

---

### Post by 0004tom on 2010-08-13
No you need to run make install as root.

sudo make install

---

### Post by Paul820 on 2010-08-13
> sudo make install
Then enter your password. It needs to be root.

---

### Post by leavitodeaver on 2010-08-13
gotcha.  did that, now it's 
> make[2]: Leaving directory `/home/jason/Desktop/gfm-1.04/man'
make[1]: Leaving directory `/home/jason/Desktop/gfm-1.04/man'
make[1]: Entering directory `/home/jason/Desktop/gfm-1.04'
make[2]: Entering directory `/home/jason/Desktop/gfm-1.04'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jason/Desktop/gfm-1.04'
make[1]: Leaving directory `/home/jason/Desktop/gfm-1.04'

now i'm done?  hopefully?

---

### Post by Paul820 on 2010-08-13
Yes, all done. :D

---

### Post by leavitodeaver on 2010-08-13
beautiful.  thanks to all of you, this forum is full of the most helpful people i've ever met.  keep up the good work

---

### Post by klEEh on 2010-08-20
> **Paul820 said:**
> 
Look in synaptics for      Quote:
                                                 libticonv-dev                      

Look in synaptics for 
It won't make a makefile until all dependencies are met. Look in the readme file to see what is required to build the package.

U are a heeeero!:KS

---

