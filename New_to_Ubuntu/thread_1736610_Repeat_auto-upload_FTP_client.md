---
title: "Repeat auto-upload FTP client?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by chuangt2u on 2011-04-22
Hi.

I'm setting up a webcam to display images online, and have used camE to generate an image every X seconds - save it and overwrite the previous image using the same filename. 
I have commercial server space to store the image.
I've also set up a very simple webpage that auto-refreshes every X seconds to display the image.... 

[http://cambodiamapswebcam.blogspot.com/](http://cambodiamapswebcam.blogspot.com/)

all I need now is to get the images online. I realise that this is crude, but slow/dodgy internet services are the norm here... no streaming video.

Does anyone know of an FTP client that can be set to repeatedly upload the "same" .jpg file every X seconds?

I've tried Filezilla, but that does not allow for repeated/automated uploads as I need them.
I also looked at Gnome Konquerer, but couldn't see whether it could be done there. There are so many FTP programs out there for Linux that I don't really know where best to continue... can anyone help?

I'm using Ubuntu 10.04 Lucid Lynx LTS, and have had it for around 4 months, so I'm no expert! ... simple solutions if possible please :D

Many thanks

C

---

### Post by frup on 2011-04-22
What about a command line FTP client? You could set a bash script to run the command frequently.

---

### Post by chuangt2u on 2011-04-23
Seems a good idea - but which client to use, and how do I write the script?

---

### Post by frup on 2011-04-23
There is a built in ftp command

[http://unixhelp.ed.ac.uk/CGI/man-cgi?ftp](http://unixhelp.ed.ac.uk/CGI/man-cgi?ftp)

You could set up something in cron for the timing I suppose or set up a bash script in a loop that waits a seconds between iterations I guess.

You can learn bash scripting here [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
You can learn about cron here [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

Unless someone else is willing to do all the work for you, you're going to have to learn how to set it up by yourself. There may be a better way of doing things, but that seems like a good way to start.

---

### Post by chuangt2u on 2011-04-23
Thanks for the replies, frup.

I took one look at the content of those links and very nearly had a heart attack!

I found that Dropbox does it just fine. Sent the webcam image to one of the Dropbox sync folders with "camE" and used the Dropbox URL in the webpage with a small "Googled" script to refresh the image without refreshing the page.

Sorted!

---

