---
title: "No internet (wifi + ethernet): network unclaimed"
date: 2017-05-03
forum: Networking &amp; Wireless
---

### Post by nikopolidis85 on 2017-05-03
Hello,

I am unable to use the internet after an ubuntu sotware update.

This is my error: Network UNCLAIMED (see image below)

Does someone have a solution?

sudo modprobe r8169
sudo modprobe iwlwifi does not work...

Kind regards,
Nico

[ATTACH=CONFIG]274948[/ATTACH]

---

### Post by LastDino on 2017-05-03
There seems to have been bug with latest update rollout done through the Gui package manager

see>[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

I hope you did not remove old Kernels?

---

### Post by nikopolidis85 on 2017-05-03
thank you for the update LastDino!

What would you do if you had this problem? Wait for a bugfix or change the kernel ?

Maybe a n00bish question but where can i find my previous kernels?

---

### Post by wildmanne39 on 2017-05-03
Let's boot using an older kernel, reboot as soon as the computer starts to boot back up press and hold the shift key and you should see the grub menu choose advance mode for an older kernel not the newest, you have to be fast pressing the shift key. 

If you have two operating systems installed you do not have to hold the shift key down.

When the computer boots you should have a connection then do:
```
sudo apt-get install --reinstall linux-image-extra-4.4.0-77-generic
```
Reboot and see if your connection is back with the new kernel, also watch for errors while running the command.
Thanks

---

### Post by nikopolidis85 on 2017-05-03
Fixed! Thank you wildmanne39

---

### Post by wildmanne39 on 2017-05-03
I thought that would fix it and your welcome!:)

---

### Post by LastDino on 2017-05-04
Oh wildmanae39 got it before me, glad things worked out for you.


Please mark the thread as "solved", it helps keeping solved problems away from the unsolved ones.

---

