---
title: "Installing latest version of SCID chess database"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by mushypeas on 2011-02-27
Hi

The version of SCID chess database in the ubuntu software manager is very out of date. The latest version is here ([http://scid.sourceforge.net/download.html](http://scid.sourceforge.net/download.html)) but I have no idea how to install (sorry - I am new to ubuntu).

Does anyone know how to get ubuntu to link to the latest version or install the latest version?

Thanks

Mushypeas

---

### Post by davidmohammed on 2011-02-27
at the bottom of the web-page was these instructions...

"To compile Scid for Linux or other Unix operating systems, you must have Tcl/Tk (8.5 or newer is required) and a C++ compiler. You should be able to compile Scid just by typing ./configure and then make in the scid directory. If that does not work, you may need to edit the Makefile."

can I suggest you install the following

sudo apt-get install build-essential

then

sudo apt-get install tcl8.5

assuming you have downloaded the database in "Downloads"

using nautilus (filemanager)  double click the file located in Downloads - choose the extract option

cd Downloads
cd <folder extracted to>

type

./configure

make

ensure no errors are reported then install with

sudo make install

---

### Post by mushypeas on 2011-02-27
Thanks. I had an error but will persevere and let you know how I get on

---

### Post by bogdarnet on 2011-05-23
Seems the answer to the below issue is here:
[http://ubuntuforums.org/archive/index.php/t-1175019.html](http://ubuntuforums.org/archive/index.php/t-1175019.html)

Tried following davidmohammed's instructions (earlier this thread), and all went fine until ./configure:

./configure
configure: Makefile configuration program for Scid
    Tcl/Tk version: 8.5
    Your operating system is: Linux 2.6.32-31-generic-pae
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.5 library: /usr/lib
    Location of Tk 8.5 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
    Using Makefile.conf.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.

---

