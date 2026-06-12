---
title: "print to pdf tool in ubuntu 10.04"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by darknomel on 2011-04-11
Hi all,

Does anyone know what the tool is called to allow you to print to file by default in Ubuntu 10.04?

I'm trying to circumvent this and print directly to the installed cups printer by default. I want to try remove tis tool and see if that works.

Thanks!

---

### Post by Nickjpost on 2011-04-11
I believe you may want to check the cups configuration file under the "Listen" directive in /etc/cups/cupsd.conf

---

### Post by darknomel on 2011-04-11
> **Nickjpost said:**
> I believe you may want to check the cups configuration file under the "Listen" directive in /etc/cups/cupsd.conf

Sorry, I don't quite get this? I check /etc/cups/cupsd.conf , but there is nothing about the print-to-file printer in there?

---

### Post by stoogiebuncho on 2011-04-11
I'm not sure I'm understanding exactly what you're asking.

Are you asking what the program is called that prints to PDF? (it's cups-pdf)

Are you trying to print to pdf by default?

---

### Post by darknomel on 2011-04-12
> **stoogiebuncho said:**
> I'm not sure I'm understanding exactly what you're asking.

Are you asking what the program is called that prints to PDF? (it's cups-pdf)

Are you trying to print to pdf by default?

On my machine I have a print to file printer. I want to get rid of this printer so that the default printer is the only printer installed. I have a kiosk machine that I build that is in about 700 branches, and I'm getting complaints that users are accidentally printing to file instead of to the printer.

---

### Post by mcduck on 2011-04-12
> **stoogiebuncho said:**
> I'm not sure I'm understanding exactly what you're asking.

Are you asking what the program is called that prints to PDF? (it's cups-pdf)

Are you trying to print to pdf by default?

Well, that
 at the same time true and not. :)

While you can install and use cups-pdf to print to file, recent versions of Gnome actually have this ability built-in, using Cairo to directly render the document into a file.

I'm not aware of any method for disabling this feature, though. Anyway, you should be able to set the actual printer as the default printer (just don't try removing Cairo or anything like that, as it does a lot more than just this and removing it would pretty much break the GUI completely).

---

### Post by darknomel on 2011-04-12
> **mcduck said:**
> Well, that
 at the same time true and not. :)

While you can install and use cups-pdf to print to file, recent versions of Gnome actually have this ability built-in, using Cairo to directly render the document into a file.

I'm not aware of any method for disabling this feature, though. Anyway, you should be able to set the actual printer as the default printer (just don't try removing Cairo or anything like that, as it does a lot more than just this and removing it would pretty much break the GUI completely).

Setting the printer as default works, though some stupid clients still select the print to file option and then get confused by the output.

---

### Post by SeijiSensei on 2011-04-12
> **darknomel said:**
> On my machine I have a print to file printer. I want to get rid of this printer so that the default printer is the only printer installed.

Can't you just delete that definition from /etc/cups/printers.conf?  Or is the print-to-file option not defined there?  Only one entry appears when I choose print in an application, and it's the one defined in printers.conf.

---

### Post by darknomel on 2011-04-12
> **SeijiSensei said:**
> Can't you just delete that definition from /etc/cups/printers.conf?  Or is the print-to-file option not defined there?  Only one entry appears when I choose print in an application, and it's the one defined in printers.conf.

I've gone through printers.conf quite a lot and I can't seem to find it :(

---

### Post by SeijiSensei on 2011-04-12
Hmm.  I use KDE and have no print to file option anywhere, just the printer in printers.conf.  Perhaps it's a GNOME thing?

Maybe you can try [http://localhost:631/](http://localhost:631/) to talk to CUPS that way and see if you can find a way to delete the print-to-file option from there.

---

### Post by jaambutt on 2011-04-12
on your printer settings, there's a place to select "print document and markups". You only have "print document" selected.

---

### Post by mcduck on 2011-04-12
> **SeijiSensei said:**
> Hmm.  I use KDE and have no print to file option anywhere, just the printer in printers.conf.  Perhaps it's a GNOME thing?

Maybe you can try [http://localhost:631/](http://localhost:631/) to talk to CUPS that way and see if you can find a way to delete the print-to-file option from there.

Yes, like I said it's a built-in feature of Gnome (and not related to the old cups-pdf plugin), using the same Cairo backend that is used to render 2D graphics for the desktop. It has PDF, Postscript and SVG output support in addition to X Window System and OpenGL so it can print the same stuff to those formats that it can print on the screen.

---

### Post by darknomel on 2011-04-12
Thanks guys, will have a look at it tomorrow morning and feedback. I appreciate the help so far!

---

### Post by SeijiSensei on 2011-04-12
Maybe you don't need GNOME in a kiosk environment?  How about a different Ubuntu flavor like Lubuntu (LXDE) or Xubuntu (XFCE)?

---

