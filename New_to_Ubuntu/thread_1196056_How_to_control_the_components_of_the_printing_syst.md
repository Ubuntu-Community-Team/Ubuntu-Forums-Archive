---
title: "How to control the components of the printing system"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by RobertL on 2009-06-24
My USB-attached HP inkjet printer started producing garbled output, I think when I upgraded to jaunty but it might have worked ok for a week or two after that... no way to be positive now. In trying to debug it I keep reading things that say try this or that version of the PPD file, or this or that driver, or some other version of something. 

Is there a unified way to find out the details of all the printer-related software I currently have installed? And then is there a way to change one component at a time?

I know how to delete the printer and install a new printer, select the model number, etc. I've done that several times now but it doesn't fix the problem. It all happens nice and automagically but unfortunately the output on the printer is always garbled so something that is automatic is wrong.

I gather that the overall printing system is called cups so I was expecting to find some kind of cups command that would show what is installed but I haven't found it.

BTW... the printer is USB-connected on a ubuntu machine and samba-shared on a local network and windows machines on the network can print to it fine. The output is only garbled from linux. Also during my first 6 months experience using linux (with ubuntu intrepid) it worked fine. So I I'm pretty sure the garbled output is caused by some component of the linux/jaunty software.

---

### Post by MrWES on 2009-06-24
> **RobertL said:**
> My USB-attached HP inkjet printer started producing garbled output, I think when I upgraded to jaunty but it might have worked ok for a week or two after that... no way to be positive now. In trying to debug it I keep reading things that say try this or that version of the PPD file, or this or that driver, or some other version of something. 

Is there a unified way to find out the details of all the printer-related software I currently have installed? And then is there a way to change one component at a time?

I know how to delete the printer and install a new printer, select the model number, etc. I've done that several times now but it doesn't fix the problem. It all happens nice and automagically but unfortunately the output on the printer is always garbled so something that is automatic is wrong.

I gather that the overall printing system is called cups so I was expecting to find some kind of cups command that would show what is installed but I haven't found it.

BTW... the printer is USB-connected on a ubuntu machine and samba-shared on a local network and windows machines on the network can print to it fine. The output is only garbled from linux. Also during my first 6 months experience using linux (with ubuntu intrepid) it worked fine. So I I'm pretty sure the garbled output is caused by some component of the linux/jaunty software.

Point your browser to:
[http://localhost:631]("http://localhost:631")
That is cups web interface.

Bill

---

### Post by Tamlynmac on 2009-06-24
I had a similar problem after installing 9.04. I installed the new HP driver located below and it resolved the problem.

[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

I used the automatic installer and it went perfectly. Just follow the simple instructions.

Good Luck and I hope this helps.

---

