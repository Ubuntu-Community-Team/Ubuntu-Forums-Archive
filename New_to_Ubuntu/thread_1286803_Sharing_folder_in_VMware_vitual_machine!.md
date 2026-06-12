---
title: "Sharing folder in VMware vitual machine!"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-10-09
I am having win XP pro installed on VMware virtual machine on Ubuntu. I am using VMware player to run it. The prooblem i have is that i am not able to share other drives to XP that i have on which the Virtual machine is installed.

I configured the VM in this way:

--> I have modified .VMX file to increase the number of shared folder.(Errorless)
--> In VMware Player(menu)-->shared folders I have given the path of all mounted drives i.e in format like "/media/drive1".
--> I made it "always enabled" and "Map as network drive in guest OS" is checked.

But I am not able to access them inside my Guest Win XP despite of having all drives mounted.

Please help..

---

### Post by eshant_engineer on 2009-10-10
please help...

---

### Post by corncob on 2009-10-10
This might not be exactly the same thing as I am using Sun VirtualBox, the successor, I believe, to VMWare.  In XP I went to START, then "All Programs".  I found a listing saying "Sun VirtualBox Guest Additions" which I clicked on and installed.  I forget the details but these additions allowed me to create a shared folder with the default name "ubuntushared" which appears both on the Ubuntu host and the XP guest.  If I move a file to this folder in Ubuntu, I can retrieve it from the ubuntushared folder in XP.
BTW, when I opened VirtualBox just now, a popup told me that a new version is available:
```
http://download.virtualbox.org/virtualbox/3.0.8/virtualbox-3.0_3.0.8-53138_Ubuntu_jaunty_i386.deb
```
Hopefully this just upgrades what I have and not make me reinstall XP.  The website should give some info.

---

