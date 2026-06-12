---
title: "Print Server with CUPS printing blank pages from windows"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by z33 on 2007-04-30
Issue:

I setup an ubuntu print server with CUPS and i use IPP to connect to the printer from my Windows XP machines. I want this to work properly but it is not working 100%.

Speculation:

FROM WINDOWS: 
    I can print a pdf file fine however, when i print a notepad file nothing comes out. I figured there was a type format problem so i printed a file with text and graphics. The result was that the graphics was printed however the text was not printed. 

FROM UBUNTU Fiesty
   I printed the same document (microsoft word file opened with OpenOffice) and it printed properly.

So i thought maybe i was missing device fonts which windows was using. So i did 
apt-get install msttcorefonts

this did not work either, could it be that i need a postscript printer? i am not sure how this works though.

Problem:

I do not know what else to check for and my print server is not working 100% if you can help please do try.

Information:

Printer is: HL-2040 using the HL-2060 drivers on ubuntu they work perfectly
Windows XP Home being used
Ubuntu Fiesty is running on the print server with IPP CUPS

The printer was added in windows XP home by adding a network printer and giving it the URL for the IPP printer with CUPS


Many thanks in advance

---

### Post by z33 on 2007-05-02
I have to convert my files to pdf before i print them on the printer. This seems to be the only work around.

---

