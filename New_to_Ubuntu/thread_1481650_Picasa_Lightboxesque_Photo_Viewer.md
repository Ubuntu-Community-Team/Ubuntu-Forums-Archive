---
title: "Picasa Lightboxesque Photo Viewer"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by dpCalbee on 2010-05-12
I've just installed Picasa on 10.4 LTS and it works great. In Windows the viewer acts a bit like lightbox with transparencies. Is it because the linux version is running off wine that it can't do this?

I like feh, and Eog but the picasa veiwer is really handy sometimes. Is there a viewer that acts teh same way or a possibility this could be integrated in newer version of picasa?

---

### Post by Temposs on 2010-05-12
Yes, it's because Picasa is run through wine. It is not integrated into Linux like it is in Windows.

What functionality are you needing?

---

### Post by nikhil.parmar on 2011-04-21
Yes even i believe that Picasa PhotoViewer is the best. I have the solution to open all images with Picasa PhotoViewer in Ubuntu, you dont require wine for this.
Follow this guide..
Step 1. Download Picasa 3 from [http://picasa.google.com/linux](http://picasa.google.com/linux) and install it

Step 2. Download Picasa PhotoViewer from "http://www.caiacoa.de/Transfer/PicasaPhotoViewer-1.0.3.deb" (Link without "Quotes") and install it (sudo dpkg -i PicasaPhotoViewer-1.0.3.deb)

NOTE: You require to have Picasa 3 for running Picasa PhotoViewer.

Step 3. 
Suppose we have a file which name is XYZ.jpg.
Now

[LIST=1]
[*]Select the file
[*]Right Click onto it
[*]Select Open With
[*]Choose Other Application&#8230;
[/LIST]
Click more & in the text box paste this: '/usr/bin/PicasaPhotoViewer' [CENTER]
[/CENTER]
[LEFT]Now all jpg files will open with Picasa. Choose your familiar image file extensions & do it again & again.


Then all images will open with Picasa!!!


This worked for me........Hope Ur problem is solved.
[/LEFT]

---

### Post by Lipaugus Vociferans on 2012-05-26
[SIZE="2"]I'm having trouble installing Picasa Photoviewer in **Ubuntu 12.04**, I get this message: 
dpkg: error processing /home/leandro/Escritorio/PicasaPhotoViewer-1.0.3.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 17 package 'picasaphotoviewer':
 blank line in value of field 'Description'

Any ideas??:confused: 

Thanks in advance!!![/SIZE]

---

### Post by redmorning on 2012-05-27
> **nikhil.parmar said:**
> Yes even i believe that Picasa PhotoViewer is the best. I have the solution to open all images with Picasa PhotoViewer in Ubuntu, you dont require wine for this.
Follow this guide..
Step 1. Download Picasa 3 from [http://picasa.google.com/linux](http://picasa.google.com/linux) and install it

Step 2. Download Picasa PhotoViewer from "http://www.caiacoa.de/Transfer/PicasaPhotoViewer-1.0.3.deb" (Link without "Quotes") and install it (sudo dpkg -i PicasaPhotoViewer-1.0.3.deb)

NOTE: You require to have Picasa 3 for running Picasa PhotoViewer.

Step 3. 
Suppose we have a file which name is XYZ.jpg.
Now

[LIST=1]
[*]Select the file
[*]Right Click onto it
[*]Select Open With
[*]Choose Other Application&#8230;
[/LIST]
Click more & in the text box paste this: '/usr/bin/PicasaPhotoViewer' [CENTER]
[/CENTER]
[LEFT]Now all jpg files will open with Picasa. Choose your familiar image file extensions & do it again & again.


Then all images will open with Picasa!!!


This worked for me........Hope Ur problem is solved.
[/LEFT]
it works great (as expected)!
thank you very much nikhil.parmar!

---

