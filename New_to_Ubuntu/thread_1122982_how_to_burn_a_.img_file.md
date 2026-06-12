---
title: "how to burn a .img file"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by patchido on 2009-04-11
well... i have 3kb and it wount let me burn the disc :S anyone know of a program that will?

---

### Post by llamabr on 2009-04-11
It should.  What's the error?

You can burn an iso (I think .img is just another naming convention for a disk image) using cdrecord.  Or any other program that comes with your ubuntu distro.

---

### Post by Michael.Godawski on 2009-04-11
hi, 
have a look at :

[LIST]
[*][http://lj4newbies.blogspot.com/2007/06/mount-iso-cuebin-nrg-img-mdf-files-in.html](http://lj4newbies.blogspot.com/2007/06/mount-iso-cuebin-nrg-img-mdf-files-in.html)
[*][http://ubuntuforums.org/showthread.php?t=215386](http://ubuntuforums.org/showthread.php?t=215386)
[*][http://www.ubuntugeek.com/ccd2iso-convert-clonecd-disc-image-img-format-to-standard-iso-iso.html](http://www.ubuntugeek.com/ccd2iso-convert-clonecd-disc-image-img-format-to-standard-iso-iso.html)
[/LIST]
But I also think k3b should do it...

---

### Post by kwacka on 2009-04-11
I've used K3B to burn .img files.

Just make sure that when you are browsing for the file you set the filter to 'All files' instead of image files.

I've also heard that downloaded DVD video files can be re-named from 'x.img' to 'x.iso' to burn them.

---

### Post by thunder04 on 2010-04-08
I'm running Xubuntu and it seems that K3b crashes just before the burn process starts.

I found a cool program that'll convert .img files to .iso files called ccd2iso (available through APT/Synaptic).

I used this tool to convert the .img files I needed to burn, burned the newly created .iso files with Brasero, and volla! :D

---

