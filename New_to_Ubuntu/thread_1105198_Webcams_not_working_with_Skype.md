---
title: "Webcams not working with Skype"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by mikebravo on 2009-03-24
After complaining about the upgrade from Hardy to Intrepid breaking my webcam, and unsuccessfully trolling the beginners forum for answers, I broadened my search and found a sticky post ( [http://ubuntuforums.org/showpost.php?p=6115686&postcount=30](http://ubuntuforums.org/showpost.php?p=6115686&postcount=30) ) by spiderbatdad saying try

Code:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  
OR
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

and sure enough, I open a terminal, enter either one of those, and my webcam works. MY QUESTION IS: where can I put one of those lines so that it will be automatically loaded without having to type it in each time (I am an Absolute Beginner remember).

Will making it a permanent work around be setting a bomb that will blow up on me if I upgrade to Jaunty?

---

### Post by PriceChild on 2009-03-24
right click the 'Applications' menu and choose 'edit menu'. Then navigate to the skype entry and add the command you found the the 'command' box.

I don't think that it will blow up when you go to Jaunty. At the worst, it will stop skype working during some update requiring you to remove the LD_PRELOAD.

---

### Post by mikebravo on 2009-03-26
Your answer is pretty clear but does not work for me. I followed your instructions and replaced the word 'skype' in the command box with one of the lines spiderbatdad suggested. Got "Error    Could not launch menu item   Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" (No such file or directory)"  So, I put the work "skype" at the front of the line. This loaded Skype but when I tried to test my video, the test screen was noisy green with black 'hum' bars.

I put the same line as originally written in the terminal, got this response:
mike@mike-linux:~$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Starting the process...
Skype Xv: Xv ports available: 32
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 280

But, Skype opened and video tested perfectly.

What am I doing something wrong?

---

### Post by ckaven on 2009-03-29
wow ran same line and got same results. tried to get it to stick but also got he same problem. hope some one can help here.

---

### Post by spiderbatdad on 2009-03-29
[http://ubuntuforums.org/showthread.php?p=6934020](http://ubuntuforums.org/showthread.php?p=6934020)

---

