---
title: "No Custom Paper-size in Printing (OpenOffice.org)"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Charlie91 on 2010-11-11
I have a paper size called *Long Bond*, measuring 8.5x13 in. (21.59x33.02 cm) that is not one of the options in the Printer, although it can be set within OpenOffice.org.  There is no *Custom* option.  I tried to print using *Letter* and *US Legal* (8.5x14in) but it's not workable. :(

How can I put 8.5x13in. (*long bond*) in the choices for paper size in printing?

---

### Post by walt.smith1960 on 2010-11-12
format =>page =>paper format => format =>user.  It looks like you can specify paper width, height and orientation there.

---

### Post by Charlie91 on 2010-11-12
Using that menu, I can set the paper-size to *long bond* (don't even need the *user* format).  The problem is when *printing* comes, there is no *long bond* or *user* format among the choices!  And if I print anyway, something bad always happens.

The *custom* option is there if I print from *gedit*; it's gone if I print from *OpenOffice.org*.

[IMG]http://ubuntuforums.org/picture.php?albumid=2100&pictureid=6996[/IMG]
File>Print>Properties window

---

### Post by Charlie91 on 2010-11-13
I guess the *OpenOffice.org* team should include this option (putting a *Custom* format in one of the choices) in the next update (I assumed it's an *OpenOffice* thing because I've no problems with *gedit*).  **The paper-size in *Format > Page* is there, but not in *File > Print > Properties***.

I'm just wondering, the choice of *US Legal* (8.5"x14") doesn't work with my desired *Long Bond* (8.5"x13"), but I'll have to force this maneuver.  How can the printer 'know' that my paper is 1 inch shorter? Unless someone answer this, I just have to find a way around this problem (sometimes magic works with Ubuntu). :P

Since *Long Bond* is not in the printing choices, I think choosing *US Legal* in *Format>Page* makes sense for consistency; I'll just increase the bottom-margin by 1 inch. I'll try that...

---

### Post by Charlie91 on 2010-11-14
I guess this thread should be rephrased to: **How can I 'force' OpenOffice.org to use the system Print dialog-window rather than its own?**  I observed that *gedit*, *Document viewer* (I think this is *Evince*) and *Firefox* all use the same *dialog-box* in printing (system default) documents.

Going back to the problem...  to print a document with paper-size of 8.5"x13", I found a rather long way around it.  I just did it: export the ODT file to PDF--then print the PDF file.  Choosing to print the document in *OpenOffice* just is 'impossible'.

I'm sorry, it seems this thread has become a private mini-blog on the printing subject... :popcorn:

---

### Post by Alejandro Nova on 2011-03-05
Charlie, and everyone out there.

In Chile, the problem with the "Long Bond" paper size is widespread and severe. The standard sizes of paper here are US Letter (Carta) and "Long Bond" (Oficio). Forget about Legal or A4.

That's why, a long time ago, I introduced a little kludge in Gutenprint to do the job: I filed a bug report requesting the paper size "Chilean Office" to be introduced. This is a virtual symlink to "American Foolscap", "Long Bond" or whatever measuring 8.5 x 13 inches.

The catch is: you need the full driver. Here's how you do it.

1. Get your preferred browser (YES, WEB BROWSER) and point it to 127.0.0.1:631
2. Select the "Administration" tab.
3. Select "Manage Printers".
4. Select your printer, and, in the list of Administrative Tasks, select "Modify printer"
5. You'll see that Ubuntu, by default, selects for you a "Simplified Driver" You'll see something like this.

> Epson Stylus Color XXX - Gutenprint 5.2.6 (Simplified driver) - en_US

You need this one.

> Epson Stylus Color XXX - Gutenprint 5.2.6 - en_US

Once you have your unsimplified driver, restart OpenOffice and, the next time, "Chilean Office" will be available as one of your paper size options. That will do the job.

---

### Post by ledjazz on 2011-04-26
This problem is still active in Open Office 3.3.0.

Amazing reply from Alejandro Nova. Gracias!

---

### Post by Charlie91 on 2012-07-22
Thanks Alejandro for that answer.  I guess after 2 years, the problem (for me) is solved (from many sequential OpenOffice updates).

Thanks all!

---

### Post by wildmanne39 on 2012-07-22
Old thread closed.

---

