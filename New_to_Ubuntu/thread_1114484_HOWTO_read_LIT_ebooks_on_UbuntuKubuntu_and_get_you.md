---
title: "HOWTO: read LIT ebooks on Ubuntu/Kubuntu and get your ebooks onto your Android phone!"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-04-02
Hi, all!

I've been fighting with this since I got my T-Mobile G1 back last October.  I have a massive ebook collection; most of it is in LIT format with some HTML and Mobipocket formatting mixed in.  I used to use Microsoft Reader on my Windows Mobile phone, but when I switched to the G1 running Android, I had no idea how to get my books onto it (which completely SUCKED, because 60% of my use of my previous smartphone had been as a portable ebook reader).

Here's the solution!!

1. Get ConvertLit: Install package "convlit" in Adept Package Manager or in a terminal.

2. Get Calibre:  [http://calibre.kovidgoyal.net/download_linux](http://calibre.kovidgoyal.net/download_linux)
Follow the instructions for binary installation; there should be a snippet there that you can cut-and-paste into a terminal.

3. Run "calibre" or "calibre &" from a terminal.

4. When Calibre opens, you'll see an option to point to your ebook directory.  Give Calibre the default directory for your ebooks.

5. Add a given ebook in LIT format to Calibre's library (I picked the Hitchhiker's Guide to start with from my 'Adams, Douglas' folder inside my ebooks directory).

6. Hit the "Convert Ebooks" button at the top.  Make sure "EPUB" is the selected output format in the little dropdown on the right of the main Calibre window.

7. In the popup, you can either fiddle with the options, or just convert it to EPUB straight off.

8. My converted Hitchhiker book showed up on my Desktop, not in the directory I had stored the book in, so go look there if you're trying to find it.  Make sure you've actually SAVED it; there's a "Save to Disk" button at the top of the main Calibre window.

9. Get FBReaderJ.  Make sure your G1 isn't plugged into your computer or mounted, because there will be a problem downloading the Android package to the SD card if so.  Use your browser or Google Search on your phone to Google "fbreaderj".  Open up the top result to download FBReaderJ (the Android package).  Android packages have the .APK extension.  

10.  Use your file explorer (I downloaded ASTRO file explorer from the Android Market; it's free) to find the downloaded .apk. Again, ensure that your phone isn't plugged in, because you can't access the SD card through a file explorer if your SD card is mounted to your computer.  I found the .apk in /sdcard/downloads.

11.  Click on the downloaded file and install it.  You may have to change settings to allow non-Market applications to be installed.  Launch the app to ensure it installed.

12.  Now, close the app, and mount your phone to your computer.  Do so by connecting your phone to your computer via a USB cable.  You should get the notification at the top "USB connected".  Open that notification; it should say something like "Press here to access USB" or something like that.  You'll get a question about whether you want to mount your phone; select yes.

13.  Crack open Dolphin.  Your phone's SD card will be mounted as a VFAT volume; you might see a little mobile phone icon next to it (I do). Open that sucker up, and create a directory at the top level called "Books".  If you create it just like that, FBReader will automatically load books you drop into that directory.

14. Open up a second instance of Dolphin, and navigate to wherever you put your .EPUB book you converted in Calibre.  Drag and drop that book to the /Books directory you've just created.

15.  Close out both the Dolphin instances, and disconnect your phone from your computer.

16. Open FBReader from your Applications.  Press the "Menu" key, and select "Library".  It should automatically load the book you dropped into your phone.

YAAAAAYYYY!!!

I think Calibre has a batch conversion function; I don't know.  Can anyone figure out how to recursively batch convert all LIT files in every subdirectory of a given directory to EPUB?  I'd be mighty grateful!  I have a ../MyEbooks directory containing everything from ../MyEbooks/Abbott, John/ to ../MyEbooks/Zitkala, Za/, and I'd sure like to be able to specify that I want each converted EPUB file to stay in the directory Calibre found them in as opposed to creating a new directory on my Desktop for each of them!

PS: if you have a different format than EPUB that you need to work with, you can also use Calibre to open the LIT ebooks, and copy-paste the text of the ebook into Open Office, Kate, whatever...to save it in your chosen format, like PDF, RTF, TXT, whatevs.

---

### Post by Kantis on 2009-04-03
Oh, thank you so much! I've been searching for a tutorial like this for months, and now it is written. Finally I can read that stack of 20 e-books that I downloaded as .lit files. Works like a charm! :D

---

### Post by BKonkle on 2009-05-03
You, sir, are fantastic!  Thanks for the tutorial!

---

### Post by oliwek on 2009-05-12
```
sudo aptitude install convlit calibre
```

works for me in jaunty, probably the easiest way for points 1 and 2 in your tutorial

thanks for the good work

---

### Post by tarahmarie on 2009-05-12
> **oliwek said:**
> ```
sudo aptitude install convlit calibre
```

works for me in jaunty, probably the easiest way for points 1 and 2 in your tutorial

thanks for the good work

Sweet!  Calibre has been added to the repos?  Wahoo!

---

### Post by xdevnull on 2009-05-15
Several of the books I've moved over have -no- formating!  What's up with that.  Is there something I can do to fix it?

---

### Post by tarahmarie on 2009-05-16
> **xdevnull said:**
> Several of the books I've moved over have -no- formating!  What's up with that.  Is there something I can do to fix it?

I haven't had any problems with formatting; what format are you going to/from?

---

### Post by xdevnull on 2009-05-16
.lit  to epub.  I've also had something similar with .txt files.  Interstingly I converted a .lit to .mobi then to .epub.  Now there are paragraph spaces but no line wrap!

I did successfully convert a .prc that seems to work.  I have also downloaded from their "standard" website and that seems to work.  I can also successfully view all the files in the desktop FBreader.

There has got to be some setting in Calibre?

---

### Post by tarahmarie on 2009-05-17
> **xdevnull said:**
> There has got to be some setting in Calibre?

I don't know; as I haven't had any problems with it. I didn't go looking, but if anyone knows, it might help if I run into conversion problems.

---

### Post by xdevnull on 2009-05-18
Just did an html book and that worked pretty well!

---

