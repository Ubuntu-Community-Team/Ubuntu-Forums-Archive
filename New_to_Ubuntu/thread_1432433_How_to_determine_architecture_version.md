---
title: "How to determine architecture version"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by aboxorg on 2010-03-17
I am trying to figure out how to determine architecture version of the installed ubuntu version. Does anyone know how to figure this out or does i686 mean 32bit?

I have an AMD 64bit system but for a couple reasons I've come to think I installed the 32bit version. 

Is that even possible, to install the 32bit version and not 64bit and how would I know since I did this like a year ago.

I tried using "uname -a" and the properties tab in the system monitor didn't say 64bit except under the CPU not the version.

Linux abox-desktop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux

I am running 9.04. Should I upgrade? Does it make it even cooler?? :)

Thank you so much if you can help! ubuntu kicks ***!

-Avery Howell

---

### Post by llamabr on 2010-03-17
does

```
cat /proc/version 
```

tell you?

what about 

```
uname -m
```

also

```
cat /sbin/init/
```

That's where I'd start.

---

### Post by mickie.kext on 2010-03-17
> **aboxorg said:**
> 
Linux abox-desktop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux


If that is what you get when type **uname -a**, then you are running 32-bit version. i686 means 32-bit.

You want to know do you need 64-bit? You need first to tell specification of your computer, most important is amount of RAM.

---

### Post by lavinog on 2010-03-17
> **aboxorg said:**
> 

Linux abox-desktop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux

I am running 9.04. Should I upgrade? Does it make it even cooler?? :)


i686 is a 32bit architecture.

10.04 will be released next month, so you could wait until then.
Because of the drastic differences in underlying technologies (grub, ext4...etc) You may be better off doing a fresh install instead of an upgrade.

---

### Post by aboxorg on 2010-03-17
> **mickie.kext said:**
> If that is what you get when type **uname -a**, then you are running 32-bit version. i686 means 32-bit.

You want to know do you need 64-bit? You need first to tell specification of your computer, most important is amount of RAM.


Thank you very much for your response.

I have a AMD Athlon 64bit Processor 3200+ with **2.0GiB of Ram** (not sure about mem speed but I got the fastest at the time this system was new, I built it a few years back)

Do you think I would gain much from upgrading to the 64bit version of ubuntu and going to the latest release since I'm at 9.04? My cpu is pegged a lot and if this would help make it not be 90% most of the time it would be great !

Thank you again you're very nice <3  :KS

---

### Post by oldos2er on 2010-03-17
What CPU-intensive tasks are you running? If you're doing video encoding or something similar, you should see some improvement using 64-bit Ubuntu (which btw runs great on 2GB RAM).

---

### Post by mickie.kext on 2010-03-17
> **aboxorg said:**
> Thank you very much for your response.

I have a AMD Athlon 64bit Processor 3200+ with **2.0GiB of Ram** (not sure about mem speed but I got the fastest at the time this system was new, I built it a few years back)

Do you think I would gain much from upgrading to the 64bit version of ubuntu and going to the latest release since I'm at 9.04? My cpu is pegged a lot and if this would help make it not be 90% most of the time it would be great !

Thank you again you're very nice <3  :KS

Benefits of 64-bit can be seen if you have 4GB or more RAM.

With that hardware I'd say that it is not worth a hustle of reinstalling to go for 64-bit because you practically wont see the difference. 

But if you plan on reinstalling anyway, you might want to go for it.

---

