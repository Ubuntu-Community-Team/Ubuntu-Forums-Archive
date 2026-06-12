---
title: "Dynusb how do I install it"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Russell Burrows on 2009-06-13
I kept haveing problems with trying to set autounmount for USB removable sticks and drives........grrrr.

They made it sound real simple but debian tells me no hot tools found and install stops and I positively had no idea what to do or what to run once I downloaded the i386 zipped file and I got to extract and thats as far as my install got....sigh.
I am running ubuntu 8.10 with a Celeron 1.7 GHz processor.

Is there some way to use synaptic package manager to get this program as doing or undoing tarballs has left me stumped.
Thank you. 

So I found this website  [http://organicdesign.co.nz/Auto-unmounting_USB_drives_in_Linux](http://organicdesign.co.nz/Auto-unmounting_USB_drives_in_Linux)

Auto-unmounting USB drives in Linux
From OrganicDesign Wiki
Jump to: navigation, search

One advantage that Windows has over Ubuntu is that USB devices such as memory sticks or external hard drives can be removed from the Windows machine by simply unplugging the USB device, without going through the "unmount" procedure first. Windows is not affected by this behaviour, however from the perspective of a Linux-like system, things can get into a real mess if external drives are removed from Windows machines without being properly ejected or unmounted first. Often this will lead to the drive not being able to be mounted in Ubuntu, requiring the user to connect the device to a Windows machine again and then unmounting it properly from there. This is a very important problem to fix, especially when the Linux system is to be used by non-technical people, for instance in classrooms or internet cafes.

DynUsb is a simple utility (only 13K of source code) which makes it safe to spontaneously pull devices out without any problem.

It seems to work really well, but if you've recently written to the drive, its still best to unmount in case not all cached data has been written.
Installation

Download the latest version from here. If you have a 32bit i386 architecture and are running a Debian based system such as Ubuntu or Mepis then you can install from the .deb, otherwise you'll need to download the source, unpack it and run make install in it's directory. It is extremely minimal and builds and starts almost instantly. :confused::confused::confused:

---

### Post by ashmew2 on 2009-06-13
Umm, at the bottom of the site it also says that you can also install it from a .deb file..

Here's the link to it : [http://sourceforge.net/project/downloading.php?group_id=121562&filename=dynusb_0.2.0-1_i386.deb](http://sourceforge.net/project/downloading.php?group_id=121562&filename=dynusb_0.2.0-1_i386.deb)

Just save it to desktop and double click it to install dynusb.

---

### Post by Russell Burrows on 2009-06-13
> **ashmew2 said:**
> Umm, at the bottom of the site it also says that you can also install it from a .deb file..

Here's the link to it : [http://sourceforge.net/project/downloading.php?group_id=121562&filename=dynusb_0.2.0-1_i386.deb](http://sourceforge.net/project/downloading.php?group_id=121562&filename=dynusb_0.2.0-1_i386.deb)

Just save it to desktop and double click it to install dynusb.

Already tried that and I also tried extracting and Debi installer tells me no hottool.

I went and Altavista and googled and it comes up that Ubuntu no longer uses hottools so I am back to zip.

Thank you.

---

