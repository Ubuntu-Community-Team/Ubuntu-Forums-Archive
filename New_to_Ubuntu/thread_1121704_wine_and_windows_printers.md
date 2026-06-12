---
title: "wine and windows printers"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by bu2971x on 2009-04-10
why isnt WINE enough to run printers that want Windows ?????

---

### Post by Paqman on 2009-04-10
Because Wine doesn't do drivers. It's only for applications.

Wine doesn't try and recreate the whole of Windows. If you want everything that Windows can do, you could install Windows in a VM. The downside of that is that it's extremely resource-hungry, since you're running two OSes at once.

---

### Post by djbushido on 2009-04-10
Wine is a binary layer. This means that it allows you to run windows programs. So if you have a windows program to print to the printer (Lexmark I think does this) then you can do that. Otherwise, the driver has to be made to work with Linux.
What kind of printer do you have by the way?

---

### Post by halitech on 2009-04-10
WINE doesn't "talk" to the hardware, thats why it won't work for drivers for printers, etc

---

### Post by irfan9727 on 2009-04-10
Printer that wants windows? Do you mean, driver? What is the type of the printer? Weird, this is the first time I've seen sentient printer! :lolflag:

---

### Post by Sef on 2009-04-10
If your printer does not have a GNU/Linux driver, then you have two options if you want to get a working printer:

1) Get a printer that will work with GNU/Linux.   Check out [OpenPrinting]("http://openprinting.org/printer_list.cgi").

2) Buy an old Windows computer and make it your print server.

---

### Post by bu2971x on 2009-04-10
no matter.........
I bought an HP J4680 Officejet and it works perfect right out of the box.
Ubu found the right driver in 10 seconds.

---

### Post by halitech on 2009-04-10
HP is about the best when it comes to being supported in *nix, Hope you enjoy your new printer :)

---

