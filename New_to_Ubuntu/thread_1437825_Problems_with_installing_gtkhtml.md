---
title: "Problems with installing gtkhtml"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Turibur on 2010-03-24
Hi,

Im quite new to these forums and an absolute beginner at ubuntu so i hope im making this right now. 

Ive been having some trouble connecting to my exchange 2007 server with evolution even with evolution-mapi installed. (I got an mapi login error).

So i tried to follow [this guide ]("http://gurrier.wordpress.com/2009/12/11/installing-evolution-2-29-3-with-mapi-plugin-under-ubuntu-9-10-karmic/")and hopefully get it working. The problem is that i can run "./configure" for gtkhtml-3.29.5 without errors but when i try to run "make" i get the following errors:

object.c: In function ‘do_action’:
object.c:80: error: implicit declaration of function ‘GTK_WIDGET_SENSITIVE’
object.c:80: warning: nested extern declaration of ‘GTK_WIDGET_SENSITIVE’
object.c:80: error: implicit declaration of function ‘GTK_WIDGET_VISIBLE’
object.c:80: warning: nested extern declaration of ‘GTK_WIDGET_VISIBLE’
make[2]: *** [object.lo] Error 1
make[2]: Leaving directory `/home/david/evolution/gtkhtml-3.29.5/a11y'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/evolution/gtkhtml-3.29.5'
make: *** [all] Error 2

I first thought that i was missing a library or something similar and looked for GTK+ in synaptic but to my suprise i already had the latest version. I'd be very grateful for any assistance :)

---

### Post by Turibur on 2010-03-25
Bump.

Ive tried to install gtk+-2.20.0 and gtk+2.9.4 manually without any luck except that the error message has changed a bit.

make[3]: Entering directory `/home/david/evolution/gtkhtml-3.29.92/components/editor'
make  all-am
make[4]: Entering directory `/home/david/evolution/gtkhtml-3.29.92/components/editor'
  CC     gtkhtml-color-combo.lo
gtkhtml-color-combo.c: In function ‘color_combo_default_release_event_cb’:
gtkhtml-color-combo.c:325: error: implicit declaration of function ‘GTK_WIDGET_STATE’
gtkhtml-color-combo.c:325: warning: nested extern declaration of ‘GTK_WIDGET_STATE’
make[4]: *** [gtkhtml-color-combo.lo] Error 1
make[4]: Leaving directory `/home/david/evolution/gtkhtml-3.29.92/components/editor'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/david/evolution/gtkhtml-3.29.92/components/editor'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/david/evolution/gtkhtml-3.29.92/components'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/evolution/gtkhtml-3.29.92'
make: *** [all] Error 2

---

