---
title: "Gui easy sharing your printer for big noobs ?"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by frenchn00b on 2008-03-08
hello, 

Is there any program like that for n00bs ?

thanks:confused::confused:

---

### Post by vixol on 2008-03-08
On the computer with the printer start System-Adminsitration-Printing
Under server settings choose "Share published printers connected to this system"

On the computer who wants to connect start  System-Adminsitration-Printing
Choose "SHow printers connected to other systems". Click Apply and exit. Restart  System-Adminsitration-Printing. Now the shared printer should appear in the area to the left.

---

### Post by frenchn00b on 2008-03-08
> **vixol said:**
> On the computer with the printer start System-Adminsitration-Printing
Under server settings choose "Share published printers connected to this system"

On the computer who wants to connect start  System-Adminsitration-Printing
Choose "SHow printers connected to other systems". Click Apply and exit. Restart  System-Adminsitration-Printing. Now the shared printer should appear in the area to the left.

(in gnome-panel you mean ?)

---

### Post by vixol on 2008-03-09
Yes, in the upper left corner of your screen

And I assume you have already installed the printer on the first computer. Otherwise I think you can figure out how to do that using same program as above.

I have found sometimes that using the old printer gui is sometimes easier. If you want to try it, type
sudo apt-get install gnome-cups-manager
to install it and then
sudo gnome-cups-manager
to use it. I find it more intuitive to use to istall printers with but that's just my two cents.

---

