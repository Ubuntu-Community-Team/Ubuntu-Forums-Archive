---
title: "Problem making CD images"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-04-11
I own an old PSX and a bunch of old PSX games. I would like to play them on my computer, but I keep running into a problem. On Ubuntu it will mount the disc and then immediately unmount it. On Windows 7 I get this error "Recording has failed. Code: 00000001".

Any ideas on how to fix this? Or why this is happening? I have made images from the same discs using previous versions of Ubuntu and Windows.

---

### Post by readycarpenter on 2010-04-11
does it happen with every disk? or just some of them, are they badly scratched? I have "backed up" ps1 games using dd you do not need to mount it

```
if=/dev/cdrom of=~/Desktop/cd.iso bs=1024
```

peace :P

---

### Post by slughappy1 on 2010-04-11
It happens with every cd I've tried. They are all in mint/near mint condition. I always forget about dd. I'll try that and see if it works.

---

### Post by slughappy1 on 2010-04-11
I tried that but I run into an error
```
jason@Barnaby:~$ dd if=/dev/cdrom of=~/Desktop/FinalFantasy7-1.iso bs=1024
dd: reading `/dev/cdrom': Input/output error
16+0 records in
16+0 records out
16384 bytes (16 kB) copied, 3.89891 s, 4.2 kB/s
jason@Barnaby:~$ 

```

---

