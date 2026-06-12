---
title: "Getting songs off an Ipod?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-11-29
Hey,

I have an 80GB 5th Gen Ipod Video with about 4GB worth of stuff on it.  I also have recently been forced by a Windows Update screwup to restore my Vista partition back to factory settings, deleting all my songs and leaving the Ipod as the only place for them.  I seem to be having trouble trying to use any of the Linux tools available to get my songs OFF the iPod and onto the PC.  I can't use iTunes, because iTunes will overwrite the iPod with it's (blank) library as soon as i plug it in. I need to get the songs ON to the PC so i can import them into iTunes BEFORE connecting the iPod. I've tried to use Rhthmbox, Banshee and Amarok, and none of them seem to want to actually transfer the files, jsut add them to my libary (Amarok throws errors about encryption).   I've also tried gtkpod  but that is throwing errors about invalid file format... or it just crashes when i try. im in 9.04

---

### Post by SuperSonic4 on 2009-11-29
gtkpod usually works

---

### Post by jmcgovern on 2009-11-29
I've tried to us gtkpod several times.  I keep getting an error that says 'template does not match file type', and nothing copies.

---

### Post by Bastila22 on 2009-12-01
ifunbox works great

---

### Post by Some Penguin on 2009-12-01
I might be missing something here, because I don't have an iPod Video, but...

1- It seems that you're just interested in copying over the files, not removing any DRM or switching to another codec (because you want to re-import them using iTunes, which probably should handle its own DRM nicely).

2- The iPod Video probably supports the USB Mass Storage standard.

3- You presumably already have a cable that connects the iPod to a USB port.


If all the above is correct, you should be able to simply connect the iPod, mount it (it is likely to have a FAT32 filesystem, so
  'mount -t vfat /dev/sd[foo] /mnt/<some empty directory>'
should work if it's not automounting)

and then copy all the .m4a / .m4p / .m4v files to somewhere accessible to Vista (which will use ntfs-3g).  This won't copy the database of playlists, but iTunes should be able to recreate it, one would think.

For finding and copying those files, something like
 
   find /mnt/<mount point> -name *.m4* -print | xargs cp /to/destination

Add any other extensions of files you'd also want to keep.

(recursively search for all .m4* files;  'xargs' is used to accept output and feed it to a command.   'find | xargs' is a useful idiom for handling both recursion and for what might otherwise be very long command lines).

Then you reinstall iTunes and import the *.m4* files.

---

