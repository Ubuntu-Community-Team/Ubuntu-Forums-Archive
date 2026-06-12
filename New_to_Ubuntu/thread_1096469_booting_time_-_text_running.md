---
title: "booting time - text running"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-03-14
from today...
wehneever i start ubuntu

the orange progress bar fills upto "B" of ubuntu
and then a black screen appears with running texts with "[ok]" attached to the end.....

but still boots and works fine...

i wantto  get rid of this

---

### Post by RetchingRabbit on 2009-03-14
This just means the splashy isn't working right. I have no idea how to fix it since the first thing I usually do is wipe the splashy...I'd rather have the text tell me what the system is doing.

---

### Post by kimikrishna on 2009-03-15
> **RetchingRabbit said:**
> I'd rather have the text tell me what the system is doing.


I dont want to know ..... 
its not coming in xp... and my frnds who are "win" fans wish to see my ubuntu first before they agree to install in their computers.

how to fix it ?

---

### Post by kimikrishna on 2009-03-15
help me to fix it fully.....
i dont want these running texts with [ok] at the end...
thansk in advance

---

### Post by kansasnoob on 2009-03-15
Did you move or resize the swap partition?

Post the output from terminal of:

```
sudo blkid -c /dev/null
```

and:

```
cat /etc/fstab
```

and:

```
cat /etc/initramfs-tools/conf.d/resume
```

I suspect a UUID problem. I just need to see those outputs to be sure. If that's what it is it's easy to fix.

---

### Post by humphreybc on 2009-03-15
I too have the same problem but only when the Laptop is running on battery power. When it's plugged in on AC power it completes to the end of the bar and boots fine...

---

### Post by kansasnoob on 2009-03-15
> **humphreybc said:**
> I too have the same problem but only when the Laptop is running on battery power. When it's plugged in on AC power it completes to the end of the bar and boots fine...

I think that's different. Basically hal recognixes a hardware change so "initra.." performs differently!

Basically if I change even one minor piece of hardware on a machine the "hardware detection" mode kicks in!

You might want to check and see if your swap is activated at start-up. The easiest way is to install gparted and then look in System > Administration > Partition Editor and see if Swap is "on" at start-up.

---

### Post by kimikrishna on 2009-03-15
krishna@ubuntu:~$ sudo blkid -c /dev/null
```
[sudo] password for krishna: 
/dev/sda1: UUID="5ABCA255BCA22C07" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda5: UUID="E63CC0AC3CC07957" LABEL="Archana" TYPE="ntfs" 
/dev/sda6: UUID="929CC74B9CC72915" LABEL="Krishna" TYPE="ntfs" 
/dev/sda7: UUID="F2CCD07DCCD03D93" LABEL="New Volume" TYPE="ntfs" 
/dev/loop0: UUID="a100b06f-15ab-4f12-8666-62c47e7a8995" TYPE="ext3" 

```

---

### Post by kimikrishna on 2009-03-15
krishna@ubuntu:~$ cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0 
```

---

### Post by kimikrishna on 2009-03-15
krishna@ubuntu:~$ cat /etc/initramfs-tools/conf.d/resume```

cat: /etc/initramfs-tools/conf.d/resume: No such file or directory
```

---

### Post by kimikrishna on 2009-03-16
now wwhat ?

---

### Post by kimikrishna on 2009-03-17
](*,)](*,)](*,)](*,) no one got a solution :( :(

---

### Post by Ravernomina on 2009-03-17
Ugh -.- reinstall.... its not that hard if u cannot solve it reinstall!!! just make like a 5 gig partition on ur HHD and put all ur files their then format ur ubuntu partition their ur done :l.

---

### Post by philinux on 2009-03-17
> **Ravernomina said:**
> Ugh -.- reinstall.... its not that hard if u cannot solve it reinstall!!! just make like a 5 gig partition on ur HHD and put all ur files their then format ur ubuntu partition their ur done :l.

Advice to re-install is really a last resort thing.

---

### Post by philinux on 2009-03-17
I would install startupmanager, it's in synaptic. Menu item ends up up system>admin.

One option is to show text at start up. I'd tick this and then when sum has finished reboot. Then change sum to not show text. It might just fix it.

---

