---
title: "Open Office 2.4"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by DarinB on 2009-11-30
I set up a computer for someone about a year ago. 
Now Open Office 2.4 will not open .doc,,,,she gets an error message, what is the easiest add the hardy repo for OO 3.0 and upgrade? And if i do??? do i remove 2.4 or just have her use 3.0 only????

---

### Post by Geoff918 on 2009-11-30
What's the error message? That may be more telling. You could always add OpenOffice through other means, but that's not necessarily going to take care of the root issue.

---

### Post by DarinB on 2009-11-30
yeah i am concerned about that. i will have her email me a screen shot of the error message

---

### Post by DarinB on 2009-11-30
I upgraded on a friends pc from OO 2.4 to OO3.0  now there is no Open Office writer in the applications. and when she clicks an icon on her panel it flashes OO 3.0 then closes??? what do i do now???
i used this below ?????? now she has no writer at all???

To install it for Ubuntu Hardy, add the following repository (System > Administration > Software Sources, Third Party Software tab, click "Add"):

deb [http://ppa.launchpad.net/r0lf/ppa/ubuntu](http://ppa.launchpad.net/r0lf/ppa/ubuntu) hardy main


And add the key using this command (in a terminal):

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B72FD7EC


Then, in a terminal, type:

sudo apt-get update

and then:

sudo apt-get upgrade

---

### Post by Hagar Delest on 2009-12-01
First try yo [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

