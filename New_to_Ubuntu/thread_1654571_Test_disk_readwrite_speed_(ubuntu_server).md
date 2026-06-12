---
title: "Test disk read/write speed (ubuntu server)"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by onthejazz on 2010-12-28
I don't know if I've got a problem with the disks in my server or I need a new switch. I would like to know if there was an application to test disk read /write speeds?

---

### Post by ian dobson on 2010-12-28
Hi,

dd is the easiest way to test the throughput on your drives:-

dd if=/dev/zero of=/path/to/file/on.fs bs=4k count=10000

That'll test the write speed and

dd if=/path/to/file/on.fs  of=/dev/null bs=4k count=10000
That'll test the read speed.

Note you'll need to play with the count until the data copyied is atleast double your installed ram.

Regards
Ian Dobson

---

### Post by onthejazz on 2010-12-28
> **ian dobson said:**
> Hi,

dd is the easiest way to test the throughput on your drives:-

dd if=/dev/zero of=/path/to/file/on.fs bs=4k count=10000

That'll test the write speed and

dd if=/path/to/file/on.fs  of=/dev/null bs=4k count=10000
That'll test the read speed.

Note you'll need to play with the count until the data copyied is atleast double your installed ram.

Regards
Ian Dobson

If I have just typed 

dd if=/dev/zero of=blankimage bs=4k count=10000

where have I saved this file and can I erase it.

---

### Post by onthejazz on 2010-12-28
write = 234 MB/s and read = 253 MB/s 

But if I cut or copy files from my smb directories with my windows pc I get nowhere near these transfer rates!

---

### Post by ian dobson on 2010-12-29
Hi,

So the problem is that copying from a windows PC with samba is slow. OK, samba isn't that quick, on my big RAID I get read/write speeds of about 320Mbyte/90Mbyte sec. But when I copy a large file over the network from my frontend linux box I only see 29Mbyte/sec and thats on a Gigabit lan with optimised samba options.

The parameters I'm using on my backend server are (/etc/samba/smb.conf):-
```
[global]
##Optimize tcp
socket options = TCP_NODELAY  SO_RCVBUF=131072 SO_SNDBUF=131072  rlimit_max=16384
```

Regards
Ian Dobson

---

