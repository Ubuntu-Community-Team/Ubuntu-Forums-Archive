---
title: "How to determine where apps are started from?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by lofttroy on 2009-02-19
I'm very new to Ubuntu and Google hasn't answered my prayers.

How do I find out where an application is started from when I log on?  Specifically I'm looking for the start command for X11vnc so that I can change the port that it listens on.  Here's basic list of what I know (it's short).

x11vnc is not running when the logon screen is displayed.
There are no hidden files in my home directory that seem to relate to this program.
I suspect that I need to find something under /etc/rc??????

Thanks for the help.

Troy

---

### Post by perlluver on 2009-02-19
You could do it like this ```
find / -name x11vnc
```

---

### Post by bodhi.zazen on 2009-02-19
or 

```
which x11vnc
```

---

### Post by krunge on 2009-02-19
> **lofttroy said:**
> 
How do I find out where an application is started from when I log on?  Specifically I'm looking for the start command for X11vnc so that I can change the port that it listens on.  Here's basic list of what I know (it's short).

x11vnc is not running when the logon screen is displayed.
There are no hidden files in my home directory that seem to relate to this program.
I suspect that I need to find something under /etc/rc??????


My guess it is an Xsetup script.  Look for these sorts of files:

```

     GDM (GNOME)  /etc/X11/gdm/Init/Default    (or sometimes Init/:0)
                  /etc/gdm/Init/Default
     KDM (KDE)    /etc/kde*/kdm/Xsetup
     XDM          /etc/X11/xdm/Xsetup          (or sometimes xdm/Xsetup_0)

```

or whatever your distro has renamed them to or whereever your distro moved them to. The locate(1) command may come in handy in finding these files. (more info: [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager))
Or maybe an X startup script.

So look in the script files of that sort for any "x11vnc" being started and report back here what you find.

If you find it in a file of that sort **PLEASE** post what you find.  There are a number of posts in these forums asking the same thing about how mythbuntu starts x11vnc.

---

### Post by krunge on 2009-02-19
> **krunge said:**
> 
If you find it in a file of that sort **PLEASE** post what you find.  There are a number of posts in these forums asking the same thing about how mythbuntu starts x11vnc.

Oh, in case you don't understand what I mean or how to find files like this on your system this may help:

```

grep -r x11vnc /etc

```
as root.

---

### Post by gackt on 2009-02-20
will this help?

System > Administration > system

try to modify the x11vnc parameter.

---

### Post by lofttroy on 2009-02-20
I finally found it!

Many thanks to krunge.  This was the trick.  To everyone else, your ideas worked, but weren't quite what I was looking for.

The file that sets the configuration of x11vnc on my machine is located in
```
/usr/share/mythbuntu/session.sh
```

In case it's different depending on hardware here's  a brief synopsis:
AMD Operton 2347HE
Tyan h1000E 3970 series board
16GB RAM
pc HDTV HD-5500 reciever card

Thanks again!

Until I break it again / can't figure it out.

---

### Post by krunge on 2009-02-20
> **lofttroy said:**
> I finally found it!

The file that sets the configuration of x11vnc on my machine is located in
```
/usr/share/mythbuntu/session.sh
```


Great, glad you found it and reported the result!  This will help people searching for this answer.

One more thing, could please paste into another post the lines in that file that are related to x11vnc?  Thanks again.

---

