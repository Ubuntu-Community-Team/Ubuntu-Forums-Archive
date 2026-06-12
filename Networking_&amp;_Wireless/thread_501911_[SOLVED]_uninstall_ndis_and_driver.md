---
title: "[SOLVED] uninstall ndis and driver"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-15
The ndiswrapper page on uninstalling at sourceforge says:

 Starting with version 1.0, you can uninstall programs and modules installed with make uninstall in ndiswrapper directory. This won’t remove Windows drivers installed in /etc/ndiswrapper; for that, you should ndiswrapper -r driver command. Rest of this document shouldn’t be necessary to uninstall. However, should you have problems, follow it and see if make uninstal fails to remove anything and report that to mailing list or forums.

    *
 Make sure you unload your current ndiswrapper module with ‘modprobe -r ndiswrapper’ 

I took the foregoing to mean, modprobe -r first, then make uninstall

doing that gave:

mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers$ make uninstall WUSB11v4.inf
make: *** No rule to make target `uninstall'.  Stop.
mark@Lexington:~/ndiswrapper-147/WUSB11v4_08272004/Drivers$ 

How do I remove this ? Safely?

---

### Post by MyR on 2007-07-15
try "make uninstall" with no file after it
peace

---

### Post by Mark_in_Hollywood on 2007-07-15
tried that already. same response as with a filename

---

### Post by MyR on 2007-07-15
you need to be in the folder you installed it *from*

see this thread:
[http://ubuntuforums.org/showthread.php?t=222184](http://ubuntuforums.org/showthread.php?t=222184)

peace

---

### Post by Mark_in_Hollywood on 2007-07-16
yea, guy I was there -- where were you?

---

### Post by MyR on 2007-07-16
well the official uninstallation documentation is here
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)
it pretty much says the same thing though
only thing i can think of is to try sudo make uninstall
good luck!
peace

---

### Post by Mark_in_Hollywood on 2007-07-16
did it with sudo too

---

### Post by kevdog on 2007-07-16
You probably figured it out by now but the way to do it isudo ndiswraper -e ******  (driver name without the .inf or .sys extension).  To do the same thing you can do the following
cd /etc/ndiswrapper
sudo rm -R *

Then unload the module: sudo modprobe -r ndiswrapper
Then to actually remove the ndiswrapper executable (I often have to do this since I work with the ndiswrapper svn executable), go to the compilation directory (as you indicated), and type sudo make uninstall.

Again you might want to consult the official ndiswrapper documentation, because sometimes the make uninstall commands doesnt remove all the necessary execuatables needed when installing the new updates.

---

### Post by Mark_in_Hollywood on 2007-07-16
> **kevdog said:**
> You probably figured it out by now but the way to do it isudo ndiswraper -e ******  (driver name without the .inf or .sys extension).  To do the same thing you can do the following
cd /etc/ndiswrapper
sudo rm -R *

Then unload the module: sudo modprobe -r ndiswrapper
Then to actually remove the ndiswrapper executable (I often have to do this since I work with the ndiswrapper svn executable), go to the compilation directory (as you indicated), and type sudo make uninstall.

Again you might want to consult the official ndiswrapper documentation, because sometimes the make uninstall commands doesnt remove all the necessary execuatables needed when installing the new updates.

Nope NO sir, not one of those commands worked.Very frustrating.

---

### Post by MyR on 2007-07-16
how did you install it? it certainly has a will to live.

---

### Post by kevdog on 2007-07-17
Maybe its already uninstalled???

sudo updatedb (wait for a minute or two)
sudo locate ndiswrapper

What is the output not counting the directory and files from where the source files live?

---

### Post by Mark_in_Hollywood on 2007-07-24
After 

sudo -r ndiswrapper in several directories/subdirectories and much manual removal, ndiswrapper is toast.

thanks one and all.

---

