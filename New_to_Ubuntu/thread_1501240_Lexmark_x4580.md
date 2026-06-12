---
title: "Lexmark x4580"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Sam24 on 2010-06-04
Hi,
 
First of, thanks for all the useful support here on the forums its been a real help.
 
What I wanted to ask is, I have been given a Lexmark x4580 All in one printer, how do i connect this via usb to my comuter running Ubuntu 10.04.
 
I dont care about the scanning functions or any of the ink level display reading things, all I want to be able to do is print.
 
Thanks for your help

---

### Post by ramjet_1953 on 2010-06-04
Generally, Lexmark printers are almost impossible to get working under Linux, as they do not release drivers for Linux.

I had a look on the OpenPinting database and it is not even listed.

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Regards,
Roger:)

---

### Post by davidmohammed on 2010-06-04
if you've got a Mac friend - get them to install the x4500 driver download from lexmark website.  When they have done that, see if there is a ppd file installed - since Mac OS uses CUPS there is a good possibility the ppd is installed.

Copy that ppd across to ubuntu and add a printer - when prompted, point it to the ppd.

If you are lucky, your lexmark will work.  If the ppd refers to any Mac binaries, then you will be out of luck.

---

### Post by Sam24 on 2010-06-04
[QUOTE=davidmohammed;9408499]if you've got a Mac friend - get them to install the x4500 driver download from lexmark website. When they have done that, see if there is a ppd file installed /QUOTE]
 
 
is there any way of just downloading the ppd file?
 
thanks

---

### Post by davidmohammed on 2010-06-04
the lexmark mac os driver is a .dmg - specific to mac's.  Dont think linux can extract that type of file but you may be able to mount it.  Google is your friend on how to do that...

---

### Post by Sam24 on 2010-06-04
> **davidmohammed said:**
> the lexmark mac os driver is a .dmg - specific to mac's. Dont think linux can extract that type of file but you may be able to mount it. Google is your friend on how to do that...
 
 
i have got hold of the .dmg file and can view it but where do i look there is a load of folders in it?!

---

### Post by davidmohammed on 2010-06-04
> **Sam24 said:**
> i have got hold of the .dmg file and can view it but where do i look there is a load of folders in it?!

at a guess - search for any file with a .ppd extension.  

However, I've no idea if the mac installer actually creates one of these files - hence "find a mac friend".  Alternatively - you've got one very big door-stop...

---

### Post by Sam24 on 2010-06-04
oh well nice expensive door stop it is then :(

---

### Post by mapes12 on 2010-06-05
Try this for the dmg package:-

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

Hewlett Packard printers are my preferred choice as they are well supported by HP:-

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

:)

---

### Post by Sam24 on 2010-06-07
Thanks for the link mapes12, but where on the site do I find the dmg package?
 
Thanks again.

---

### Post by Dragyrn1456 on 2010-12-02
> **mapes12 said:**
> Try this for the dmg package:-

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

Hewlett Packard printers are my preferred choice as they are well supported by HP:-

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

:)

...where do i find the file in the first link? can someone please just give me a direct download link for the file!?:!:

---

