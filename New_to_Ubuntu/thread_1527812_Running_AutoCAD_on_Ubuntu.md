---
title: "Running AutoCAD on Ubuntu"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by MSada on 2010-07-09
Can anyone please tell me how i can run AutoCAD on Ubuntu(i use 10.04). I've tried installing it with wine but it still doesn't work.

---

### Post by audiomick on 2010-07-09
Hallo. 
I haven't looked into the subject lately, but I think CAD programs and Linux is a pretty desolate perspective. To run AutoCad, I think you will have to set up a virtual machine with Windows as the client. VMware or Virtual Box seem to be the most common alternatives.

---

### Post by -kg- on 2010-07-09
If you aren't absolutely tied to AutoCAD, the site below lists some of the alternatives specifically for the Linux platforms, some with .deb files:

[http://www.tech-edv.co.at/lunix/CADlinks.html]("http://www.tech-edv.co.at/lunix/CADlinks.html")

---

### Post by audiomick on 2010-07-09
Nice link, kg. I have had a look at the Varicad Viewer. It seems quite nice, and the program looked promising, but I haven't tried it yet.

---

### Post by Ural Nanok on 2013-01-31
To eneble the seamless mode between Ubuntu 12.10 and the Virtualbox I had to install the Vboxadditions in the Windows 7 that runs in the Virtualbox, after this install and same installation in the Ubuntu then the Guest machine identifes upon startup that it is enabled to get into the seamless mode, nice :)  
 

 Instaling AutoCAD 2013 (Civil 3D) on a Windows 7 that runs in a virtual box on Ubuntu, you may need to install some Windows features manually,  
 

 1. Visual C++ 2010 redistributable and the SP 1 download from Microsoft.
 2. Dot Net 4 (I installed full version) this is in the 3rd Patry directory of the Acad setup DVD.
 3. DirectX 9 also in the 3rd Patry directory of the Acad setup DVD.
 At least I had to do this manually to get the installation started and complete else the installation notified an error and halted, sometimes one needs to tweek the configuration file for the setup process to complete. So AutoCAD 2013 can be installed and run in the Win 7 virtual machine.
 

 I still have to see if AutoCAD can be installed directly into the Ubuntu machine, if I succeed then I will post that.
 

 Best Regards
 Ural Nanok

---

