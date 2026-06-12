---
title: "how do I make a compressed iso?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-30
I want to use linux to image a windows hard drive and save the .iso to a dvd disk how do I do that? windows hard dive is 200gb my dvd is 4.1gb. Remastersys has compresstion for the iso but dont want a copy of the live cd along with the windows image. If I use the dd if=/dev/hda of=/tmp/hardrive.iso bs=1024 command the image is to large for the dvd. someone told me i could try

mkisofs -V LABEL -r DIRECTORY | gzip > cdrom.iso.gz—creates a compressed ISO for easy backup (replace the italicized sections with your CD label and directory, of course)

but i just want to be able to put in the cd and use the live cd with
dd if=/CDROM/hardrive.iso of=/dev/hda
to restore the image

Someone else told me to try a CramFs but they nor I know know how to make one.

---

### Post by rcayea on 2011-01-30
Maybe investigate to see if UCK (Ubuntu Customization Kit) will do the job.

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

