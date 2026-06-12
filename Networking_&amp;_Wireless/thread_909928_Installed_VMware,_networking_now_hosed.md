---
title: "Installed VMware, networking now hosed"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by llcoolbeans on 2008-09-04
Hello,

I am new to Linux so please bear with me.

I installed VMware-server on Hearty.  The installation was successful and I was able to create an XP virtual machine using briged network connections without issue.  Virtual machine can see the internet and all local network devices except the host machine.

Networking in Hearty without using the virtual machine is now completely hosed.  I seem to be getting a valid ip, but machine can not connect to the internet or see any other computers besides the virtual machine.

The VMware installer asked many questions during setup, I wonder if I answered one or more wrong.  The install guide I read said to just choose the defaults, that's what I did.

help!

---

### Post by llcoolbeans on 2008-09-04
I guess i'll try uninstalling vmware-server tonight.  Hopefully that will undo any network settings that it created.  Otherwise the only other thing I know to do is reinstall Ubuntu and start over from scratch.  Sigh.

---

### Post by llcoolbeans on 2008-09-04
I was able to uninstall vmware-server and it did restore my internet connection.

However, synaptic now seems to be broken.  Add/Remove programs opens but when I try to install something, it just hangs.  I cannot open Synaptic Package manager at all.

Dangit!  I guess it's time to reinstall the os.

---

### Post by llcoolbeans on 2008-09-04
I give up.  Reinstalling now.

---

### Post by led-bloon on 2008-09-04
I am no expert but have successfully used vmware workstation on Gutsy. I used "nat" for networking and "defaults" for the rest of the setup. Should be no problems for Hardy. Try this and good luck.
:KS

---

