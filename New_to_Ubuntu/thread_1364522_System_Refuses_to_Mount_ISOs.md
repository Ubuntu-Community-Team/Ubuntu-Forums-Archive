---
title: "System Refuses to Mount ISOs"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by xnerdx on 2009-12-26
I have spent the past 3 days downloading an ISO and I think that it will cost me more that 150$ to pay for the internet service because I was just recently told about the 5gb cap on my service. I am very frustrated my system refuses to mount ISOs. I have used several methods, I have used mount/unmount scripts, I have run commands using mount with ro,loop=/dev/loop0 , with -o loop, using GMountISO, gISOMount, and nothing works! I have been reported this error message when using mount:
```

linus@SuDoX:~$ sudo mount -t iso9660 -o ro,loop=/dev/loop0 <iso image> /mnt/iso
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Please can someone help me, I tried Acetoneiso and I can't get the dang thing to install.... I just don't know what to do anymore.

---

### Post by taurus on 2009-12-26
Are you sure it is really an ISO image?

```
file filename.iso
```

What does it say when you run this command, after failing to mount it?

```
dmesg | tail
```

---

### Post by doas777 on 2009-12-26
is there any copyprotection on the image?

---

### Post by xnerdx on 2009-12-26
```

linus@SuDoX:~$ dmesg | tail
[ 8545.473251] ISOFS: Unable to identify CD-ROM format.
[ 8546.917787] ISOFS: Unable to identify CD-ROM format.
[ 8549.463197] ISOFS: Unable to identify CD-ROM format.
[ 8551.665051] ISOFS: Unable to identify CD-ROM format.
[ 9143.651959] ISOFS: Unable to identify CD-ROM format.
[10287.909057] ISOFS: Unable to identify CD-ROM format.
[10344.857316] ISOFS: Unable to identify CD-ROM format.
[10576.455976] ISOFS: Unable to identify CD-ROM format.
[11419.625901] ISOFS: Unable to identify CD-ROM format.
[16310.732657] ISOFS: Unable to identify CD-ROM format.

```

It is possible it has a copyright but it SHOULD mount on a windows machine because it has an amazingly large peers list so I figure people have gotten it to work :)
Also, I have an iso that I have mounted before that doesn't mount either.

---

