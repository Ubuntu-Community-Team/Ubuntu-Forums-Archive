---
title: "concerns about removing windows vista"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by kfrancist on 2010-07-08
i currently have a dual boot setup on my laptop with ubuntu 10.04 and  windows vista.  i would now like to remove windows vista entirely.

the problem is, i'm worried what will happen to my ubuntu setup (and my  wireless driver in particular) if i just delete or reformat the vista  partition.  

not too long ago, i completely screwed up my windows partition and had  to reinstall vista.  during the time that windows was nonfunctional, my  wireless wouldn't work in ubuntu at all--and it had something to do with  the driver and "ndiwrapper" if i remember correctly (this was a few  months ago).  and once i got vista up and running again the problem went  away.

so is ubuntu actually dependent on some of the drivers in my windows  system?  if so, is my wireless device the only thing i need to worry about?  and what do i have to do to fix this before i remove windows?

and in case you need to know, this is what i have for a wireless device:
Realtek RTL8187B(802.11b/g)

and my laptop is a gateway m6308

thanks

---

### Post by sandyd on 2010-07-08
> **kfrancist said:**
> i currently have a dual boot setup on my laptop with ubuntu 10.04 and  windows vista.  i would now like to remove windows vista entirely.

the problem is, i'm worried what will happen to my ubuntu setup (and my  wireless driver in particular) if i just delete or reformat the vista  partition.  

not too long ago, i completely screwed up my windows partition and had  to reinstall vista.  during the time that windows was nonfunctional, my  wireless wouldn't work in ubuntu at all--and it had something to do with  the driver and "ndiwrapper" if i remember correctly (this was a few  months ago).  and once i got vista up and running again the problem went  away.

so is ubuntu actually dependent on some of the drivers in my windows  system?  if so, is my wireless device the only thing i need to worry about?  and what do i have to do to fix this before i remove windows?

and in case you need to know, this is what i have for a wireless device:
Realtek RTL8187B(802.11b/g)

and my laptop is a gateway m6308

thanks
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

See option #2 first since your using a new distro.
can you post the output of 
```

uname -a
```?

because if your using 2.6.27, it should work out of the box as always, without ndiswrapper. and ndiswrapper is not the right way of doing it anyways.

---

### Post by kfrancist on 2010-07-08
thanks for the quick reply!  here's the output of uname -a:

Linux ASSKICKATRON 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

so, it appears i've got a later version of the kernel.  shouldn't that be even better?:p

and just so ya' know my wireless worked right out of the box.  i never messed with any settings.  so i'm thinking ndiswrapper was the default "solution" somehow.

---

### Post by sandyd on 2010-07-08
> **kfrancist said:**
> thanks for the quick reply!  here's the output of uname -a:

Linux ASSKICKATRON 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

so, it appears i've got a later version of the kernel.  shouldn't that be even better?:p

and just so ya' know my wireless worked right out of the box.  i never messed with any settings.  so i'm thinking ndiswrapper was the default "solution" somehow.
then your good to go! :)

---

### Post by kfrancist on 2010-07-08
ok...thanks!

so i guess i'll just go ahead and remove windows.

and if i get that same problem, should i just post another message in this thread?  or would it be better to start a new one?

---

### Post by sandyd on 2010-07-08
> **kfrancist said:**
> ok...thanks!

so i guess i'll just go ahead and remove windows.

and if i get that same problem, should i just post another message in this thread?  or would it be better to start a new one?you can just continue here, although there shouldn't be any problems.

---

