---
title: "dual monitors / no xorg.conf"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by mf205 on 2010-05-31
I'm running 64-bit Lucid on a Dell Inspiron laptop, and I have an LG monitor sitting next to it.  I'd like to have a dual set-up, and it seems from reading the forums that twinview is what I need.  However, all the posts that tell me how to get twinview going tell me early on to edit /etc/X11/xorg.conf.  But there is no file xorg.conf anywhere on my system.

The contents of my /etc/X11/ are:

app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

I can't find this problem on any other thread.  Any ideas?

---

### Post by Bob Bertrands on 2010-05-31
Can you please post the output of 
```
lshw -C display
```

B

---

### Post by mf205 on 2010-05-31
> Can you please post the output of 
     Code:
     lshw -C display 
Thanks for the reply, Bob.  Here it is:

matt@matt-laptop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff

---

### Post by Bob Bertrands on 2010-05-31
please run:

```
sudo Xorg -configure
```

This will create a xorg.conf file. 
But you will need the output of lswh -C display and lspci to correctly setup your xorg.conf file

---

### Post by Bob Bertrands on 2010-05-31
Better option:

Follow the instructions on this site

[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

Good luck

B

---

### Post by mf205 on 2010-05-31
Thanks for the help.  When I run

Code:
 	sudo Xorg -configure 
I get:
[INDENT]
Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running
[/INDENT]

---

### Post by saakeman on 2010-05-31
go to display settings 
 * say detect monitors and maybe it will show it 
  * config it to your personal style :) 

---------------------**
**joins facebook's dustbin of history**
THATS 
** dustbin of history***

---

### Post by saakeman on 2010-05-31
> **saakeman said:**
> go to display settings 
 * say detect monitors and maybe it will show it 
  * config it to your personal style :) 

---------------------**
**joins facebook's dustbin of history**
THATS 
** dustbin of history***

thats how i did it and it worked fine ! :)

---

### Post by quadproc on 2010-05-31
> **mf205 said:**
> I'm running 64-bit Lucid on a Dell Inspiron laptop, and I have an LG monitor sitting next to it.  I'd like to have a dual set-up, and it seems from reading the forums that twinview is what I need.  However, all the posts that tell me how to get twinview going tell me early on to edit /etc/X11/xorg.conf.  But there is no file xorg.conf anywhere on my system.

The xorg.conf file is now optional.  Later releases of Ubuntu will honor an xorg.conf file if it exists but if it is not present then they will look at your hardware and attempt to do what makes sense.  If the file exists it will be located in /etc/X11.

You cab put lots of things into an xorg.conf file but personally I prefer to keep it as simple as I can.  I did learn the hard way that early versions of X windows did not know how to deal with multiple graphics cards or subsystems; I had to supply a BusID for my primary graphics card so that X could figure out where to send its ordinary output.

quadproc

---

