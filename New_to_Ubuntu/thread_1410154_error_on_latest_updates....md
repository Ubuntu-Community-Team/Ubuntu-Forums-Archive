---
title: "error on latest updates..."
date: 2010-02-18
forum: New to Ubuntu
---

### Post by mustard greens on 2010-02-18
latest update (firefox etc.) getting the message below.  any ideas?


E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory


read some archive posts on a similar error message, solution was deleting the offending lock, but I am nervous to try this.

---

### Post by howefield on 2010-02-18
It means you have another package manager running, whether that be  apt-get, Software Center, Update Manager, Synaptic Package Manager, Adept Package Manager, ect ect.

You can only have one package manager running at a time.

Try closing all package managers or if that doesn't work, reboot and try again. ?

---

### Post by mwcrowley on 2010-02-18
howefield has it right.  If you are nervous about deleting the lock file a reboot will close the package manager that was running if you could not find it.  If the lock file is still present after a reboot it means that package manager closed without removing the lock file (this is rare but does happen).  Simply delete the lock file and start up your package manager.

---

### Post by mustard greens on 2010-02-18
thanks guys the reboot worked. I hadnt had another synaptic open though so I dont know why it was locked.  anyway, looks solved.  thanks for the help.

---

### Post by mustard greens on 2010-02-24
so I am getting this error every time I attempt to engage the update through update manager.  I have not been using any other synaptics prior to these events.  

any ideas?

can I just 
sudo rm /var/cache/apt/archives/lock

I saw that in another post about stuck locks.

---

