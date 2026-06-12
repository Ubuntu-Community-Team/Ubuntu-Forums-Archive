---
title: "Build-Essential Questions"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by newport_j on 2009-08-25
When I give the command: 
 
sudo apt-get install build-essential
 
it asks for two things, one of them directly.
 
It asks to place the CD-ROM (8.04.2 Ubuntu LTS disk) install disk in the CD-ROM drive: 
 
It also requires you to be on the internet. 
 
Why does it require both?
 
 
It seems if you are on the internet then there is not need for the original install disk, and if you put the original install disk in the CD-Rom drive, why do they need the internet?
 
 
Second question:
 
how I install buld-essential only using the CD -ROM disk?
 
 
Third quesion:
 
How do I install build-essential only uisng the internet?
 
 
Forth question:
Why do they not just install build-essential when one installs Ubuntu?
 
 
I need an answer to these four questions.
 
 
Newport_j.

---

### Post by cariboo on 2009-08-25
> It asks to place the CD-ROM (8.04.2 Ubuntu LTS disk) install disk in the CD-ROM drive:

You have cd-rom enabled in the /etc/apt/menu.lst, to disable it go to System-->Administration--Software Sources and disable it. 

> Why do they not just install build-essential when one installs Ubuntu?

Starting with 8.10 build essential is installed by default.

---

### Post by mcduck on 2009-08-25
> **cariboo907 said:**
> 
Starting with 8.10 build essential is installed by default.
No, it definitely isn't. But it *is* included on the Alternative CD. Perhaps on the desktop CD as well, I'm not sure about the later one.

But it sure isn't installed by default. :)

---

### Post by newport_j on 2009-08-25
In order to disbale cd-rom I need to go 

system-administration-software sources

and disable it.

How do I do that?

I go to the software source window and use the Ubuntu software tab. There is no check box or radio button saying to enable or disable cd-rom. So What do I do? The Ubuntu software has a lower level box saying if you want to install cd-rom or dvd place in disk holder. But it is not something you can erase or change. How do I disbale cd-rom.

ewport_j

if I do disable cd-rom then does it change and make 


sudo apt-get install build-essential



 installable without the cd-rom put in lace instruction.

Newport_j

---

### Post by oldos2er on 2009-08-25
"I go to the software source window and use the Ubuntu software tab. There is no check box or radio button saying to enable or disable cd-rom."

 Could we please see a screenshot? There should be a box at the bottom of the Ubuntu software tab that contains a check box in front of "Cdrom with Ubuntu 8.04 'Hardy Heron....'

 You can also manually edit your sources.list file by running **gksu gedit /etc/apt/sources.list** in a terminal. Remove or add a comment mark # in front of the deb cdrom: line, which should be at the top of the file.

---

### Post by mcduck on 2009-08-25
It could be that the check box wasn't there in 8.04, it's been quite a while but I remember that the UI has changed over time. I'm sure there was a way to disable the CD-ROM even with the 8.04's GUI, but it's pretty much impossible to give instructions for that when I'm already running 9.04..

So, doing it by hand (by commenting out the line in sources.list) might be the best option.

---

