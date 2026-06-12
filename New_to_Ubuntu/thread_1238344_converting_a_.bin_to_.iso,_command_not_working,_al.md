---
title: "converting a .bin to .iso, command not working, alternatives?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-08-12
_Skip this section, solved - read post 3 for solution. New problem under_ -------

Hi, i need to mount a .bin file so have searched how and looks like it needs to be converted to a .iso file first. I have downloaded bchunk upon reading others success with the software. This is the command i used (replacing the file names with the appropriate file locations+names -

> I used bchunk to convert my bin/cue to iso
Code:

sudo apt-get install bchunk

Code:

bchunk filename.bin filename.iso myconvertedfile



but the terminal just displays -

> mckenzie@mckenzie-home:~$ bchunk /media/680gb/rct/tt.bin /media/680gb/rct/tt.iso myconvertedfile
binchunker for Unix, version 1.2.0 by Heikki Hannikainen <hessu@hes.iki.fi>
	Created with the kind help of Bob Marietta <marietrg@SLU.EDU>,
	partly based on his Pascal (Delphi) implementation.
	Support for MODE2/2352 ISO tracks thanks to input from
	Godmar Back <gback@cs.utah.edu>, Colas Nahaboo <Colas@Nahaboo.com>
	and Matthew Green <mrg@eterna.com.au>.
	Released under the GNU GPL, version 2 or later (at your option).

Could not open CUE /media/680gb/rct/tt.iso: No such file or directory


I thought the command would create the .iso file? what am i doing wrong? and is there a way to get it working?
[B]
SOLVED[/B]
-----------------------------------------
[B]
New Problem[/B]
Ok so now i have a .isz file which i need to extract or mount. The software i used for the .bin doesnt work, any solutions?

cheers

---

### Post by phantomjoker on 2009-08-12
**wait, is this due to the fact that i located the hdd as /media/680gb and not /dev/sdb...?**

---

### Post by phantomjoker on 2009-08-12
alls good, i ended up using AcetoneISO from [http://sourceforge.net/projects/acetoneiso2/files/AcetoneISO/AcetoneISO2%202.0.2/acetoneiso2_20080508-1_i386.deb/download]("http://sourceforge.net/projects/acetoneiso2/files/AcetoneISO/AcetoneISO2%202.0.2/acetoneiso2_20080508-1_i386.deb/download")

mounts .bin and .iso and does a lot more, with a GUI! my favorite :)

---

### Post by phantomjoker on 2009-08-12
new problem - converting/mounting or extracting a .isz file?

---

### Post by MrWES on 2009-08-12
> **phantomjoker said:**
> alls good, i ended up using AcetoneISO from [http://sourceforge.net/projects/acetoneiso2/files/AcetoneISO/AcetoneISO2%202.0.2/acetoneiso2_20080508-1_i386.deb/download]("http://sourceforge.net/projects/acetoneiso2/files/AcetoneISO/AcetoneISO2%202.0.2/acetoneiso2_20080508-1_i386.deb/download")

mounts .bin and .iso and does a lot more, with a GUI! my favorite :)

I take it you installed the 10 packages to satisfy the dependencies? Or was that available in the repositories?

Update: My silly mistake, I forgot Deb package installer will install the dependencies too.

Bill

---

### Post by bulletxt on 2009-08-12
Latest AcetoneISO release can be found at official website:

[http://www.acetoneteam.org](http://www.acetoneteam.org)

There is also the Ubuntu deb package.

---

### Post by MrWES on 2009-08-13
> **bulletxt said:**
> Latest AcetoneISO release can be found at official website:

[http://www.acetoneteam.org](http://www.acetoneteam.org)

There is also the Ubuntu deb package.


Wow, I just checked it out -- I see on the menu it rips DVD's to Xvid avi? Gonna have to give that a spin. Anyone else with more experience on this?

Bill

---

### Post by bulletxt on 2009-08-13
> **MrWES said:**
> Wow, I just checked it out -- I see on the menu it rips DVD's to Xvid avi? Gonna have to give that a spin. Anyone else with more experience on this?

Bill

Yes it works, it might not give you a lot of features while converting it to xvid but it's meant on purpose to be easy as 1 click. And as you can see there are a lot of features in AcetoneISO :)

---

