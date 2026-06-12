---
title: "explain me the copy speed from hdd to hdd"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by outlaw45k on 2010-05-10
so i just add a new 1TB drive to my linux box and i start to move some files the speed was at 1mb/s at this comment i was on wtf mode

before i put the HDD i read some stuff about how to edit fstab 
here is how the fstab was for my 1tb drive
```
/dev/sdb1 /media/T ext4 rw,auto,user,sync 0 2 
```based on what i read that is a good config
now my config for the hdd is
```
/dev/sdb1 /media/T ext4 user 0 2
```and the transfer rate is over 80 mb/s

my question is why ?

tvm

---

### Post by gzarkadas on 2010-05-10
Its probably the `sync' option. Synchronous writes, albeit safer are generally slower (and much slower sometimes). They can also destroy media with low number of write cycles, as described in this [link]("http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html"). What type is the filesystem of your hdd?

---

### Post by jerome1232 on 2010-05-10
> **outlaw45k said:**
> 
```
/dev/sdb1 /media/T **[COLOR="Blue"]ext4[/COLOR]** rw,auto,user,sync 0 2 
```based on what i read that is a good config
now my config for the hdd is
```
/dev/sdb1 /media/T **[COLOR="Blue"]ext4[/COLOR]** user 0 2
```

^

---

