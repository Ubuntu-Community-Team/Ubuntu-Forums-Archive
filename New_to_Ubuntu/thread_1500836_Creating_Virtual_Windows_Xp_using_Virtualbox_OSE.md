---
title: "Creating Virtual Windows Xp using Virtualbox OSE"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by HenrySkitsas05 on 2010-06-03
I've installed VirtualBox OSE, and I've tried following an online guide at making a System and failed. When I put the XP CD in and clicked "Start" it replied 

"FATAL: No bootable medium found! System halted."

People have told me bluntly that "Obviously theres a problem with your disc" 

That isn't very helpful. Could someone kindly explain what I should do. 

Thank you.

---

### Post by nhasian on 2010-06-03
if you plan on using any USB devices, then i would uninstall the OSE version and get the full version directly from virtualbox.  then double check your virtual computer settings and make sure you have enabled support for the cd-rom.  worst case scenario is you could make a backup iso image of your windows CD and have virtualbox boot off the iso image instead of using the cdrom drive.

---

### Post by blchinezu on 2010-06-03
did you mount the host optical drive in the virtual machine?

---

### Post by HenrySkitsas05 on 2010-06-03
How do you mount the optical Drive? Sorry, I am a pretty big noob.  I've had Ubuntu for a while, but I haven't used it for Software really.

---

### Post by blchinezu on 2010-06-04
enter virtualbox, start the virtual machine and in the upper menu go to **devices** > **CD/DVD devices** > **Host Drive **...
after selecting that restart/reset or whatever your virtual machine and it should recognize the optical drive

---

### Post by lkraemer on 2010-06-04
USB is NOT supported in the OSE version, so you will have to uninstall
with Synaptics Package Manager, then go to [www.virtualbox.org](www.virtualbox.org)
and download the version for your distro.  For Ubuntu install dkms also
as noted on the Download site.  When Virtualbox is installed create your
VDI file, then install the Guest OS.  If Windows is the Guest be sure to
install Guest Additions........

There is a nice tutorial on the [www.pclinuxos.com](www.pclinuxos.com) website, in the
October 2008 issue of the PCLinuxOS Magazine. You might want to
read through it.  It is an older version of VirtualBox, but you will
basically follow the same steps.

The problem you are seeing is because you must first use NEW to create a
Container for the Virtual Disk Image, by answering the questions as presented
on the screen, then the second step is to install the GUEST OS
in the VDI Container.  You can VERIFY this by going to your HOME Folder,
then to .VirtualBox, then to HardDisks, and look for any *.vdi files.
If none are present you must use NEW to create one.

You will also want to follow these directions on the [www.VirtualBox.org](www.VirtualBox.org) site

Note: Ubuntu users might want to install the dkms package (not available on Debian)
to ensure that the VirtualBox host kernel modules (vboxdrv and vboxnetflt) are properly
updated if the linux kernel version changes during the next apt-get upgrade.

Also, you will need to install the GuestAdditions.ISO, along with reading
the information here:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
on Windows Shared Folders with a Windows GUEST VDI.

And don't forget the HOWTO's and TUTORIALS.

lk

---

