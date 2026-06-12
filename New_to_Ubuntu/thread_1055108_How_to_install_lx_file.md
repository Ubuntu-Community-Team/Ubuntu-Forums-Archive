---
title: "How to install lx file"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by oiler on 2009-01-30
Trying to use old 1000 series Lexmark printer on Xubuntu. Found PPD file and system recognizes and installs printer and PPD file but returns message"Printer requires lx program but it is not currently installed".  Found lx.c which I think is correct.  How do you install this?  See below for info from lx.c

Lexmark 1000 Black & white driver
 *
 * Author: Jean-Francois Moine
 *	mailto:moinejf@free.fr
 *	http:moinejf.free.fr
 *
 * Last update: 2003/03/28
 *
 * Adapted from lm1100 by Tim Engler <tim@burntcouch.com>
 *	[http://www.burntcouch.com/lexmark/](http://www.burntcouch.com/lexmark/)
 *
 * License: GPL
 *
 * Generation:
 *	cc -O2 lx.c -o lx
 *
 * Usage:
 *	Create the script 'lp':
 *		!/bin/sh
 *		gs -q -sDEVICE=pbmraw -r288 \
 *		-dNOPAUSE -dSAFER -dBATCH \
 *		-sOutputFile=- \
 *		$1 | lx > /dev/lp0
 *	then call:
 *		lp <file>.ps

Sure appreciate the patience shown me in my fumbling efforts with Linux.  Running Intrepid Ibex (Xubuntu 8.10)

Thanks,

Oiler

---

### Post by taurus on 2009-01-30
Make sure you are in the same directory where lx.c is (otherwise, you have to include the whole path), then compile it and move the binary to /usr/bin so it's on your path.  

```
sudo apt-get update
sudo apt-get install build-essential
cc -O2 lx.c -o lx
sudo mv lx /usr/bin
```
Now, create a script

```
gksudo mousepad /usr/bin/lp
```
and add the following lines to that new file.

```

#!/bin/bash
gs -q -sDEVICE=pbmraw -r288 \
-dNOPAUSE -dSAFER -dBATCH \
-sOutputFile=- \
$1 | lx > /dev/lp0

```
Ave it and exit.  Now, you can print a postscript file with

```
lp filename.ps
```

---

### Post by oiler on 2009-01-30
Please check below contents of script created for accuracy.  The process of get, install, etc. seemed to run perfectly with the system going on-line to check for updates, etc.



ELF
#!/bin/bash
gs -q -sDEVICE=pbmraw -r288 \
-dNOPAUSE -dSAFER -dBATCH \
-sOutputFile=- \
$1 | lx > /dev/lp0


If this is okay I am assuming printing is accomplished from terminal command line.  Is this for postscript files only?  If so how do you create postscript files from other documents you desire to print?

---

### Post by taurus on 2009-01-30
According to the instruction from your first post, it says postscript, .ps.  You can try to print a doc to see if that works.  I can't check because the link that you have provided is dead.

---

### Post by oiler on 2009-01-30
Tried to print a couple documents.  Below is result.  

Oiler


caf@caf-desktop:~$ lp Lexmark-1000-lm1100.ppd
/usr/bin/lp: line 1: ELF: command not found
/usr/bin/lp: line 6: /dev/lp0: Permission denied
caf@caf-desktop:~$ 
caf@caf-desktop:~$ lp Daily_Business.pdf
/usr/bin/lp: line 1: ELF: command not found
/usr/bin/lp: line 6: /dev/lp0: Permission denied
caf@caf-desktop:~$

---

### Post by taurus on 2009-01-30
You need to edit that file and remove the first line because it shouldn't be there.

```
ELF
```
Then save it.  Now, what are the outputs of these commands from a terminal?

```
ls -la /dev/lp0
id
```

---

### Post by oiler on 2009-01-30
Here are outputs after editing.



caf@caf-desktop:~/Desktop$ ls -la /dev/lp0
crw-rw---- 1 root lp 6, 0 2009-01-30 10:14 /dev/lp0
caf@caf-desktop:~/Desktop$ id
uid=1000(caf) gid=1000(caf) groups=4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare),1000(caf)
caf@caf-desktop:~/Desktop$

---

### Post by taurus on 2009-01-30
Have you tried to reconfigure your printer again from System -> Administration -> Printing?

---

### Post by oiler on 2009-01-30
System -> Administration -> Printing not shown on XFCE desktop.  Printers are configured from Applications>Settings>Printing.  Properties shown seem to be correct as to connection, etc.  Output below resulted from print attempt from terminal:

caf@caf-desktop:~/Desktop$ lp lx.c
/usr/bin/lp: line 5: /dev/lp0: Permission denied
caf@caf-desktop:~/Desktop$ lp Lexmark-1000-lm1100.ppd
/usr/bin/lp: line 5: /dev/lp0: Permission denied
caf@caf-desktop:~/Desktop$

---

### Post by taurus on 2009-01-30
Where did you download the lx.c because the timestamp looks real old, 2003?

Have you checked out Lexmark's site to see if there is at least a newer driver for your printer that works with Linux?

---

### Post by oiler on 2009-01-30
Your right, but this is an old printer.  The only drivers Lexmark has refer to Unix/Linux and are listed as "AIX" with several versions up thru 5.1.  Lexmark is not very supportive of Linux and I may be flogging a dead mule here but apparently some folks have gotton this model to work on some Linux versions. I am home now and do not have access to the Linux machine as it is at office.  I would like to send you the .ppd driver that started this for your inspection next week.

Thanks so much for your interes.  It is appreciated.

---

