---
title: "Am I running on 64Bit?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by Johnecash on 2009-08-03
I have Ubuntu runnning on this
 
Compaq Presario Desktop PC 1.6 GHz AMD Athlon X2 4200 Dual Core Processor, 1 GB RAM
 
I dont recall it asking for me to select 32 bit or 64 bit on install - can anyone help?
 
Is there a command to check?
 
I intsalled ubuntu version 9.04

---

### Post by juancarlospaco on 2009-08-03
**uname -a ; lsb_release -a**

---

### Post by Sef on 2009-08-03
Applications > Accessories > Terminal

then copy and paste this command:

```
uname -a
```

If you have 64-bit, it will say this (my highlighting):

> Linux jokat0 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 **x86_64 GNU/Linux**


---

### Post by Johnecash on 2009-08-04
Hi guys I get this

-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

is there anyway to tell if I can get it running on 64 Bit?

---

### Post by lisati on 2009-08-04
> **Johnecash said:**
> Hi guys I get this

-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 [COLOR="Teal"]i686[/COLOR] GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

is there anyway to tell if I can get it running on 64 Bit?

It looks like you're using the 32-bit version. I don't know of a "quick and easy" way of "upgrading" to 64-bit without making a backup of your data and oing a fresh install of the 64-bit version. I understand that the process can sometimes be simplified if you've set up a separate partition for your data.

---

### Post by binbash on 2009-08-04
You are using 32bit

---

### Post by Johnecash on 2009-08-04
I am happy to do the back-up and upgrade 

is the 64 bit version heaps better?

do you think my box will handle 64 bit anyway?

---

### Post by Viva on 2009-08-04
You won't see too much performance gain. I'd say, keep it as it is for now and try the 64 bit version when Karmic is released.

---

### Post by Johnecash on 2009-08-04
ok will do thanks for the advise

---

### Post by theozzlives on 2009-08-04
With only 1 GB RAM, you really don't need 64 bit.

---

### Post by eternalsword on 2009-08-04
Unless you're doing cpu intensive stuff (scientific computations, 3D rendering, video encoding encoding, significant amount of source code compilation, etc) you probably would not notice much of a performance difference.  

To determine if you are capable of running 64-bit, just check your cpuinfo for the lm flag. 

```
grep flags /proc/cpuinfo
```

If lm is listed, you can run 64-bit.

---

### Post by 3rdalbum on 2009-08-04
64-bit operating systems do use a little more RAM than 32-bit. If you've only got a gigabyte of RAM, then you might want to stay with 32-bit as it will result in more memory available for cache.

---

### Post by mikechant on 2009-08-04
> Unless you're doing cpu intensive stuff (scientific computations, 3D rendering, video encoding encoding, significant amount of source code compilation, etc) you probably would not notice much of a performance difference. 

I do a lot of video rendering, so I benchmarked 9.04 32bit vs 64 bit using the 'DeVeDe' application (which I believe uses mencoder for video conversion) and got **exactly** the same results on 32 and 64 bit. I used the relevant repository versions in each case so they should have been correctly built for 32 or 64 bit. Still, maybe I was doing something wrong...

---

