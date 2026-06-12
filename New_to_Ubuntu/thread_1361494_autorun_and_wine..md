---
title: "autorun and wine."
date: 2009-12-22
forum: New to Ubuntu
---

### Post by ja660k on 2009-12-22
Hey guys,
Here's my problem. bare with me because this could get quite convoluted. 

i have a windows app ISO on my desktop, i mount it and i double click install.exe and wine doesnt do anything, in fact nothing happens. 

is there a way to somehow mount the iso into the cdrom0? to trick it so it thinks theres a cd in the drive and wine will execute autorun that way?

or whats the best way of doing this?
(id rather not burn the images into cd's if i dont have to)

thanks

---

### Post by Mark Phelps on 2009-12-22
You could save yourself a lot of work and grief if you first go to the WineHQ site to check out the compatibility of your "app" in Wine.

History has shown that some apps work very well in Wine (usually, the older versions), some OK, and some, not at all.

Link is below:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by synapsys on 2009-12-22
Also you can install **gmountiso**, which makes it super easy to mount an iso to a directory of your choice, including cdrom0.

---

