---
title: "http://www.momento.com.au/"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by adsf on 2009-05-25
Hi, 

Got the girlfriend using linux though she still does understand why I done use windows.  Its been going well for a while. 

A friend of her has put her on to [http://www.momento.com.au/](http://www.momento.com.au/)  and she wants to use it.  It allows some one to create a photos album and then have it printed.

does any one have a suggestion except for installing windows? Has any one used something simular that is either web based or Linux friendly?

I tried to get the program to run under WINE, but i am not that firmular with WINE and got no where.

---

### Post by Steelmourne on 2009-05-25
You could install Picasa from Google and create a photo album from it, or you can go to synaptic and install wine. Right click the program's exe and select open with wine. Try to install it and see if it runs. It also seems the site allows individual uploading of photos so you might try that.

---

### Post by adsf on 2009-05-25
Thanks Steelmourne,  i tried the WINE route, is seemed to install correctly but would not actually run the program.

The thing about momento that the girls liks is that it is live virtual craft booking, they will then print, bined and send it too you as a actual book.  Does Picasa do this?  I have only used it for storing photos on line.  I will have a more indepth look

---

### Post by sandyd on 2009-05-25
try this :)

[http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

---

### Post by paulphillips on 2009-06-03
I got it working!

The installation worked fine, but didn't work when trying to run it (as others have also discovered)

I noticed when I ran momento from the command line that it was complaining about a missing dll file: "mfc42.dll"

I then did a search for that file on the web, downloaded it from one of the many sites offering it, then placed it in the C:\windows\system32 directory
(this should be ".wine/drive_c/windows/system32" under your home directory - you may need to select "show hidden files" under the file browser window, "view" menu).

I re-ran momento from the applications->wine menu and voila!  It works.  I haven't used it in anger yet (my wife will do that for me ;-)) but at least I was able to create an empty coffee table book ready for inserting photos.

I hope this helps!

---

