---
title: "Photosmart Printer not connected"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by masontgreen on 2009-11-06
I have a HP Photosmart 7660 and while Ubuntu recognizes the printer, it says"Printer 'photosmart-7600-series' may not be connected." I could really use some help as I'm not a developer and don't know Terminal that well...

---

### Post by clive littlewood on 2009-11-06
Hi

Ubuntu is usually great with HP products as they supply many linux drivers.

If you do not have HPLIP Toolbox installed go to the software center and put HPLIP toolbox in the search.

Install and you should be good to go.

If not go to the HP support site and follow the links to linux drivers for your model.

They download as a .deb file so just double click and it will install automatically.

Hope this helps

Clive

---

### Post by masontgreen on 2009-11-06
I'm only getting a .run option and this is what I get when I try it in Terminal:
smokey@smokey-desktop:~$ cd Desktop
smokey@smokey-desktop:~/Desktop$ sh hplip-3.9.6.run
sh: Can't open hplip-3.9.6.run

---

### Post by masontgreen on 2009-11-06
Nevermind...It just decided to start working. Not sure why or how, but I guess I'm not too concerned with semantics right now.

---

