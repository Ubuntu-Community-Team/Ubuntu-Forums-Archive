---
title: "HP Printer Shows But Doesn't Print"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-04
Hello! Newbie back with another question. ^^;; I have an HP Deskjet D1600 printer, and it does show up on the top panel, but when I try to print something, it doesn't print. It says it's processing, but the job never goes through.

I tried going to this website: [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

But I couldn't find the exact D1600 printer, just a few with letters after the numbers. I decided on the D1600c driver, went to download it, but when I tried to run it, it came up with this error message: 

[I]Could not open the file /home/username/Downloads/hplip-3.11.3a.run.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

Character Encoding (select): Current Locale UTF-8 or Western ISO-8859-15[/I]

I clicked Retry while having selected each of the character encoding options, and nothing.

And this page that came up didn't help either, since some of the images with the steps are broken: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

So I have no idea what to do. Any help sent my way is greatly appreciated! :)

---

### Post by Mark Phelps on 2011-04-05
Have several HP printers and found using CUPS works just fine.

Open a browser, enter "localhost:631" and that will open CUPS.  You can then use the menus to add printers, and also to select CUPS drivers.

---

### Post by unknowngal on 2011-04-09
> **Mark Phelps said:**
> Have several HP printers and found using CUPS works just fine.

Open a browser, enter "localhost:631" and that will open CUPS.  You can then use the menus to add printers, and also to select CUPS drivers.

By browser, do you mean a web browser, or do you mean the Terminal? Sorry, I'm a bit confused. :confused:

---

### Post by Frogs Hair on 2011-04-09
I found this tread and tried what was suggested and I did not get a similar result as suggested by the thread only a page full of search results . 
[http://ubuntuforums.org/showthread.php?t=916711](http://ubuntuforums.org/showthread.php?t=916711)

---

### Post by rosencrantz on 2011-04-10
Does the printer also fail to print a Cups test page?
A very good page to check for printer support questions is the OpenPrinting database, but I only found the D1660 there ([http://www.openprinting.org/printer/HP/HP-DeskJet_d1660](http://www.openprinting.org/printer/HP/HP-DeskJet_d1660)).
However, I also got this bug report, which looks similar to your problem:
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/608443](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/608443)
Quoting comment #8:
> For me it has worked installing the latest HPLIP version form HP page:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by unknowngal on 2011-04-10
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

That worked! :D Thank you so much! ^_^ And, for anyone who comes across this thread needing help, here's the direct page for the download and instructions:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Thank you again! Now I'm hoping it'll still work after a restart. I'm just paranoid like that. XP

---

### Post by unknowngal on 2011-04-10
Yep, all's well on restart! :D Thank youuuu! *marks thread as solved* :D

---

