---
title: "Konqueror doesnt see some html"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by warped4sure on 2008-12-28
Just installed Hardy couple of weeks ago, Within last few days I installed a cnc program-EMC2 and it installed an rtai kernel for Hardy. Now have both kernels. No problem, The program uses Konqueror to View included documentation.
 Example:/usr/share/doc/emc2/gcode.html which is successful,
but when a term within that page is clicked on for expanded info.- the following is placed in address bar :

 file:///usr/share/doc/emc2/gcode_main.html#sec:G0:-Rapid-Linear

Instead of taking me to "#sec:xxx:xxxxxxx",  Konqueror responds with the following error:

--------------------------------------------------------------------
An error occurred while loading file:///usr/share/doc/emc2/gcode_main.html#sec:G0:-Rapid-Linear:
The file or folder /usr/share/doc/emc2/gcode_main.html does not exist.
---------------------------------------------------------------------

Problem occurs in either kernel but when I access with Firefox, Mozilla Firefox , Epiphany or Opera it performs correctly. Is something missing or wrong in Konqueror??

Konqueror - KDE Release 3.5.10

Any help most appreciated.
warped4sure

Corrections and additional info.
After closer reading and examining source code of html, found that Konqueror ignores the "href" in html page. the other browsers that worked follow the "href's" correctly and actually go to URL:[http://linuxcnc.org/docs/2.2/html/gcode_main.html#sec:G0:-Rapid-Linear](http://linuxcnc.org/docs/2.2/html/gcode_main.html#sec:G0:-Rapid-Linear). But Konqueror looks for info in: file:///usr/share/doc/emc2/gcode_main.html#sec:G0:-Rapid-Linear  -and gives error message. My temporary solutions are(2):(1)Use the open with another browser funtion (2)Copy the html from correct URL into the file location (that will require updating maintenance).

---

