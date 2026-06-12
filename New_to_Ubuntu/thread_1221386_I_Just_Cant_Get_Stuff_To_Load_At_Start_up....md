---
title: "I Just Cant Get Stuff To Load At Start up..."
date: 2009-07-23
forum: New to Ubuntu
---

### Post by zzyzx1 on 2009-07-23
So, i have battled "getting stuff to work" and won a moderate victory now i need it to load.

Most important: My shared, networked, windows drive -> blitz/e, or smb://blitz/e, or, /home/me/.gvfs/e on blitz/... this is part of the problem.

Before you stop me and say "this is a mounting issue, please re post appropriately" it will mount from browser and via cli with cmd-> gvfs-mount smb://blitz/e. So, no problem mounting.

I narrowed it down to two methods in with to mount at start-up:

1) sudo nano /etc/rc.local -> gvfs-mount smb://blitz/e (added)
2) created sharemount.sh and added gvfs-mount smb://blitz/e, then made executable with chmod +x ~/sharemount.sh, then added the file to applications start up.

Neither one work! And i cant figure out how to trouble shoot it...

last, and almost important, is my music. its a .asx file opened with VLC. I added that to start up and nothing... 

Appreciate any guidence!

---

### Post by wojox on 2009-07-23
This may help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by zzyzx1 on 2009-07-23
> **wojox said:**
> This may help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Nope, cool tool.. but im trying to auto-mount a windows drive over the network, not ON my Ubuntu box... 

Ubuntu--->LAN--->Windows_external_shared_drive/whatever.

---

### Post by zzyzx1 on 2009-07-23
> **zzyzx1 said:**
> Nope, cool tool.. but im trying to auto-mount a windows drive over the network, not ON my Ubuntu box... 

Ubuntu--->LAN--->Windows_external_shared_drive/whatever.


Wow,uhh I fixed it. Havent fat fingered in a while but i guess i did the sharemount.sh file... i changed gvs-mount smb://xxxxxx/xxx to gvfs-mount and whammo... works in the start up great.

So, anyone know what this little diddy doesnt work for start up..?

sudo nano /etc/rc.local (add mount path)

Thanks.

---

### Post by mcduck on 2009-07-23
> **zzyzx1 said:**
> Wow,uhh I fixed it. Havent fat fingered in a while but i guess i did the sharemount.sh file... i changed gvs-mount smb://xxxxxx/xxx to gvfs-mount and whammo... works in the start up great.

So, anyone know what this little diddy doesnt work for start up..?

sudo nano /etc/rc.local (add mount path)

Thanks.

GVFS only works after Gnome is running, which is not the case at the time when stuff in /etc/rc.local is executed.

If you want to mount the drive at system level, before logging into desktop, you'll have to mount in in /etc/fstab (and yes, you can mount network drives there).

---

