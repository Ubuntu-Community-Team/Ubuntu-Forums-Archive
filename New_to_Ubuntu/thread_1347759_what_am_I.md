---
title: "what am I?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by karmicgaz on 2009-12-06
Am I i386 or amd64? How can I tell?

---

### Post by desperado665 on 2009-12-06
run in terminal:

```
uname --all
```

---

### Post by lisati on 2009-12-06
One way of checking CPU info is from the terminal (assuming it's installed in your machine):
```
cat /proc/cpuinfo
```

---

### Post by aktiwers on 2009-12-06
```
uname -a
```

---

### Post by karmicgaz on 2009-12-06
Yes all well and good but I know what processor I have, I wish to know what version of ubuntu 9.10 i'm running, 32bit or 64bit. What is i686?

---

### Post by Nburnes on 2009-12-06
> **karmicgaz said:**
> Yes all well and good but I know what processor I have, I wish to know what version of ubuntu 9.10 i'm running, 32bit or 64bit. What is i686?

In Terminal run ```
uname -a
```

i686 is 32bit 
amd64 is 64bit

---

### Post by lisati on 2009-12-06
> **karmicgaz said:**
> Yes all well and good but I know what processor I have, I wish to know what version of ubuntu 9.10 i'm running, 32bit or 64bit. What is i686?

686 indicates 32-bit.

---

### Post by karmicgaz on 2009-12-06
Thankyou. Problem solved!

---

### Post by aktiwers on 2009-12-06
If its 32bit then in the output will be i686 GNU/Linux 
If it is 64bit then it will be x86 64 GNU/Linux
Edit: everyone beats me to it

---

### Post by Diametric on 2009-12-06
So, I ran the "uname --all" command as someone recommneded, my print was:

me@me:~$ uname --all
Linux me 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux

So, Whats up with the "i686" part - I thought a machine was i386 unless is was a 64bit processor?  Anyone?

Thanks for the original question and the replies.

Cheers,
Diametric

---

### Post by Nburnes on 2009-12-06
> **Diametric said:**
> So, I ran the "uname --all" command as someone recommneded, my print was:

me@me:~$ uname --all
Linux me 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux

So, Whats up with the "i686" part - I thought a machine was i386 unless is was a 64bit processor?  Anyone?

Thanks for the original question and the replies.

Cheers,
Diametric
i686 is simply what architecture your OS is built for, in this case 32 bit.

x86_64 is 64 bit.

---

