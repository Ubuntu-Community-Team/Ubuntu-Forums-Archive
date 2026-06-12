---
title: "Problems with VirtualBox"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Monrizzy on 2009-10-24
I'm having problems with VirtalBox all of a sudden.  I've got Mint & XP running as guests in VirtualBox and they have been running fine for weeks.  I use XP to sync my iPhone with iTunes and now I can't open either one.  I get this message...

> Failed to open a session for the virtual machine Window XP Pro II.
Virtual machine 'Window XP Pro II' has terminated unexpectedly during startup.

Still relativley new to gnu/linux and I need help!

---

### Post by dj-toonz on 2009-10-24
Hi, after doing some digging I came across this post

 Below the error was given the following explanation:

    Virtual machine 'Windows XP' has terminated unexpectedly during start up.

followed by some codes. Another dialog reported "VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908) " with instructions to re-setup the kernel module by executing:

/etc/init.d/vboxdrv setup

which I did:

sudo /etc/init.d/vboxdrv setup
[sudo] password for toonz:
 * Stopping VirtualBox kernel module
 *  done.
 * Recompiling VirtualBox kernel module


Hope that helps , If not somebody else can add something new

---

### Post by Monrizzy on 2009-10-24
That did it!! Thanks a ton!!!

---

