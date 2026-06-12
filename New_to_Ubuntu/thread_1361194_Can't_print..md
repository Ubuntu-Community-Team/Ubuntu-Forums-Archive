---
title: "Can't print."
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Sunbirdaz on 2009-12-21
I have a dual boot Win XP and Ubuntu. My PC connects wirelessly to my router. My printer connects to the router via cat5. In Windows I set up the printer as an IP printer and printing to it works fine. When I add a printer in Ubuntu it finds the printer and it appears to be configured correctly. When I print to it the print job goes to the print que and I get a pop up that says the job has printed but nothing comes out of the printer. I've checked the cups service and it is installed and checked. My printer is an Epson Aculaser CX11NF.
Thanks.

---

### Post by halitech on 2009-12-21
you may want to look here

[http://www.openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_CX11NF](http://www.openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_CX11NF)

---

### Post by Statik on 2009-12-21
I have had this problem with my brother MFC printer over the network. When Ubuntu finds the printer, it uses its WIN name, but doesn't print to it. If I change it to the printer's IP address, but change nothing else, it works great. Not sure why this is, but it works. :)

Statik

---

### Post by Sunbirdaz on 2009-12-23
> **halitech said:**
> you may want to look here

[http://www.openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_CX11NF](http://www.openprinting.org/show_printer.cgi?recnum=Epson-AcuLaser_CX11NF)


Thanks. I followed the link and downloaded a couple of printer files but they would not execute. Ubuntu didn't know what they were. 
Now Ubuntu doesn't recognize the wireless adapter. I'm doing this from Windows. Life's too short for all  this frustration. I guess I'll stick with Windows.

---

### Post by Sunbirdaz on 2009-12-23
> **Statik said:**
> I have had this problem with my brother MFC printer over the network. When Ubuntu finds the printer, it uses its WIN name, but doesn't print to it. If I change it to the printer's IP address, but change nothing else, it works great. Not sure why this is, but it works. :)

Statik

Thanks. When Ubuntu found the printer it had it's IP address so I'm still scratching my  head.

---

### Post by halitech on 2009-12-24
> **Sunbirdaz said:**
> Thanks. I followed the link and downloaded a couple of printer files but they would not execute. Ubuntu didn't know what they were. 
Now Ubuntu doesn't recognize the wireless adapter. I'm doing this from Windows. Life's too short for all  this frustration. I guess I'll stick with Windows.

the files aren't executables, they are .deb files which contain the info needed to install. basically you open a terminal and run
```
sudo dpkg -i iscan_2.23.0-3.ltdl7_i386.deb
``` to install it. (assuming the file you downloaded was iscan_2.23.0-3.ltdl7_i386.deb) You would also need to make sure you are in the directory that you downloaded the file to.

Sorry you feel that this is frustrating but your choice on if you want to use windows or try to learn Ubuntu. Good luck with whatever you decide to do.

---

