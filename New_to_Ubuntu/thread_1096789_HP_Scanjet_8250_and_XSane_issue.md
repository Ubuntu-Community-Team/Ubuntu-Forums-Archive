---
title: "HP Scanjet 8250 and XSane issue"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-15
Xsane is just shutting itself down after I click "scan". It recognizes the scanner, because the scanner sounds like it's getting ready to scan, but then the program just closes out. The 1st time I tried Xsane it actually restarted my computer. I usually scan to a PDF document.

Thanks,

JS

---

### Post by rburkartjo on 2009-03-15
js, did you have it set the the correct device when you scanned. note i have tow options and have to manually set it to my deskjet 4110 printer. works fine for me

---

### Post by js@lloyd on 2009-03-15
> **rburkartjo said:**
> js, did you have it set the the correct device when you scanned. note i have tow options and have to manually set it to my deskjet 4110 printer. works fine for me

Yes, I selected the HP device.  It starts to communicate with the scanner, as it it starts the initial process, but then the program just closes.

---

### Post by rburkartjo on 2009-03-15
js, sorry my advise didnt help. some more ideas make sure you have the lastest version of xsane installed. you could also try uninstalling xsane and reinstalling and could do with the printer (system/adm/printing). good luck.there are also two other scanner program you could try scanner utility or skanlite avail from app/ add/remove just do a search

---

### Post by dje on 2009-03-15
please run xsane from the terminal:
```
xsane
```
and post the output here (if any)

you may also wish to try quiteinsane which is another graphical frontend to sane:
```
sudo apt-get install quiteinsane
```

you may also try installing the latest version of hplip which may provide better support for your scanner: [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

dje

---

### Post by js@lloyd on 2009-03-15
> **dje said:**
> please run xsane from the terminal:
```
xsane
```
and post the output here (if any)

you may also wish to try quiteinsane which is another graphical frontend to sane:
```
sudo apt-get install quiteinsane
```

you may also try installing the latest version of hplip which may provide better support for your scanner: [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

dje

This was the output from last week.
(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:632: Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

I had to pull my home office apart, as I have some new flooring going in tomorrow.  I'll try the quiteinsane tomorrow night when I put it all back together.

---

