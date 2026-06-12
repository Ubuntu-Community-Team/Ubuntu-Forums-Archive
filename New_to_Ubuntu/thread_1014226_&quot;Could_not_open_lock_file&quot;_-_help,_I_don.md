---
title: "&quot;Could not open lock file&quot; - help, I don't understand!"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Green_Mac on 2008-12-17
I'm trying to install an app (bibus) on hardy.  After adding a line to /etc/apt/sources.list (which went fine) the instructions say:

    * Download the public key with the following command: 

wget -q [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey) -O- | sudo apt-key add -

which also went fine (response: OK).  But when I typed apt-get update as instructed, I got the response:

Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)

I'm using the only account I've ever created on the PC, so I don't see that it can be a permissions thing.  Can anyone tell me what I'm doing wrong?

---

### Post by Shhnap on 2008-12-17
That means that you have more than one package manager open at a time. Close the other one down and try again. :)

EDIT: MAybe more info is needed. Whenever you download or update a package the package manager 'locks' a file that prevents and other new packages from being accessed. You you just have to close the other think that is touching the packages before it will release the lock and let you download what you want.

---

### Post by adult swim on 2008-12-17
do you have synaptic package manager or add/remove open?

---

### Post by xjcannonx on 2008-12-17
try ```
sudo apt-get update
```

---

### Post by Green_Mac on 2008-12-17
Fantastic!  That was so quick.  I would have replied more quickly but I'm still so used to windows that when closing synaptic (yes, I did still have it running) didn't immediately do the trick, I restarted the machine to see if that helped.  It didn't, but putting sudo in front did.  It's working now, thanks to you all!  God, I love linux, just for the user community.

---

