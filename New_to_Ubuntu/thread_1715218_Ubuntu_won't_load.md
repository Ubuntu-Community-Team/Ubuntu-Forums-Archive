---
title: "Ubuntu won't load"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by denmanjum on 2011-03-26
After installing Ubuntu and after the reboot when I choose which OS to use after start up I chose Ubuntu and it just hangs there like it's loading but it never loads.
I've tried several installs but the exact thing happens every time.

I've created a CD and a USB copy and have tried both.



I've created a partition on  my HD.

I'm running XP pro on an X86 based system

---

### Post by laerub18 on 2011-03-26
which ubuntu did you install ? 
how much space does the ubuntu partition have ?

> I've tried several installs but the exact thing happens every time.
do you mean you tried reinstalling ubuntu on the same partition several times ?

when you say it never loads, how long did you wait ? i just did an install and it took some time the first time to load..


do you get to the login screen or not even ?

---

### Post by denmanjum on 2011-03-26
> **laerub18 said:**
> which ubuntu did you install ? 
how much space does the ubuntu partition have ?


do you mean you tried reinstalling ubuntu on the same partition several times ?

when you say it never loads, how long did you wait ? i just did an install and it took some time the first time to load..


do you get to the login screen or not even ?

I installed  10.10. I created a partition and gave it 20 g.
When I reboot and choose Ubuntu the I see the logo see and it trying to load but nothing happens. Each time I tried an install I cleaned all of the Ubuntu files out before hand and started fresh.
 I've waited as long as 20 min.

---

### Post by Quackers on 2011-03-26
Does the screen go black? Does HDD activity stop? Did you need to use a boot option (like nomodeset, for instance) to get the live cd to work?

---

### Post by denmanjum on 2011-03-26
> **Quackers said:**
> Does the screen go black? Does HDD activity stop? Did you need to use a boot option (like nomodeset, for instance) to get the live cd to work?


  After the reboot and choosing Ubuntu  the screen that comes up says "Ubuntu" It just hangs there like it's trying to load. sort of looks like this


                  Ubuntu
                  .......

With the dots at the bottom  going through the loading motion as any program trying to load.

---

### Post by FootySr on 2011-03-27
> **denmanjum said:**
> After the reboot and choosing Ubuntu  the screen that comes up says "Ubuntu" It just hangs there like it's trying to load. sort of looks like this


                  Ubuntu
                  .......

With the dots at the bottom  going through the loading motion as any program trying to load.

I had this happen to me once during a clean install of Ubuntu because I had a usb headset connected. Weird but once I unplugged headset it fired right up.

---

### Post by arvevans on 2011-03-27
Usually a hardware incompatibility.  Try a text-based install to see what is actually happening:

[INDENT][http://ubuntuforums.org/showthread.php?t=1554331]("http://ubuntuforums.org/showthread.php?t=1554331")[/INDENT]

---

### Post by jramshu on 2011-03-27
My brother couldn't get his to boot until we unplugged a USB driven cooling fan, unplugged it and tried again and it booted.

---

### Post by ugm6hr on 2011-03-29
> **arvevans said:**
> Usually a hardware incompatibility.  Try a text-based install to see what is actually happening:

[INDENT][http://ubuntuforums.org/showthread.php?t=1554331]("http://ubuntuforums.org/showthread.php?t=1554331")[/INDENT]

Actually, it's usually a corrupt download in my experience, except when very new hardware is concerned. Any hardware sold with XP should at least boot OK.

Check the "md5sum" to ensure your download is OK. If you used the same download to create CD & USB - they may both have the same error.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

