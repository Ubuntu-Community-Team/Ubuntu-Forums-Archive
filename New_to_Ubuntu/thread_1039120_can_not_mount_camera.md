---
title: "can not mount camera"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by sigurnjak on 2009-01-14
this is an error i get when i plug in my hp camera ;
Invalid mount option when attempting to mount the volume 'HP_M437'.

and dmesg output is here if it helps

andrey@andrey-desktop:~$ dmesg | tail
[ 2332.426332] sdd: rw=0, want=1987584, limit=1987583
[ 2332.426649] attempt to access beyond end of device
[ 2332.426654] sdd: rw=0, want=1987584, limit=1987583
[ 2332.426971] attempt to access beyond end of device
[ 2332.426976] sdd: rw=0, want=1987584, limit=1987583
[ 2332.427328] attempt to access beyond end of device
[ 2332.427333] sdd: rw=0, want=1987584, limit=1987583
[ 2332.427653] attempt to access beyond end of device
[ 2332.427658] sdd: rw=0, want=1987584, limit=1987583
[ 2332.592771] VFS: Can't find ext3 filesystem on dev sdd1.


Also as of recently my ipod will not mount and gives me  this error 

Invalid mount option when attempting to mount the volume 'ANDREY'S IP'.

Can anyone sort this mess out for me ?

---

