---
title: "Firefox Shutting Immediately After Opening"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by muzzmackay on 2009-01-22
Strange wee annoying problem on Ubuntu 8.10 AMD64.

Frequently but not at all times when opening firefox and just about to google, firefox closes.

No error messages.

---

### Post by Michael.Godawski on 2009-01-22
Hi,

and if you open firefox with the terminal? still no error messages?

```
firefox
```

---

### Post by muzzmackay on 2009-01-22
Took me a few tried to get it to shut by itself, I thought it had decided to start working :p

Here's the response in the terminal:

ERROR: ld.so: object '/usr/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ICEDTEAPLUGIN_DEBUG = (null)
ERROR: ld.so: object '/usr/$LIB/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:10293): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:10293): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
*** NSPlugin Wrapper *** ERROR: passing an unknown instance
*** NSPlugin Wrapper *** ERROR: passing an unknown instance
*** NSPlugin Viewer  *** ERROR: NPN_PopPopupsEnabledState() wait for reply: Connection closed
Segmentation fault

Hope you can make sense of it.

---

### Post by stderr on 2009-01-22
It looks like it *may* be your Java plugin. I had a similar thing whereby if Firefox closed when a tab with the Runescape Java interface was still open, it would crash shortly after opening. I am using sun-java6-plugin, though.

Do you have any such tabs open with Java applets when the crashes occur?

---

### Post by muzzmackay on 2009-01-22
> **stderr said:**
> Do you have any such tabs open with Java applets when the crashes occur?

I'm not sure what applets are running when I close down. Can I remove the IcedTea plugin and try another ?

---

