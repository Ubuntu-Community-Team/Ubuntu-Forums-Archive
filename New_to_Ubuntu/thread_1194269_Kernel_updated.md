---
title: "Kernel updated"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Duskao on 2009-06-22
Hello everybody.
Last night I using my computer and the update manager popped up. There were a few different updates but one of them was a Kernel update. I'm using Jaunty. Sorry I can't remember the whole kernel number but it is the default kernel that comes with jaunty and it updated from .11 to .13. In GRUB it is now the default for the boot and my video driver isn't working with it. I can still choose .11 (which I'm using now). Is there a way I can fix this so it will work with my video driver (Radeon fglrx 9.5). Should I update my video driver to 9.6? If so, how do I remove/uninstall 9.5. 

Hope someone can help me out, thanks.

---

### Post by The-Don on 2009-06-22
I had the same problem. What I did was:

[LIST]
[*]Pressed ESC during the Grub process
[*]Select the kernel (Recovery Mode)
[*]Select 'netboot'
[*]Typed in "cd / etc/X11"
[*]"ls -l" <-- at the bottom hopefully you'll see the below files:
[*]"sudo mv xorg.conf xorg.conf.broke" <-- that renames the file
[*]"sudo cp xorg.conf.failsafe xorg.conf" <-- that install the failsafe file (by a rename)
[*]Restart PC.
[/LIST]
If the above doesn't work, then repeat the above renames back to how you originally had it.

---

### Post by ivanvajar on 2009-06-22
You need to reinstall your drivers after update. Drivers are not smart enough to reconfigure themselves in order to work as they should with new kernel.

---

### Post by Shazaam on 2009-06-22
Once you get your drivers fixed install dkms. You can use Synaptic to install it. Once installed there is NO need to configure it as the default settings work fine. It will help when there is a kernel update...

[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)
man page...
[http://linux.dell.com/dkms/manpage.html](http://linux.dell.com/dkms/manpage.html)

---

### Post by Duskao on 2009-06-26
what is dkms?

---

### Post by carml on 2009-06-26
DKMS = Dynamic Kernel Module Support Framework
This package contains the framework for the Dynamic Kernel Module
Support (DKMS) method for installing and updating kernel modules.

Just install them by opening a terminal and typing there ```
sudo apt-get install dkms
```,followed by your password. :)

---

### Post by philinux on 2009-06-26
> **Duskao said:**
> Hello everybody.
Last night I using my computer and the update manager popped up. There were a few different updates but one of them was a Kernel update. I'm using Jaunty. Sorry I can't remember the whole kernel number but it is the default kernel that comes with jaunty and it updated from .11 to .13. In GRUB it is now the default for the boot and my video driver isn't working with it. I can still choose .11 (which I'm using now). Is there a way I can fix this so it will work with my video driver (Radeon fglrx 9.5). Should I update my video driver to 9.6? If so, how do I remove/uninstall 9.5. 

Hope someone can help me out, thanks.

Which version of ubuntu are you using.

---

