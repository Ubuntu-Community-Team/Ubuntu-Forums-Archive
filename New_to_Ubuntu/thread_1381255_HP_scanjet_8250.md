---
title: "HP scanjet 8250"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by rev9ers on 2010-01-14
Greetings all. I'm pretty new to linux and Ubuntu. I have purchased a Hewlett Packard ScanJet 8250 scanner and am having trouble configuring it so that the ADF works. When I run xsane from the terminal I get the following output:

anthony@anthony-desktop:~$ xsane
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:32524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

The scanner scans individual documents from the flatbed quite well, but the ADF functionality is the main reason I purchased the scanner. When I searched the forums, I found answers to similar posts, but no solutions to this particular problem.

Could someone help me resolve this issue? This scanner is supported by the Avision backend according to the xsane project. Is there a way to work with the backend so that the ADF will work. Is anyone aware on any workarounds?

I have only 30 days (27 actually, after 3 days of tinkering with it) before I cannot return the scanner for a different one.

Cheers

---

### Post by steve-shinn on 2010-01-14
Have you installed the HP drivers for Linux ?

---

### Post by rev9ers on 2010-01-14
I was under the impression that all I needed was the sane and xsane stuff. So, no I have not installed hp specific drivers for linux. Are they availabe at the hp website?

---

### Post by sandyd on 2010-01-14
-> HPLIP
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by steve-shinn on 2010-01-14
> **rev9ers said:**
> I was under the impression that all I needed was the sane and xsane stuff. So, no I have not installed hp specific drivers for linux. Are they availabe at the hp website?

Not sure but you could try the SANE/Avision backend :-

[http://www.exactcode.de/site/open_source/saneavision/](http://www.exactcode.de/site/open_source/saneavision/)

---

### Post by Sef on 2010-01-14
Once plugged in, what do you get when you go here:  Applications > Graphics > XSane?  If you get an error message, please post it.

---

### Post by rev9ers on 2010-01-14
> **carlee said:**
> -> HPLIP
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Unfortunately, the HP ScanJet is not supported by HPLIP according to the Hewlett Packard site.

---

### Post by rev9ers on 2010-01-14
> **Sef said:**
> Once plugged in, what do you get when you go here:  Applications > Graphics > XSane?  If you get an error message, please post it.

I do not get an error message when I plug in the scanner and it scans from the flatbed fine. However, when I change the Scan Source to "ADF Front", the scanner lcd screen displays "Error 15" and xsane just sits there reportedly "Scanning" without progressing at all.

---

### Post by rev9ers on 2010-01-14
Oh, and one more thing. After I try, and fail, to use the ADF as the document source and I stop xsane spinning its wheels by cancelling the scan, if I try to scan again, xsane displays an error which reads: "Failed to start scanner: Scanner cover is open". 

Note that the scanner cover is not open when this error message displays.

---

### Post by enigmaingr on 2010-06-09
That's the issue I have as well.  Everything else is fine except the ADF function.  Not sure how to solve it as Simple Scan is the same way.

---

### Post by DinkyDogg on 2011-04-05
I can confirm this issue still exists in Ubuntu 10.04 for this scanner.

---

