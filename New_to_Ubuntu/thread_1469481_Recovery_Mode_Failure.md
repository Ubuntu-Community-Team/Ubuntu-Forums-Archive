---
title: "Recovery Mode Failure"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Peter09 on 2010-05-02
I have just upgraded one of my desktops to Lucid, the others went OK but I expected problems with this one because it has an nvidea card. So when it failed to give me an intelligible screen at startup I was not particularly worried, went back to startup and selected recovery mode.

This is where things went wrong. After a normal text start up I ended up with

> 
Refer to mount.cifs(8) manual page (e.g) man mount cifs
.... more lines similar to below ....
mountall: mount /home/<username>/DVD [852] terminated with status 32

The directories that are highlighted are ones that  have a mount point in my home directory which points to a network resource.

I cannot get any further progress in recovery mode, it all hangs there .... cntrl C gives no response and no command line appears with cntrl-Alt-F2

Can anyone help here?

---

### Post by sisco311 on 2010-05-02
Instead of booting into recovery mode, can't you just switch to a virtual console (Ctrl+Atl+F1)?

You can also try to highlight the recovery mode, press e for edit and replace the **ro single** kernel parameters with **rw init=/bin/bash**, press Ctrl+x to boot. In the root shell comment out the network share from /etc/fstab, reboot (Ctrl+Alt+Del) and try recovery mode again.

---

### Post by Peter09 on 2010-05-02
> Instead of booting into recovery mode, can't you just switch to a  virtual console (Ctrl+Atl+F1)?Nope - Ctrl+Alt+F1 gives a black screen :(

But Yes :P

> replace the **ro single** kernel parameters with **rw init=/bin/bash**drops me to a root prompt.
I can now edit /etc/fstab
Thanks very much for the suggestion.

Now to figure how to get the nvidiea card working from the command line.

---

### Post by Peter09 on 2010-05-02
See

[http://ubuntuforums.org/showthread.php?p=9217336#post9217336](http://ubuntuforums.org/showthread.php?p=9217336#post9217336)

for reasons why this happened and if it can help you. Note that its related to virtualbox usb support.

---

