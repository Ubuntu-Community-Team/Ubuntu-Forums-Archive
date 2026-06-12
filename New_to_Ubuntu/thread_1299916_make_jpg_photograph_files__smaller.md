---
title: "make jpg photograph files  smaller"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-10-24
Hi Ubuntu Community:

I have a nice digital camera that makes jpg files that are typically 800Mb. I might take 24-50 of pictures at a time.

I want a shell script or some software that will 
[LIST]
[*]read all of the jpg files in a specified folder
[*]process each of those jpg files so that the output of the program yields NEW files in a specified folder ... where each file is 90Kb.
[/LIST]

How can I do this?

Thank you! :)
Phil Smith
Duluth, GA

---

### Post by kaibob on 2009-10-24
There are a lot of ways to do what you want. The simplest is probably nautilus image converter. It doesn't allow you to choose file size, but it does allow you to select image size in pixels, which achieves the same result. Nautilus image converter is in the repo's; some screen shots can be seen at:

[http://www.bitron.ch/software/nautilus-image-converter.php](http://www.bitron.ch/software/nautilus-image-converter.php)

You may also want to look at phatch: 

[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by steveneddy on 2009-10-24
Here's another suggestion:

[http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux](http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux)

---

### Post by laidback on 2009-10-24
Wow..this is just great. I never knew that the Nautilus/resize feature was available (silly me), just fantastic. So useful if you want smaller versions to send to friends via email, and batch processing too...Ubuntu is just so wonderful, as is the forum.

Many thanks.

Laidback

---

### Post by Old Jimma on 2009-10-25
WOW!!!

Thanks to kaibob and steveneddie for tips on such great software already packaged with Ubuntu!!

:P

Phil Smith
Duluth, GA

---

### Post by jrrader on 2009-10-25
If you're comfortable with terminal Imagemagick is a shell application that you can use to pretty much do anything with your pictures.  I write scripts that use imagemagick to resize and watermark my professional photos for use online.

---

### Post by cmcanulty on 2011-12-31
I installed the nautilus image converter but it doesn't show up in context menu, any other way to use it?

---

### Post by lkraemer on 2011-12-31
I prefer Irfanview, and  use the Batch feature.  It works wonderful!

[http://www.irfanview.com/](http://www.irfanview.com/)
Version 4.32

Irfanview also has lots of Plugins.  Check them out!


lk

---

### Post by fooman on 2011-12-31
> **cmcanulty said:**
> I installed the nautilus image converter but it doesn't show up in context menu, any other way to use it?

have you tried logging out and back in again to see if its there (should be)?

---

### Post by Bartender on 2011-12-31
> **lkraemer said:**
> I prefer Irfanview, and  use the Batch feature.  It works wonderful!

[http://www.irfanview.com/](http://www.irfanview.com/)
Version 4.32

Irfanview also has lots of Plugins.  Check them out!


lk

I don't see a Linux version.  Are you running it via Wine?

---

### Post by aeronutt on 2011-12-31
> **cmcanulty said:**
> I installed the nautilus image converter but it doesn't show up in context menu, any other way to use it?

Nautilus image converter doesn't work well with the latest versions of Nautilus, and hasn't had an update in a few years. I recently found 'nautilus-image-manipulator' in the repositories, and it works well.

---

### Post by aeronutt on 2011-12-31
Check out Fred's scripts based on imagemagick.

[http://www.fmwconcepts.com/imagemagick/index.php](http://www.fmwconcepts.com/imagemagick/index.php)

---

### Post by lkraemer on 2012-01-01
Bartender,
Yes I am running it in Wine 1.1.42 on Debian 6.0 "Squeeze".
[B]

Install WINE 1.1.42 in Ubuntu 10.04 LTS.[/B]

Wine needs winecfg ran so that .wine is created in /home/user,
so the subdirectory exists, If Wine has been configured. Skip to **1A** Below:


1.  This is with a clean configuration directory.

```

winecfg

```

**1A:**
Once the .wine directory is built the configuration tool will start, and you can set a virtual desktop in the graphics tab if you wish.

Install the MFC42.dll from a Windows XP box, if it does not already exist, or install WineTricks, then install the included dll.

You will need a native MFC42.dll in ~/.wine/drive_c/windows/system32 before the install will work.


2.  Installing IrfanView with:

```

wine iview432_setup.exe

```

Delete the I_view32.ini file in ~/.wine/drive_c/Program Files/IrfanView
(I don't have any notes about doing this on Debian, so I might have skipped this step....and it might not be needed nowdays....
as these notes were from a Ubuntu 8.04 LTS install.)


3.  Change the ICON by Right clicking on the Desktop Icon and then clicking on the displayed ICON. Change to /usr/share/pixmaps/wine.svg
    OR Download Irfanview.PNG and copy to /usr/share/icons/hicolor/48x48/apps/
    Other ICON choices are located at /usr/share/icons and lower subdirectories.....


Irfanview works wonderful!  Check out the CAD Plugin for OCR!


lk

---

### Post by coldraven on 2012-01-01
+1 Phatch
You can create your own actions, even specify a maximum file size, and where to save the results.

---

