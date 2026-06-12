---
title: "Saving and moving files in Scribus"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Stunt Double on 2009-05-25
I'm using Scribus with 8.04. It works well except that when I save files in .sla or .sla.gz format, and then attempt to move those files via a flash drive, the images are lost.
  The Image boxes are there but empty. 
  All text is properly saved
 Exporting the files to .pdf or .eps does preserve the images.
The other computers that I am moving the files to are also running 8.04 and the same version of Scribus.
  I have tried it with 3 separate flash drives, and in each case, the images were lost.
  Is there a way to preserve the entire file in .sla so it can be moved to another computer for further refinement and printing?

 Thanks

---

### Post by achase79 on 2009-07-01
Scribus does not embed images into it's .sla files.  All it does is marks the links to files much like a web page does.

to edit the file somewhere else you will have to include the image files with the sla file.  Using File -> Collect for Output will put everything in one folder.

---

