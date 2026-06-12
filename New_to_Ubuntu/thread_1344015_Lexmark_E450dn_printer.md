---
title: "Lexmark E450dn printer"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by werecatomega on 2009-12-02
i have been googling this without success. i'm trying to setup a network printer, Lexmark E450dn, but i need the driver. Ubuntu doesn't have this driver by default but i can't find any drivers for linux online. can somebody help me?

---

### Post by halitech on 2009-12-02
according to openprinting.org it should work perfectly but doesnt list what driver to use.

[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-E450dn](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-E450dn)

Not sure how well it will work but Lexmark does have a Debian driver that is a .deb

[http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_E450DN&id=DR15561&os=DEBIAN_GNU_LINUX&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&actp=DD_LIST&productCode=LEXMARK_E450DN&id=DR15561&os=DEBIAN_GNU_LINUX&oslocale=en_US&segment=DOWNLOAD&userlocale=EN_US&locale=en)

---

### Post by werecatomega on 2009-12-03
when i installed the .deb, i couldn't find in the list anywhere where it said E450dn.

---

### Post by starwed on 2010-08-17
I seem to be able to print using a driver labelled "e352dn".  I've only tried basic printing, though, nothing duplex.

---

### Post by franapoli on 2011-01-03
I solved the issue on my ubuntu lucid.
To allow full duplex right-click on the printer Icon from System / Administration / Printer (I think that's the english translation) and set it from there. I previously did this from the "Properties" button of the print dialogue, but doesn't work now.
This could be enough. If it isn't, consider that I'm using the "Lexmark E450DN drivers for CUPS based systems" available from the Lexmark website, not the .deb.
cheers

---

