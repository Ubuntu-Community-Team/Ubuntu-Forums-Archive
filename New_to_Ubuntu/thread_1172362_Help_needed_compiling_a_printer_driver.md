---
title: "Help needed compiling a printer driver"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-05-28
I need some help compiling the following printer driver for my samsung spp-2020 photo printer:D

> [http://openprinting.org/show_printer.cgi?recnum=Samsung-SPP-2020](http://openprinting.org/show_printer.cgi?recnum=Samsung-SPP-2020)

so far I've tried comipiling but I get the following error (I'm copy & Pasting from the instructions on the page above)

```
carl@carl-desktop ~/Desktop/rastertospp-1.1 $ gcc -O2 -Wall -lcupsimage -o rastertospp rastertospp.c
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
```

---

### Post by halitech on 2009-05-28
just a quick question, did you install build-essential to get all the compiling tools you need to compile apps?

---

### Post by kamitsukai on 2009-05-28
> **halitech said:**
> just a quick question, did you install build-essential to get all the compiling tools you need to compile apps?

Yep all installed =]

---

### Post by philinux on 2009-05-28
I'd email the guy he's kindly left his address on the driver page.

---

### Post by kamitsukai on 2009-05-28
Ok I've done it =] (very proud of myself...)

But it's till not exactly brilliant it leaves gaps on either side of the image and the print quality is OK at best...

my next option is using virtualbox with XP...

for instructions I used this page which I put through google translate as it's in french:

> [http://forum.ubuntu-fr.org/viewtopic.php?pid=1280210](http://forum.ubuntu-fr.org/viewtopic.php?pid=1280210)

---

