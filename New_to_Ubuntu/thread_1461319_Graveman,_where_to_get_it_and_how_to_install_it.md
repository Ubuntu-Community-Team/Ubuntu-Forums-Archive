---
title: "Graveman, where to get it and how to install it?"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by kichigai_dave on 2010-04-24
I was looking to get some different burning apps. Tried Kbe, gnombaker, etc... all too slow. It's taking me about 16 minutes to burn a DVD. I've got a 22x burner it should be at least half that. I wanted to try "graveman", but I can't find it and don't know how to install it if I did. Any suggestions on different apps or where I can get graveman and how to install it?

Thanks,

---

### Post by kichigai_dave on 2010-04-24
Oh, yeah..... details:

Xubuntu 8.04 Hardy Heron LTS
HP dvd1140 drive
anything else?

---

### Post by kerry_s on 2010-04-24
try xfburn instead, that's the burner for xfce. just look in synaptic.

---

### Post by ed-koala on 2010-04-24
Or, if you still want Graveman ...

[http://graveman.tuxfamily.org/telecharger.php?l=e]("http://graveman.tuxfamily.org/telecharger.php?l=e")

---

### Post by madmax75 on 2010-04-24
Yep, I had problems with Brasero and I replaced it with Xfburn. Works great for me!

---

### Post by kichigai_dave on 2010-04-24
Xfburn didn't show any actions for DVD's. All I saw was actions for CD's.
I went to the link for the graveman, how to you install from there? Those are Tarball files right? Never installed one before. I'll look into it. I'm sure there's something on here about them.

---

### Post by kichigai_dave on 2010-04-24
> **madmax75 said:**
> Yep, I had problems with Brasero and I replaced it with Xfburn. Works great for me!

Tried Xfburn, but it won't work for DVD's. It says it doesn't recognize the media or something. All I see are actions for CD's not DVD's. :confused:

---

### Post by Midnighter on 2010-04-24
Your burning speed is also dependant upon the media you use, not just your burner. Media are rated to burn at differing speeds.

---

### Post by kerry_s on 2010-04-24
> **kichigai_dave said:**
> Tried Xfburn, but it won't work for DVD's. It says it doesn't recognize the media or something. All I see are actions for CD's not DVD's. :confused:

what does it say under preferences> devices?

---

### Post by kichigai_dave on 2010-04-24
Yes, I know the media has specific speeds. However, my CD-RW drive reads at 16x max and my DVD-RW drive writes at 22x max, and my media says 16x. So I think I should be able to burn a full DVD in about 8 minutes. However it's taking double that.

---

### Post by kichigai_dave on 2010-04-24
Ok, I downloaded the graveman tarball and unpacked it to the desktop. However, the install file, didn't really make sense to me. Any help? I've listed the install file instructions here:

                                       INSTALL INSTRUCTION
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
    
    
    [LEFT]  Please report any problems to scresto _at_ gmail.com


END Instuctions
------------------------------------------------------------------


??:confused:
[/LEFT]

---

