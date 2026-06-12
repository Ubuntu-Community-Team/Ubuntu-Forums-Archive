---
title: "Quirk with Vmware Player and Jaunty ..."
date: 2009-05-17
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-17
I found a "quirk" with Vmware Player and Jaunty.

I can consistently demonstrate this as follows:
 - Open an *.odt Open Office document and note that it is responsive and when you move the scroll bars it is not slow.  Works as expected.
- Close the Open Office document
- Start Vmware Player v2.5.2 and start a VM
- Open same Open Office document and note that it is slow and unresponsive, and that the window turns gray and comes back.  And, the document is very sluggish to work with.
- Close document
- exit the VM and Vmware Player
- note that the document is responsive and works as you expect.


My configuration is:
- Ubuntu 9.04
- AMD 64 X2 6000+
- 6 GB Ram
- nVidia GeForce 7300 LE Video card
- Running Compiz - when I turn Compiz off, it still exhibits same problem.
- I've allocated 512MB and 1GB RAM to the VM and still exhibits same problem.

Any ideas?


Carl

---

### Post by 123456789123456789123456 on 2009-05-17
From the ram,  assume you are using the 64bit version of Ubuntu.  Are you using the 64bit version of VMware?  Did this problem exist with 8.10?
I assume if it is 64bit, there is an error code somewhere, a slight incompatability with the version of 9.04.  If it is the 32 bit version of VMWare, performance running on a 64bit OS, could cause problems.

It tries to reduce speed of OS, and Processor in order to run the program.

---

### Post by cwmoser on 2009-05-17
I using 64-bit Ubuntu 9.04, and 64-bit version of Vmware Player.

Carl

---

### Post by cwmoser on 2009-05-17
This fixed it for me - upgrade Open Office from 3.0 to 3.1:

How to Install OpenOffice.org 3.1 on Ubuntu 9.04

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml]("http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml")

Carl

[COLOR="DarkRed"]**FOLLOW UP -- Further testing ... this did not fix the Open Office slowness issue.**[/COLOR]

---

