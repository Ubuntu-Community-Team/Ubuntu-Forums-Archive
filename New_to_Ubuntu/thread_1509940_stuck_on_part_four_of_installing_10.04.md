---
title: "stuck on part four of installing 10.04"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by eman949 on 2010-06-14
I don't get any options on step four of the installing process. Can anyone please help me??

---

### Post by jtarin on 2010-06-14
Refresh my memory ......what is exactly step 4, your having problems with?

---

### Post by eman949 on 2010-06-14
hard disk partitioning

---

### Post by sb5551 on 2010-06-14
What exactly do you want to do? Install just Ubuntu on the computer or dual boot or something else?

---

### Post by guthix0009 on 2010-06-14
Try and get a new disk i had the same problem except it wouldn't even boot up

---

### Post by the.phantom on 2010-06-14
this downloadable PDF might help you a bunch?

(free)


"A Complete Beginner's Manual for Ubuntu 10.04 (Lucid Lynx)"

[http://ubuntugeek.tradepub.com/?pt=adv&page=Ubuntu%20Manual%20Project](http://ubuntugeek.tradepub.com/?pt=adv&page=Ubuntu%20Manual%20Project)

---

### Post by eman949 on 2010-06-14
ok should i change anything while burning the cd

---

### Post by lisati on 2010-06-14
Threads merged. Please do not create duplicate threads on the same subject, it can get confusing trying to follow what help has been offered.

---

### Post by guthix0009 on 2010-06-14
Burn it at a slower speed i usually burn ISO's at 4x but just burn as low as you can i recommend using PowerISO

---

### Post by eman949 on 2010-06-15
ok thanks

---

### Post by eman949 on 2010-06-15
I burned it again but i still get the same problem the screen looks like this...

---

### Post by sandyd on 2010-06-15
> **eman949 said:**
> I burned it again but i still get the same problem the screen looks like this...
you might have one of those weird, random SATA/RAID/SCSI/IDE controlers that are still not supported.

go to Applications -> Accessories -> Terminal
and type in```

lspci
```
post the output.

---

### Post by PremiereWebDesign on 2010-06-15
Initially, I had the same problem. Then, I tried unplugging my external hard drive as I noticed due to the blinking lights that something was going on with the external. Once I unplugged it, I didn't have any more problems. Installation was a breeze. So, if you are running any kind of external, you may want to try unplugging it and see what happens.

---

