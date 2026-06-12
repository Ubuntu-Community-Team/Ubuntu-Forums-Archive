---
title: "Printer not working"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Ralph Legros on 2010-04-04
Hi! My HP Laserjet 1000 printer won't print . Help please.

---

### Post by RedSingularity on 2010-04-04
Have you set up the printer in 

System>Admin>Printing?

---

### Post by Ralph Legros on 2010-04-04
Yes I have

---

### Post by Ralph Legros on 2010-04-04
When I go to print test page nothing happens.

---

### Post by bhmildy on 2010-04-05
install newest hplip from here
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by @rizz on 2010-04-05
Hey there,

  try this:

Disconnect your printer from the computer

and then open and close the lid of the printer five times. It should print a white page with 

horizontal lines on it........try it and let us know if its printing that page?

---

### Post by Ralph Legros on 2010-04-05
Hi! I went to hplipopensource.com and downloaded hplip 3.10.2run and everything installe fine with the automatic installer. Then it brought me to hp setup and everything went fine till I got to the binary plugin  and there it would not install  error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)
error: hp-setup failed. Please run hp-setup manually. What to do please. Thanks

---

### Post by bhmildy on 2010-04-05
Try these instructions:
[http://ubuntuforums.org/showpost.php?p=7027303&postcount=26](http://ubuntuforums.org/showpost.php?p=7027303&postcount=26)

I recommend you try severalof the things suggested, but this may be the important part:

> In essence, I fixed the problem by typing
sudo /usr/share/hplip/plugin.py    
Many people in Ubuntu have problems printing with LJ 1000.  Advanced search here in the forums gets dozens of discussions with the same problem.

---

