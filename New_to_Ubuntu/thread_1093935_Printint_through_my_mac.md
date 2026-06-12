---
title: "Printint through my mac?"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by ja660k on 2009-03-12
hey guys, im looking to print documents on a brother mfc 260c
but it is connected to my mac? 

so what should i do.
i have one usb port spare on my cable modem??
incase i have to make it a network printer?

help.

---

### Post by UltraMathMan on 2009-03-20
Hello,

OS X uses the Common Unix Print Server (CUPS) as does Ubuntu, so setting up the Mac to share the printer and see it on the Ubuntu computer over the network should be pretty straightforward. First start by making sure the printer on the Mac is shared - I don't recall the steps to do so exactly, so if you have trouble with that let me know and I'll try google.

Once the Mac is set to share the printer, open up a web browser on the Ubuntu machine and navigate to localhost:631

This will give you the CUPS web interface (you can get it on the Mac the same way). Go to Administration and click Find New Printers. Hopefully the printer connected to the Mac will show up there and you'll be able to add it. Let me know if it goes amiss.

-Hope this helps :)

---

### Post by cariboo on 2009-03-20
Have a look at the [Openprinting Database]("http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-260C"), for which drivers you need.

Jim

---

### Post by BDNiner on 2009-03-20
Brother has very good linux support. You can get drivers and detailed instructions on their website. and since both OSX and linux use CUPS then it should be very easy to share your printer on OSX and then connect to it from your linux computer.

---

### Post by avtolle on 2009-03-20
What kind of Mac do you have? That is, a newer intel mac or an older ppc mac? The reason for asking: Brother's support for linux is very good, but the drivers are for intel. BTW, if you have an intel system, look in the repositories for the correct printer drivers for your MFC 260c, and install from there.

---

