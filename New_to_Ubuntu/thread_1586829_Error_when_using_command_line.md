---
title: "Error when using command line"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by thorbs on 2010-10-02
Hi I get the following error when I use commandline

[B](process:5042): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.



Any suggestions?


thanks.

---

### Post by Hippytaff on 2010-10-02
[http://community.activestate.com/forum/if-you-receive-error-gtk-warning-locale-not-supported-c-library](http://community.activestate.com/forum/if-you-receive-error-gtk-warning-locale-not-supported-c-library)

might be worth a look

---

### Post by thorbs on 2010-10-03
I tried the solution in that:


/usr/lib/locale
sudo ln -s en_GB.utf8 en_GB


I replaced english with en_DK.utf8 en_DK   and also just dk_DK.UTF-8 as suggest in the terminal respons,

but non of them worked.


Could it be the issue with resipotory, not sure which one I am supposed to align with situated in Denmark and how.

---

