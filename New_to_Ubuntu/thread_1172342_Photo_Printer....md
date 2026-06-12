---
title: "Photo Printer..."
date: 2009-05-28
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-05-28
I bought an old Samsung SPP-2020 Digital Photo Printer on ebay the other day (absolute steal at £10.00!) but Ubuntu 8.10 doesn't recognise it as a photo printer but as a "generic printer" after it searched online for a download it failed to find one:( I've Googled but I can only find results in French and Spanish? (maybe it was more of a European release....)

Thanks in advance!

---

### Post by Sidewinder1 on 2009-05-28
Not to burst your bubble, but there are (not many) printers that will not work with ubuntu/linux. I've only run across one; it was a Dell Cheapie, freebie that was sold with a system. I'm thinking it was a Brother "inside".

---

### Post by kamitsukai on 2009-05-28
> **Sidewinder1 said:**
> Not to burst your bubble, but there are (not many) printers that will not work with ubuntu/linux. I've only run across one; it was a Dell Cheapie, freebie that was sold with a system. I'm thinking it was a Brother "inside".

no it's recognised and it will probably print (I don't want to waste photo paper) but clicking on the preview button before printing shows that Ubuntu doesn't understand the paper dimensions for the printer as it's only an A6 printer at the moment Ubuntu thinks it's a standard A4 text printer;)

---

### Post by philinux on 2009-05-28
There are more than you think that are supported. HP being the most as HP provide linux drivers. Epson and canon aren't bad either. As long as it's not a brand new machine you have a chance.

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)


You may find this driver helps.
[http://openprinting.org/show_printer.cgi?recnum=Samsung-SPP-2020](http://openprinting.org/show_printer.cgi?recnum=Samsung-SPP-2020)

---

### Post by kamitsukai on 2009-05-28
> **philinux said:**
> There are more than you think that are supported. HP being the most as HP provide linux drivers. Epson and canon aren't bad either. As long as it's not a brand new machine you have a chance.

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)


You may find this driver helps.
[http://openprinting.org/show_printer.cgi?recnum=Samsung-SPP-2020](http://openprinting.org/show_printer.cgi?recnum=Samsung-SPP-2020)

Ok thanks:D

I'm not sure on this bit though

> Make sure your
   CUPS is configured for use with rasterto* filters, it should be
   someplace in the CUPS docs, but in short: you must use the ESP version
   of ghostscript which can output with a 'cups' device (do gs -help|grep
   cups if unsure), you should have /etc/cups/pstoraster.convs present
   and in mime.convs the following lines should be uncommented:
   
application/postscript  application/vnd.cups-postscript 66      pstops
application/vnd.cups-postscript application/vnd.cups-raster     100     pstoras
ter
application/octet-stream        application/vnd.cups-raw        0       -


Whats it actually want me to do? and how?

---

### Post by kamitsukai on 2009-05-28
and I'm getting errors when building...

> carl@carl-desktop ~/Desktop/rastertospp-1.1 $ gcc -O2 -Wall -lcupsimage -o rastertospp rastertospp.c
In file included from rastertospp.c:12:
driver.h:39:25: error: cups/cups.h: No such file or directory
driver.h:40:27: error: cups/raster.h: No such file or directory
In file included from rastertospp.c:12:
driver.h:129: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
driver.h:159: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
driver.h:193: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
driver.h:218: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:72: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:75: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:76: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:77: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:82: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:118: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:134: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c:180: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
rastertospp.c: In function &#8216;main&#8217;:
rastertospp.c:209: error: &#8216;cups_raster_t&#8217; undeclared (first use in this function)
rastertospp.c:209: error: (Each undeclared identifier is reported only once
rastertospp.c:209: error: for each function it appears in.)
rastertospp.c:209: error: &#8216;ras&#8217; undeclared (first use in this function)
rastertospp.c:210: error: &#8216;cups_page_header_t&#8217; undeclared (first use in this function)
rastertospp.c:210: error: expected &#8216;;&#8217; before &#8216;header&#8217;
rastertospp.c:212: error: &#8216;ppd_file_t&#8217; undeclared (first use in this function)
rastertospp.c:212: error: &#8216;ppd&#8217; undeclared (first use in this function)
rastertospp.c:215: error: &#8216;cups_option_t&#8217; undeclared (first use in this function)
rastertospp.c:215: error: &#8216;options&#8217; undeclared (first use in this function)
rastertospp.c:226: warning: implicit declaration of function &#8216;cupsParseOptions&#8217;
rastertospp.c:227: warning: implicit declaration of function &#8216;ppdOpenFile&#8217;
rastertospp.c:234: warning: implicit declaration of function &#8216;ppdMarkDefaults&#8217;
rastertospp.c:235: warning: implicit declaration of function &#8216;cupsMarkOptions&#8217;
rastertospp.c:246: warning: implicit declaration of function &#8216;cupsRasterOpen&#8217;
rastertospp.c:246: error: &#8216;CUPS_RASTER_READ&#8217; undeclared (first use in this function)
rastertospp.c:253: warning: implicit declaration of function &#8216;cupsRasterReadHeader&#8217;
rastertospp.c:253: error: &#8216;header&#8217; undeclared (first use in this function)
rastertospp.c:259: warning: implicit declaration of function &#8216;StartPage&#8217;
rastertospp.c:274: warning: implicit declaration of function &#8216;ReadLine&#8217;
rastertospp.c:275: warning: implicit declaration of function &#8216;OutputLine&#8217;
rastertospp.c:281: warning: implicit declaration of function &#8216;EndPage&#8217;
rastertospp.c:286: warning: implicit declaration of function &#8216;cupsFreeOptions&#8217;
rastertospp.c:287: warning: implicit declaration of function &#8216;cupsRasterClose&#8217;

---

### Post by philinux on 2009-05-28
> **kamitsukai said:**
> Ok thanks:D

I'm not sure on this bit though



Whats it actually want me to do? and how?

That bit is just telling you to edit a file and remove the # to uncomment some lines.

---

### Post by philinux on 2009-05-28
I would start a new thread.

"Help needed compiling a printer driver" or something like that.

---

### Post by kamitsukai on 2009-05-28
> **philinux said:**
> I would start a new thread.

"Help needed compiling a printer driver" or something like that.

Ok will do:D

Thanks for your help;)

---

### Post by scprosser on 2009-05-28
I have to dispute the "not many printers that will be recognized by Ubuntu/Linux" statement. I have 5 Printers (An HP LaserJet 4+, an HP PSC1300, an Epson Stylus CX4200, a New Samsung Colour Laser (Forget the Model Number) and a Canon Inkjet (Forget the model number). All of them but the Samsung and the Canon were plug and play, and the Samsung Colour Laser took less than 3 minutes to setup and get working (Google is your friend!)(the Canon STILL doesn't like me, or Linux, but I digress). A lot of people (myself included originally) cringe at setting up a printer in Linux, it used to be MURDER, but it is not the same as it used to be, it's actually quite painless nowadays. Sure, there are some that it just wont work with, but odds are, you will be pleasantly suprised.

---

### Post by kamitsukai on 2009-05-28
Ok all Done:

> [http://ubuntuforums.org/showpost.php?p=7362109&postcount=5](http://ubuntuforums.org/showpost.php?p=7362109&postcount=5)

---

### Post by kamitsukai on 2009-05-28
I now have this printer setup with XP in virtualbox and all I can say is I wish I'd done this from the beggining it was alot less hassle and I'm starting think that I might do this with my samsung CLP-300 as the printing quality will be much better (the samsung drivers leave alot to be desired...)

---

### Post by Sidewinder1 on 2009-05-28
" there are (not many) printers that will not work with ubuntu/linux."
Translation: There are many printers that will work with ubuntu/linux.
:-)

---

### Post by Calle_Rönnow on 2009-12-25
EDIT: Still trying to get it to work. Will post any useful advice if successful.

---

