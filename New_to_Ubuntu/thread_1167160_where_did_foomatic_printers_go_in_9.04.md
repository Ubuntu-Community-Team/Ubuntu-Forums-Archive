---
title: "where did foomatic printers go in 9.04?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by poikiloid on 2009-05-22
we have (Hewlett-Packard) HP Deskjet 932C

My roomate has old Gateway desktop, connected by those big older printer connections. When he adds printer in Ubuntu 8.10, it suggests HP Deskjet 930C, but if you click next, you can choose 932C instead as it lets you browse the foomatic database.

I have Dell Inspiron 1150 Laptop, connected via usb. When adding printer in Ubuntu 9.04, it also suggests 930C, but when click, it doesn't give option to select a different one. Why not? And worse, the thing won't print. The only thing that prints is "**** Unable to open the initial device, quitting." at the top of the page.

What's going on? Thanks for help...

---

### Post by poikiloid on 2009-05-23
I was able to solve my question:

I had to add the wrong suggested printer. I went here to download my ppd file for my printer: [http://openprinting.org](http://openprinting.org)
Then in the printer list, I right click and to to Properties. On Settings tab, I click the button "Change..." on the "Make and Model" line. Then I do "Provide ppd file" and browsed to it.

This is not as good as the old way in 8.10 where you can do this from the beginning. Please revert, Ubuntu. Thanks.

---

