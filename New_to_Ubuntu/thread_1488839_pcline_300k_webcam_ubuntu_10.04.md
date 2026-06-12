---
title: "pcline 300k webcam ubuntu 10.04"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by darkeale on 2010-05-20
Hi,

does anyone know how to get this webcam to work in Ubuntu 10.04?
The camera is being recognised but I cannot see a picture in Skype or Cheese.

Can anyone please help with this.

Many thanks,
Alex

---

### Post by -humanaut- on 2010-05-20
I don't work with webcams however, the best solution might be to take the make and model and google it with the extenstion +ubuntu That will give you a definitive answer if it will work.

---

### Post by darkeale on 2010-05-20
Problem solved. Managed to get it working using the instructions in this thread:-

[http://ubuntuforums.org/showthread.php?t=993262](http://ubuntuforums.org/showthread.php?t=993262)

thanks,
Alex

---

### Post by ajgreeny on 2010-05-20
Your link is dead, I'm afraid, so nobody will be able to see how you solved the problem.  Can you amend it please and show the proper link.

---

### Post by darkeale on 2010-05-21
Hmmm the link works fine on my computer.

Anyway, basically, use this command in a terminal to run skype:-

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Then make a shortcut for it to make it easier:-

1. Create a simple script shown below with the name launchskype in your home folder

Quote:
#!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so 
skype &  

2. Set it as executable file. In file browser, right click the file and select "Make Link" option. It will create a link. Cut and paste this link to your desktop.
3. Double click this shortcut to launch skype. If it is prompted to "display or execute", select execute (or make select as default action in nautilus preferences)


Thanks,
Alex

---

### Post by ajgreeny on 2010-05-21
The link even works on my machine today.  Yesterday it just told me that the webpage was not available on this server.  A temporary problem of some sort, no doubt.

---

