---
title: "Canon PIXMA MP970"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by egyn on 2007-11-13
Hi, 
I've recently attached my Canon PIXMA MP970 multipurpose printer to my hub and have it working with my XP-box. I would now like to see if it is possible to access the printer on my Ubuntu machine (x86 7.10). I've done some research on these forums and on the Internet and discovered CUPS and the OpenPrinting database. It seems like the printer is too new to have gotten support through Ubuntu. I've assigned a local ip-address to the printer and have stumbled upon LPD but havent looked into detail about it.

Any ideas or hints in the matter would be great.

Egyn

---

### Post by Phloston on 2007-12-06
I'm looking into buying a MP970, but cannot find out if any one has got it to work with Ubuntu.
On the Linux Foundation page [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) I found that some Canon printers work, but nothing on the Pixma MP970 (closest is MP960, but is that close technically?

Did you manage to get it to work?

---

### Post by liquidalien on 2008-01-06
I've tried the Pixma IP6700 driver as well as the bjc600... The printer only ejects a blank sheet :(

I've tried to compile the linux driver (pixus ip..) found on the canon website but no success with the "ps to inkjet" driver, maybe because I'm on a 64 bits system.

Did someone tried to compile a more recent gutenprint driver ?

---

### Post by TooMuchCoffee on 2008-02-07
Have got greyscale Pixma MP970 working using MP150 driver included in Ubuntu 7.10.  The yellow registration is off so full colour is pretty useless. I have tried other MP Drivers but got same page feeding problem described above.  No science just trial and error.

---

### Post by liquidalien on 2008-02-09
Well, I'll try with de Pixma 150 driver.

Now, I try to make work the MP970 driver for Mac OSX on Ubuntu :) I've found the PPD but it needs a CUPS filter like "raster2canonIJ". Seaching on the net, I've found it exists a rastertocanon filter provided by CUPS but it seems missing in /usr/lib/cups/filter... I keep on searching

---

### Post by mykmelez on 2008-02-24
I tried the MP150 driver, and it worked well enough (fine for greyscale).  As far as I can tell, all the MP printers use the same driver, so it doesn't matter which one you pick.

Like TooMuchCoffee, I saw yellow being printed incorrectly (perhaps the older MP printers didn't have all the cartridges the new one does?), so I'll have to wait to print in color from Linux.  But all my photos are on my Mac OS X machine anyway, so that's ok for now.

---

### Post by HubertK on 2008-03-07
Hallo,
sorry my Englisch is very bad.
I have a same printer, i  test the printer driver Canon PIXMA iP6700D from
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) an he works fine.

I habe test the driver ip6700 from Gutenprint to, but this driver don't work jet correkt. 
The page of the paper is clean.

---

### Post by liquidalien on 2008-03-08
Thank you very much... This driver rocks !!!

I'll test it more fully this week-end.

/Fabien

---

### Post by hikertim on 2008-03-21
HubertK,

Thank you!  Your English is much better than my German!  Is your MP970 connected via USB or ethernet?  If the MP970 is connected via ethernet, is it connected directly to a PC or to a router or hub?

-HikerTim
(A Debian user learning much from Ubuntu!)

There are 11 types of people in the world;  those who understand binary, those who don't, and those who cringed at the start of this joke!

---

### Post by liquidalien on 2008-03-23
It's directly connected via USB. And you should use 1200 dpi or 2400 dpi mode for printing. The 300 dpi or 300 fast gives bad results.

/Fabien

---

### Post by Cygnus on 2008-04-20
I also tried Turboprint on my MP970 and it works fine. But to be able to print without the logo in the free version you are required to use the low resolution. I could not get good prints from that however. If I chose 300dpi the logo is gone but the prints will be really tiny and unusable, Have you seen the same thing ?

---

### Post by liquidalien on 2008-04-20
Yes only 1200 dpi works for me. I've the same results as you with 300 dpi (I'm a turbo print registred user).

Regards,

/F

---

