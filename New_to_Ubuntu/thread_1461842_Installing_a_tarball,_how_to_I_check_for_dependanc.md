---
title: "Installing a tarball, how to I check for dependancies?"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by kichigai_dave on 2010-04-24
I found the Graveman tarball that I wanted to install. However after reading the Install file, there is a whole list of dependancies that need to be installed. How do I check for these and verify that I have them or not?  I've listed the install instructions below:

                                       [LEFT]INSTALL INSTRUCTION[/LEFT]
    -------------------
    
    [LEFT]graveman! is free software; you can redistribute it and/or modify it under the terms of the[/LEFT]
    [LEFT]GNU General Public License as published by the Free Software Foundation; either version 2, or[/LEFT]
    [LEFT](at your option) any later version.[/LEFT]
    
    [LEFT]graveman! is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without[/LEFT]
    [LEFT]even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU[/LEFT]
    [LEFT]General Public License for more details.[/LEFT]
    
    [LEFT]You should have received a copy of the GNU General Public License along with program; see the[/LEFT]
    [LEFT]file COPYING. If not, write to the Free Software Foundation, Inc., 59 Temple Place -[/LEFT]
    [LEFT]Suite 330, Boston, MA 02111-1307, USA. [/LEFT]
    
    [LEFT]Copyright (C) 2004, 2005 Sylvain Cresto <scresto@gmail.com>[/LEFT]
    
    [LEFT]Copying and distribution of this file, with or without modification,[/LEFT]
    [LEFT]are permitted in any medium without royalty provided the copyright[/LEFT]
    [LEFT]notice and this notice are preserved.[/LEFT]
    
    
    
    [LEFT]Dependencies[/LEFT]
    ============
    [LEFT]  gtk+ version >= 2.4.0      [http://www.gtk.org](http://www.gtk.org)[/LEFT]
    [LEFT]  glib version >= 2.4.0      [http://www.gtk.org](http://www.gtk.org)[/LEFT]
    [LEFT]  libglade version >= 2.4.0  [http://ftp.gnome.org/pub/GNOME/sources/libglade/2.4/](http://ftp.gnome.org/pub/GNOME/sources/libglade/2.4/)[/LEFT]
    [LEFT]  libid3tag version >= 0.15  [http://sourceforge.net/project/showfiles.php?group_id=12349](http://sourceforge.net/project/showfiles.php?group_id=12349)[/LEFT]
    [LEFT]  libmad version >= 0.15     [http://sourceforge.net/project/showfiles.php?group_id=12349](http://sourceforge.net/project/showfiles.php?group_id=12349)[/LEFT]
    [LEFT]  libogg version >= 1.0      [http://www.vorbis.com](http://www.vorbis.com)[/LEFT]
    [LEFT]  libvorbis version >= 1.0   [http://www.vorbis.com](http://www.vorbis.com)[/LEFT]
    [LEFT]  libFLAC >= 1.1.0           [http://flac.sourceforge.net](http://flac.sourceforge.net)[/LEFT]
    [LEFT]  libmng >= 1.0.0            [http://libmng.sourceforge.net/](http://libmng.sourceforge.net/)[/LEFT]
    [LEFT]  cdrecord version >= 2.0    [ftp://ftp.berlios.de/pub/cdrecord/](ftp://ftp.berlios.de/pub/cdrecord/)[/LEFT]
    [LEFT]  readcd version >= 2.0      [ftp://ftp.berlios.de/pub/cdrecord/](ftp://ftp.berlios.de/pub/cdrecord/) [/LEFT]
    [LEFT]  mkisofs version >= 2.0     [ftp://ftp.berlios.de/pub/cdrecord/](ftp://ftp.berlios.de/pub/cdrecord/) [/LEFT]
    [LEFT]  dvd+rw-format >= 4.8       [http://fy.chalmers.se/~appro/linux/DVD+RW/tools/](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/)[/LEFT]
    [LEFT]  growisofs >= 5.10          [http://fy.chalmers.se/~appro/linux/DVD+RW/tools/](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/) [/LEFT]
    [LEFT]  cdrdao >= 1.1.9            [http://sourceforge.net/projects/cdrdao/](http://sourceforge.net/projects/cdrdao/)[/LEFT]
    [LEFT]  sox >= 12.17.0             [http://sox.sourceforge.net](http://sox.sourceforge.net)[/LEFT]
    [LEFT]  zlib >= 1.1.4              [http://www.gzip.org/zlib](http://www.gzip.org/zlib)[/LEFT]
    
    
    [LEFT]Basic Installation[/LEFT]
    ==================
    [LEFT]  First, make sure you have compiled and installed the dependencies.[/LEFT]
    [LEFT]  Most recents Linux distributions will include them, except maybe[/LEFT]
    [LEFT]  for libid3tag.[/LEFT]
    
    [LEFT]  Type:[/LEFT]
    [LEFT]  ./configure[/LEFT]
    [LEFT]  make[/LEFT]
    [LEFT]  make install (may require root privileges)[/LEFT]
    
    [LEFT]  After all type: graveman[/LEFT]
    
    
    [LEFT]  Please report any problems to scresto _at_ gmail.com[/LEFT]
    
   
 
END INSTRUCTIONS----------------------------

:confused:

---

### Post by jaco223 on 2010-04-24
Go to the link and download and install the .deb file
should be a lot easier than using the tarball.

[http://archive.ubuntulinux.org/ubuntu/pool/universe/g/graveman/](http://archive.ubuntulinux.org/ubuntu/pool/universe/g/graveman/)

Hope this helps.

Jaco

---

### Post by kichigai_dave on 2010-04-24
> **jaco223 said:**
> Go to the link and download and install the .deb file
should be a lot easier than using the tarball.

[http://archive.ubuntulinux.org/ubuntu/pool/universe/g/graveman/](http://archive.ubuntulinux.org/ubuntu/pool/universe/g/graveman/)

Hope this helps.

Jaco
:guitar:
Wow, thanks........uh that was much easier! Wish I would have realized that a lot earlier!

---

### Post by jaco223 on 2010-04-24
> **kichigai_dave said:**
> :guitar:
Wow, thanks........uh that was much easier! Wish I would have realized that a lot earlier!

Glad you got it installed!

Jaco

---

