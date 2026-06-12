---
title: "Headless network HPLIP"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by victorbrca on 2009-06-05
Hello all,


I'm shopping for an HP printer for home and was wondering if HPLIP allows for printing and scanning over the network when plugged to a headless server? 

Another doubt is if the printing/scanning features (if supported) would work on both Windows and Linux clients?

The printer I'm looking to buy is HP Photosmart C4480.

Thanks!

Vic.

---

### Post by jonobr on 2009-06-06
Hello

I recently setup a C7180 all in one with my ubuntu desktop installation at home.

It was super easy in 9.04 and I was surprised at how well it worked.

I used xsane for the scanning, and the drivers for printing were there also,
I tested both regular printing and photo printing which the C7180 can do.
I cant fax , but Im not too worried about that,
In my previous windows  setup I did not use the dialing app from HP,
I just used to do it manuallu (who sends faxes these days anyway:-)


Last comment is I had this printer for over 2 years now, so its no so modern, so please dont take this as a recommendation to buy if its obsolete (or about to be)

---

### Post by victorbrca on 2009-06-06
> **jonobr said:**
> Hello

I recently setup a C7180 all in one with my ubuntu desktop installation at home.

It was super easy in 9.04 and I was surprised at how well it worked.

I used xsane for the scanning, and the drivers for printing were there also,
I tested both regular printing and photo printing which the C7180 can do.
I cant fax , but Im not too worried about that,
In my previous windows  setup I did not use the dialing app from HP,
I just used to do it manuallu (who sends faxes these days anyway:-)


Last comment is I had this printer for over 2 years now, so its no so modern, so please dont take this as a recommendation to buy if its obsolete (or about to be)


Was that a desktop with X or a server?

---

### Post by jonobr on 2009-06-06
Hello

I was running the desktop.
I only install the server when Im bored and want to play with stuff....:-)

---

### Post by victorbrca on 2009-06-06
> **jonobr said:**
> Hello

I was running the desktop.
I only install the server when Im bored and want to play with stuff....:-)

Thanks!!

---

### Post by victorbrca on 2009-06-06
Anyone else with experience on HPLIP on a server?

---

### Post by victorbrca on 2009-06-11
If anyone needs to come back to this. 

I have purchased a HP C4480 and it works. I did not have to install HPLIP, but it seems that it came installed by default on the server (Jaunty).

Server Side:
- Printer - I did the printer configuration using cups (via http)
- Scanner - Shared the scanner with sane

Linux Client:
- Printer - Used the default Gnome printer settings
- Scanner - Used sane

Windows Client:
- Printer - Inserted the CD, manually added the printer and pointed to the CD for the *inf file
- Scanner - Used XSane for Win32


Vic.

---

### Post by jonobr on 2009-06-11
Good repost, thanks for sharing,

I wonder if there is a location where users can share their experience with the printers they have used with different versions.

Good / bad/ a lot of trouble?
Maybe there is, I just have not seen a user maintained list on this

Thanks!

---

### Post by victorbrca on 2009-06-11
> **jonobr said:**
> Good repost, thanks for sharing,

I wonder if there is a location where users can share their experience with the printers they have used with different versions.

Good / bad/ a lot of trouble?
Maybe there is, I just have not seen a user maintained list on this

Thanks!

HPLIP has a list with the printers that work, but they don't support network shares.

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

And here's another one:
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

Vic.

---

