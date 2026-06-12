---
title: "Windows CAD programs with Ubantu"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by z650Steve on 2011-04-04
I have tried the demo of Ubantu 10.10 and I like it! So much so, I am going to instal onto a spare hard drive or have dual boot.
 
My question is,"Can Ubantu run CAD programs such as TurboCAD and the likes?" 
 
I ask also because I BETA test a couple of CAD programs: DoubelCAD and DesignCAD and would like to try them under this operating system, perhaps by emulating Windows?
 
Thanks in advance.

---

### Post by pi3.1415926535... on 2011-04-04
You could use [WINE]("http://www.winehq.org/") (Wine Is Not an Emulator), which is a nice open source project, though it is not terribly reliable. Running Windows in a VM (Virtual Machine), is an option, but will take more power, and requires having Windows.

---

### Post by z650Steve on 2011-04-04
Thanks, will try that.

---

### Post by Learning Linux 2011 on 2011-04-04
> **z650Steve said:**
> I have tried the demo of Ubantu 10.10 and I like it! So much so, I am going to instal onto a spare hard drive or have dual boot.
 
My question is,"Can Ubuntu run CAD programs such as TurboCAD and the likes?" 
 
I ask also because I BETA test a couple of CAD programs: DoubelCAD and DesignCAD and would like to try them under this operating system, perhaps by emulating Windows?
 
Thanks in advance.

There is a program called WINE which allows you to run some Windows CAD programs.
You can go here:
[http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)
to see if the one you want will run.

Also, you can install a virtual machine like Oracle's VirtualBox and actually run Windows inside Linux.  Then you can install CAD inside of that.

---

### Post by Chronon on 2011-04-04
Here are the CAD/CAM apps listed at WineHQ:
[http://appdb.winehq.org/objectManager.php?sClass=category&iId=59&sAction=view&sTitle=Browse+Applications](http://appdb.winehq.org/objectManager.php?sClass=category&iId=59&sAction=view&sTitle=Browse+Applications)

---

### Post by rosencrantz on 2011-04-04
I'd recommend a dual boot instead of VirtualBox. CAD programs are usually rather hard on your resources and tend to be agonisingly slow on virtual systems.
Maybe you're lucky on Wine, older versions of TurboCAD seem to run somehow, but be prepared for glitches...

---

### Post by oldfred on 2011-04-05
I do not use CAD anymore, but have been saving links. Do not know if any of the really work or not:


CADD
[http://ubuntuforums.org/showthread.php?t=1589156&highlight=cad](http://ubuntuforums.org/showthread.php?t=1589156&highlight=cad)
[http://www.tech-edv.co.at/lunix/CADlinks.html](http://www.tech-edv.co.at/lunix/CADlinks.html)
Modelers:
[http://www.tech-edv.co.at/lunix/MODlinks.html](http://www.tech-edv.co.at/lunix/MODlinks.html)
[http://courira.ca/en/blog/normand](http://courira.ca/en/blog/normand)
QCad is a computer-aided design (CAD) software package for 2D design and drafting
Bricscad from Bricsys, and ARES from Graebert. Both should offer Light (2D only) and Pro (ACIS modeling) versions by the end of 2010.
HeeksCAD is a free, open source, CAD application written Dan Heeks, Anyone can download it from [http://code.google.com/p/heekscad/](http://code.google.com/p/heekscad/)
[http://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Main_Page)
There is an active project called FreeCAD[1] which has been designed as a kind of CAD platform. It has a built in Python intepreter and everything about it can be altered using Python modules. It's massively extensible and powerful. The GUI frontend only provides access to a tiny tiny subset of what the backend can do.
[http://sourceforge.net/projects/free-cad/](http://sourceforge.net/projects/free-cad/)
In 3D Salome is still the more advance, but FreeCAD seems promising
CAELinux with open source mechanical engineering apps
[http://www.caelinux.com/CMS/](http://www.caelinux.com/CMS/)

GNU LibreDWG is a free C library to handle DWG files.
[http://www.gnu.org/software/libredwg/](http://www.gnu.org/software/libredwg/)
Home models
[http://www.sweethome3d.com/index.jsp](http://www.sweethome3d.com/index.jsp)

---

