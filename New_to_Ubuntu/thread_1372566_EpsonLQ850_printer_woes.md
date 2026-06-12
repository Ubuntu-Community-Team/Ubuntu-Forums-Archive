---
title: "EpsonLQ850 printer woes"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by TerrieG on 2010-01-04
I am totally new to downloading and installing software, though I can get around in linux pretty good. I have ubuntu 9.10. I have a very old Epson LQ850 dot matrix printer. I have downloaded the .ppd file and my computer recognizes the printer and sends files to the printer as well as shows them on the printer queue. paraport is running.
 
But.... It takes 1 minute between each line it prints, prints each line twice and inserts a blank line inbetween each line. Makes me think that it is not filtering or translating on the way to the printer.
 
I downloaded foomatic-rip , filters, database, etc. though I already have it installed on my system. When I try to do the ./configure make and make install, I get error messages. configure runs, but I get warnings. When I run "make", it errors out because it can't find ghostscript/ierrors.h and ghostscript/iapi.h. 
 
 
I have also read that I might need to recompile ghostscript with the name of my driver. Don't know how to do that either.
 
I am not online so I have to download to a USB and then go home and try to install. 
 
Any suggestions of what to try next? Appreciate the help.

---

### Post by cariboo on 2010-01-05
It may be as simple as setting the correct options in the cups web interface. Open your favorite browser and type:

[http://localhost:631]("http://localhost:631")

In the url bar. Select the printers tab, and go to printer settings.

---

