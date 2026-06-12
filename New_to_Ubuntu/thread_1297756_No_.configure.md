---
title: "No ./configure?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by TironN on 2009-10-22
Hey guys. I have been attempting to compile and install Comical for reading .cbr

Now I have downloaded the latest source from their website ([http://comical.sourceforge.net/](http://comical.sourceforge.net/)). I have downloaded wxWidgets using the Synaptics Package Manager but after running:
```
tar xvfz Comical-0.8.tar.gz
cd Comical-0.8
./configure

```Well there isn't any configure file.
If possible could I put it in /opt/comcial?
Thanks

---

### Post by ethoxyethaan on 2009-10-22
what are the files inside the directory?

ls -la

---

### Post by TironN on 2009-10-22
Comical.pbproj
Comical Icons
src
unrar
unzip
AUTHORS
ChangeLog
Comical.kdevelop
Comical.kdevelop.filelist
ComicalSetup.iss
COPYING 
Makefile
Makefile.mingw
Makefile.vc
README
TODO

---

### Post by NCLI on 2009-10-22
Right-click "ComicalSetup.iss," choose "Properties," choose the "Permissions" tab, then tick the box next to "Allow executing file as program."

Finally, just drag the file into a terminal, and execute it as root. 

So, if ComicalSetup.iss is in your home directory, you'd do: 

```
sudo '~/ComicalSetup.iss'
```
"~" can be used in place of "/home/YourUsername/"

---

### Post by TironN on 2009-10-22
So just that line of code straight in?
So I opened the folder its in and then ran the code and I got command not found

---

### Post by NCLI on 2009-10-22
[COLOR=Silver]Hmm, try doing "sudo su" first, then dragging the file into your terminal, and executing it.[/COLOR]

EDIT: Strike that, there is a makefile, and I am an idiot. You only have to run ./configure if there is no makefile, but thankfully, there already is one. Just skip the ./configure step. The next steps would be:

```
make
sudo make install
```

---

### Post by TironN on 2009-10-22
```

fergus@tiron-laptop:~$ sudo su '/home/fergus/comical-0.8/ComicalSetup.iss' 
Unknown id: /home/fergus/comical-0.8/ComicalSetup.iss
fergus@tiron-laptop:~$ sudo '/home/fergus/comical-0.8/ComicalSetup.iss'
/home/fergus/comical-0.8/ComicalSetup.iss: 1: Syntax error: ";" unexpected
fergus@tiron-laptop:~$ 

```:(

Still no love

---

### Post by nothingspecial on 2009-10-22
Does it have to be comical?

Have you tried comix?

---

### Post by renkinjutsu on 2009-10-22
Have you read the README?
what's it say?

---

### Post by TironN on 2009-10-22
I'm looking at comix now but I still want to defeat this issue

---

### Post by TironN on 2009-10-22
Readme:
> ------------------------------------------------
Comical - The Comic Book Archive reader
------------------------------------------------

Finally - a cross-platform, open-source CBR and CBZ reader!  Read your favorite
scanned comic books and graphic novels with Comical's absurdly easy GUI and
in-your-face double page display!

Nifty Features:
* Single-Page or Double-Page display modes.
* Several zoom modes - Fit, Fit-to-Width, Fit-to-Height, Original, and Custom.
* Crisp image scaling with algorithms adapted from FreeImage 3.
* Autodetects double pages scanned together and displays it accordingly.
* Page rotation.
* Full-Screen mode.
* Left-to-Right or Right-to-Left browsing.
* Displays JPG, GIF, and PNG images.
* Supports RAR(.cbr) and ZIP(.cbz) comic book archives
* Supports all encrypted RAR archives as well as ZIP archives with pkzip 2.04g
encryption.

What you need to compile from source:
wxWidgets 2.6.0 or later
gcc 3.3 or later

Acknowledgements:

Cross-platform magic and GUI Widgets provided by:
wxWidgets ([http://www.wxwindows.org](http://www.wxwindows.org))

Image resizing provided by:
FreeImage ([http://freeimage.sourceforge.net/](http://freeimage.sourceforge.net/)).

JPEG support provided by:
Independent JPEG Group ([http://www.ijg.org/](http://www.ijg.org/))

ZIP decompression provided by:
Copyright (C) 1998-2005 Gilles Vollant.

RAR decompression provided by RARLabs.  You cannot use the unrar source to
re-create the RAR compression algorithm, which is proprietary.  Distribution
of modified Unrar source in separate form or as part of other software is
permitted, provided that it is clearly stated in the documentation and source
comments that the code may not be used to develop a RAR compatible archiver.

-------------------------------------------------------------------------------
Copyright (c) 2003-2006 James Athey

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

In addition, as a special exception, the author gives permission to link the
code of his release of Comical with Rarlabs' "unrar" library (or with modified
versions of it that use the same license as the "unrar" library), and
distribute the linked executables. You must obey the GNU General Public License
in all respects for all of the code used other than "unrar". If you modify this
file, you may extend this exception to your version of the file, but you are
not obligated to do so. If you do not wish to do so, delete this exception
statement from your version.

So yeah. I installed Comix and it looks fine so now its all about proving I can do it

---

