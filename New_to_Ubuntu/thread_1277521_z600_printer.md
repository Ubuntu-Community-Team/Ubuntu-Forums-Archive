---
title: "z600 printer"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by rhoward on 2009-09-28
I followed all the commands to install my z600 printer and even though, in system> administration>printing , tells me it's installed it will not print. I have searched, until my fingers were tired, trying to find a solution for it, but no luck. 
Take a look at the screenshot, in particular the bottom left where it says printer state. I apparently need something, but I have no idea what it may be.
Please, i don't want to swith between Windows and Ubuntu in order to print

---

### Post by Sourcey on 2009-09-28
This CUPS driver may help you -> [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&os_group=Redhat&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:389:0:0&os_group=Redhat&target=)

Although, you are going to need to convert the rpm to a deb using alien.

---

### Post by halitech on 2009-09-28
Lexmark is inherently bad when it comes to supporting open source but this seems to one of the few printers that someone has gotten working. See here:

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_Series](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_Series)

(instructions are for Mandriva but may work in Ubuntu)

---

