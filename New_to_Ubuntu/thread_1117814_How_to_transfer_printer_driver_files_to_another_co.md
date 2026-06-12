---
title: "How to transfer printer driver files to another computer?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by garyed on 2009-04-06
I have an old laptop running Feisty that prints fine but I need to install a the same printer on another computer also running Feisty.
I assume I could just copy the files needed from one computer to the other & then install the printer. But the trick is knowing what files i need.
To install the original drivers I had to install csh which was no problem at the time but since Feisty is no longer supported "apt-get install csh" doesn't work any longer so I'm trying to figure an alternative way to install my Brother MFC 420CN.
Any ideas

---

### Post by halitech on 2009-04-06
maybe you can download the files manually from here and put on a thumb drive or cd and manually install them on the other machine

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

or you possibly can change the sources.list file to point to there

---

### Post by garyed on 2009-04-06
Thanks for the ideas but I'm still a little lost with where to go from here.

If I could only figure out what files i needed for my printer I could just copy from the Feisty computer where the printer's working to the Feisty one that's not.

---

### Post by halitech on 2009-04-06
according to openprinting.org [http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-420CN](http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-420CN) there are native drivers on the brothers website. Maybe try downloading that and installing and it should prompt you for any missing files

[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)

---

### Post by Mark Phelps on 2009-04-06
Look in /etc/cups/ppd for files ending in ".ppd".  If you have any, copy them off to USB stick.

You can use the ppd files in your other machine to install the printers.

---

