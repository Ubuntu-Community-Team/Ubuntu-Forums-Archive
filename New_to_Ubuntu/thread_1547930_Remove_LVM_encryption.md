---
title: "Remove LVM encryption"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by RegginKrad on 2010-08-07
I just installed my server but now I just realized that you cant remotely ssh after reboot because of the passkey. How do I get rid of the passkey part?

I read this thread:

[http://forums.fedoraforum.org/showthread.php?t=202891](http://forums.fedoraforum.org/showthread.php?t=202891)

Is it possible to decrypt not-on-the-fly (not sure what this means either way) or have the passkey automatically put in?

If I could ssh the passkey in that would also be great.

For the record, I don't know how I would backup, reformat, then copy-back the OS.

---

### Post by csenciboy on 2010-12-29
I'm in the exact same boat.  Did you ever get this resolved or did you simply reinstall the OS without encryption? I want to run the server headless, but knowing nothing about Ubuntu upon initial install, I selected encrypted LVM.  Now SSH works only after I reconnect a monitor and keyboard to input the passphrase after each reboot.

Let me know how you handled it.  Thanks.

---

### Post by csenciboy on 2011-01-13
Just a follow up for anyone who stumbles across this. I reinstalled the OS without encryption. It was the only way I could find to handle the server headless.

---

### Post by bluntknife on 2011-08-09
I can't accept this isn't possible..!

For legal reasons I need to ensure the partitions that store client information is encrypted so I therefore must enable this option during the installation (10.04 LTS 32-bit).

On the other hand I cannot enter a passphrase on reboot as my server is hosted remotely and the operations staff will charge me to enter the passphrase each time.  Not only that I don't want them to know the passphrase!

Can someone suggest a solution to this problem please?

---

