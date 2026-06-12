---
title: "[SOLVED] Need Help with Wireless (I'm new)"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by opothehippo on 2008-08-27
Hello, I'm completely new to Linux, and I just installed Ubuntu 7.10 (Because 8.04 was too complicated to get working.) Im loving it much more than windows, but Im having trouble with my wireless.

I have a dell XPS M1530, with BIOS revision A09. Ever since I loaded Gusty Gibbon, wireless doesnt even show up as an option. I have read other threads with the same problem (sorry for the duplicate) but being new to the text based OS, I cant even understand how to use the soulutions. If some kind person could explain it a bit slower then usual, I would be very grateful.

---

### Post by antmenj on 2008-08-27
What wifi device does it have?

When I ordered my xps m1330 I made _sure_ I ordered intel wifi.  It just worked with gutsy:).

---

### Post by david sousa on 2008-08-27
Access the terminal and type "lspci". At the last line you can see "Network controller:" which gives your wireless card type.

Then you just have to download the correspondent drivers of your wireless card to install it trough "Windows Wireless drivers".

You can download that here [https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

Just follow the instructions and you will get that working ;)

---

### Post by opothehippo on 2008-08-27
Im still having trouble. I now know I have a Broadcom bcm4310 wireless card, and I installed what I believe is the driver of it (I used these instructions: [http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html](http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html)) but wireless just still isnt showing up.

It might be the wrong driver, but Im not sure.

Edit: Or my card could be a Intel 82801H?

:(

---

### Post by david sousa on 2008-08-28
Your card is the same as mine. I think it's right. But maybe you chose the wrong driver. 

Go at System -> Administration -> Hardware controller and see what you have there. Because your hardware maybe blocked and you have to select it to be active. Or the opposite.

Try different ways and reboot the pc whit different possibilities.

---

### Post by opothehippo on 2008-08-28
Thank you super much! It turned out it was the correct driver, I just needed to apply it. You have no idea how much it helped.

I now can fully appreciate Linux.

---

### Post by david sousa on 2008-08-28
keep enjoying ;)

---

### Post by Crafty Kisses on 2008-08-28
Can you please mark the thread solved?

---

