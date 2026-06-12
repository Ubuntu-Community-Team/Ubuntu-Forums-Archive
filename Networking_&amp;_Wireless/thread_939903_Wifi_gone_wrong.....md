---
title: "Wifi gone wrong...."
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by ZootHornRollo on 2008-10-06
hi,

i have a pc running ubuntu 8.04 that had a previously rock solid wifi connection.

WHen i tried to connect tonight it isn't even finding the network.  I changed numerous settings with no success.  Went back to previous settings, have got it working but every few minutes i get a window asking for wireless passkey poping up.  

i boted into XP and it works flawlessly.  Also no problems on my other ubuntu machine running 7.10.  THey both have the same wifi card.

just seems odd seeing as how this machine has had no problems with wifi since i upgraded to the pci wifi card a number of months ago....  why should  aproblem suddenly occur?

---

### Post by chrisd234 on 2008-10-06
I have basically the same issue. It came after I downloaded the kernel upgrade. Previously I was using the "wl" restricted driver. I upgraded the kernel yesterday via synaptic/upgrade manager yesterday and it only works if I go back into the old kernel

---

### Post by chrisd234 on 2008-10-06
Forgot add.. if this is because of the Kernel update like mine was, I simply copied the driver 'wl.ko' from the old kernel in /lib/modules/new kernel number goes here/driver folder

and I dropped then on the desktop. I then followed a tutorial I found here, as if I had already downloaded and extracted the file:

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

worked fine

---

### Post by ZootHornRollo on 2008-10-06
thanks very much.

i loaded the old kernal and all works ok.

i don't have a braodcom device.  its an edimax car that uses ralink driver.

so heres hoping there a fix soon...

---

