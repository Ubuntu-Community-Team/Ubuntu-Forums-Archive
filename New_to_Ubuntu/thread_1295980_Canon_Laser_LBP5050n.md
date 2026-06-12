---
title: "Canon Laser LBP5050n"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by illumeo on 2009-10-20
Hi 
Has anyone installed a Canon Laser Printer on their network?
I have a LBP5050n and could do with some tips!

Thanks

---

### Post by longtom on 2009-10-20
I have installed Canon printers before.  I am sure you have done your research and started.

Where is your problem?.

Your luck is in, Canon has a Linux driver for your printer:

[http://support-asia.canon-asia.com/P/search?category=Laser+Printers&series=Color&model=LBP5050N&menu=download&filter=0](http://support-asia.canon-asia.com/P/search?category=Laser+Printers&series=Color&model=LBP5050N&menu=download&filter=0)

---

### Post by illumeo on 2009-10-20
Hi,
I followed the instructions that come with the drivers, from the asian canon site, after runing the two .deb. I must have got something wrong as I ended up with two printers, one showing as stopped and the other as idle, cpp:/var/ccpd/fifo0
when i hit the Print test page nothing happens.

---

### Post by longtom on 2009-10-20
What I remember from my IP4500 it was also 2 debs.  One needed to be installed for the other to work.

After that I selected the new driver at Systems > Printing etc as one normally does.

I also got the printer from my first install with gutenberg drivers, which I deleted.

---

### Post by illumeo on 2009-10-21
Did another install by just going to printer config and new
Device URI socket://192.168.1.20:9100
still no joy.

---

