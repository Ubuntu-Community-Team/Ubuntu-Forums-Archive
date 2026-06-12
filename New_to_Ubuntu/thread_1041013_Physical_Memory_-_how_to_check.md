---
title: "Physical Memory - how to check?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by autogun on 2009-01-16
Hello guys,

Im running a Virtual-Private-Server machine with Fedora-Core-5 on it.

I googled a little and the easiest way I found to check the memory is by typing 'free -m'.
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          8100       7894        206          0        236       5515
-/+ buffers/cache:       2141       5958
Swap:        12001          0      12001
```

Now, I believe that the 8GB memory I see here belongs to the whole VPS host machine..

From the VPS-Management UI, I see the following:
vmguarpages 2147483647 in 4KB pages units which I dont quite understand.

Can you please help me and sort this one for me?

Thanks a bunch! :KS

---

### Post by blazemore on 2009-01-16
What exactly are you trying to do?

---

### Post by stevoo on 2009-01-16
You can use
$ top

and check at the top the given lines
Mem:   8189496k total,  7975080k used,   214416k free,      300k buffers
Swap:  3903784k total,   620576k used,  3283208k free,  2025164k cached


this may help out  ?

---

### Post by stevoo on 2009-01-16
You can use
$ top

and check at the top the given lines
Mem:   8189496k total,  7975080k used,   214416k free,      300k buffers
Swap:  3903784k total,   620576k used,  3283208k free,  2025164k cached


this may help out  ?

---

### Post by autogun on 2009-01-16
> **blazemore said:**
> What exactly are you trying to do?

I just want to know how much memory I have.. Should be 512Mb but I dont see this number anywhere, not even near :|

---

### Post by stevoo on 2009-01-16
actually with that you have 8gb of memeory 

if you do a 
$top 
and see this 
Mem:    515488k total,   495672k used,    19816k free,       24k buffers

then you have 512 memory !

---

### Post by autogun on 2009-01-16
> **stevoo said:**
> actually with that you have 8gb of memeory 

if you do a 
$top 
and see this 
Mem:    515488k total,   495672k used,    19816k free,       24k buffers

then you have 512 memory !

```
Cpu(s):  0.2% us,  0.0% sy,  0.0% ni, 99.8% id,  0.0% wa,  0.0% hi,  0.0% si,  0.0% st
Mem:   8295136k total,  8116904k used,   178232k free,   243592k buffers
Swap: 12289716k total,      592k used, 12289124k free,  5655288k cached
```

Hrmf..

---

