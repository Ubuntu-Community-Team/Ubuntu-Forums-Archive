---
title: "Installing VMware tools - don't understand command line"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by gogetgeek on 2009-01-17
Hello,

Now that I have VMware Workstation, I thought I would try out Ubuntu after being discouraged with it years ago. I am trying to install VMware tools from a folder called "vmware-tools-distrib" in my home directory that was extracted from the virtual CD-ROM. 

If I do *cd /home/vmware-tools-distrib* in the Terminal, I get an error message, "No such file or directory."

Also, if I just try to Run the vmware-install.pl file after double-clicking on it, nothing happens.

Can someone just give me a step-by-step description of what I am supposed to do?

Thanks,
Brett :confused:

---

### Post by cwmoser on 2009-01-17
you might be in the wrong folder.

Do this to locate vmware-install.pl:

$  locate  vmware-install.pl


Carl

---

### Post by gogetgeek on 2009-01-17
brett@Linux:/$ locate vmware-install.pl
brett@Linux:/$

---

### Post by cwmoser on 2009-01-17
Hmmm.  I have not used VMware Workstation -- just VMware Server and VMware Player.  vmware-install.pl is definitely installed with VMware Server.

One idea is to download and install VMware Server and if you still want to load up Workstation, do that.  I found VMware 1.06 is works with Ubuntu.  2.0 works but is sloooooower than 1.06.  I use Server to create my virtual machines but prefer to run VMware Player to run them.

Perhaps someone who has actually worked with VMware workstation will chime in here.

Carl

---

