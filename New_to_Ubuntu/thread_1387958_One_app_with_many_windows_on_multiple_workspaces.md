---
title: "One app with many windows on multiple workspaces"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by jripple on 2010-01-22
I use a trading platform with a lot of windows which I spread over several workspaces.  However, when I open the application, all the windows are on the first workspace and I have to move them to the workspace where they belong.

On another post I saw an example of creating a script that specified which workspace an application was opened to.

Can anyone suggest how to open an application and specify which workspace it's various windows should open to?

---

### Post by jbruced on 2010-01-22
I use devilspie to manipulate certain windows and applications.

Get devilspie and gdevilspie(easy gui to automatically manipulate windows in various ways)

Hope it works for you as well.

GL
Bruce

---

### Post by jripple on 2010-01-25
Thanks jbruced,

It sounds exactly like what I need -hopefully.  The application in question doesn't allow for unique window names, at least in the titlebar.  I'm hoping devilspie can work around that somehow.

Having a "devil" of a time getting all the stuff installed that devilspie needs.  System crashed and wound up with tty access only -am in the process of getting past that.

If there's a fast way to get through pre-setting up devilspie I'd sure like to hear about it.

:)

---

### Post by jbruced on 2010-01-26
> **jripple said:**
> Thanks jbruced,

It sounds exactly like what I need -hopefully.  The application in question doesn't allow for unique window names, at least in the titlebar.  I'm hoping devilspie can work around that somehow.

Having a "devil" of a time getting all the stuff installed that devilspie needs.  System crashed and wound up with tty access only -am in the process of getting past that.

If there's a fast way to get through pre-setting up devilspie I'd sure like to hear about it.

:)

My pleasure.
The gui did what I needed, any specifics to your situation?
I'll try to help if I can.

Bruce

---

### Post by jripple on 2010-01-27
[SIZE=2]> My pleasure.  The gui did what I needed, any specifics to your situation?  I'll try to help if I can.
[/SIZE][FONT=Arial][SIZE=1][SIZE=2]Here's what I did to install devilspie: [/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=1][SIZE=2]according to the instructions[/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=1][SIZE=2] went to the directory containing the package's source code and typed ./configure.  A bunch of thing were checked and then this:

------
No package 'glib-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables WNCK_CFLAGS
and WNCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
------

It was while trying to remedy the above that I fell upon hard times which in the end required reinstalling ubuntu. It's in the hopes of not repeating that scenario that I'm looking for an easier way.   Each of the above mentioned missing packages seems to also require various packages, on and on  -just too much for my limited ubuntu abilities right now.

Suggestions appreciated.

Thanks,
J.[/SIZE]  
 [/SIZE][/FONT]

---

### Post by Mornedhel on 2010-01-27
devilspie is available in the repositories, so a simple "sudo apt-get install devilspie" should do the trick.

In case you are not familiar with APT (the preferred way of installing software in Ubuntu), a general tip is to always check the repositories first for what is available there. Installation through the repositories takes care of downloading, unpacking, and installing the software *as well as its dependencies*. See the Software Center for a simple GUI, or the Synaptic Package Manager for something a bit more hands-on. The apt-get command above does the same thing.

Unfortunately, gdevilspie is not in the repositories, but according to the [Google Code page](http://code.google.com/p/gdevilspie/), running it does not require installation.

---

