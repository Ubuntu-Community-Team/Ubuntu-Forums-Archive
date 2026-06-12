---
title: "how do i remove the boot choice?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by samtaleterapi on 2009-05-06
hi

i have removed ubuntu
i had installed it inside windows
during the boot process i still have to choose between xp and ubuntu (or wait 30 secs)
is there a straight forward way to eliminate this?
so xp just starts up without delay?

thanks
rasmus

---

### Post by kpkeerthi on 2009-05-06
[http://www.windowsinternals.com/fixing-a-missing-or-corrupt-windows-bootloader-with-fixmbr/]("http://www.windowsinternals.com/fixing-a-missing-or-corrupt-windows-bootloader-with-fixmbr/")

---

### Post by cholericfun on 2009-05-06
since you removed ubuntu i'm not so sure how to "hack" around this
but try inserting the xp cd and theres some FIXMBR command in repair mode

google it to find out exactly what the commands are..

---

### Post by Bradtek on 2009-05-06
Wouldn't this question be more appropriate in a Windows forum ?

But anyway, in a recovery console type fixmbr

---

### Post by triunenature on 2009-05-06
> **Bradtek said:**
> Wouldn't this question be more appropriate in a Windows forum ?

But anyway, in a recovery console type fixmbr

I do believe this is a Ubuntu problem, since ubuntu broke it... LoL

---

### Post by El Zoido on 2009-05-06
Ok, I'm not sure if it will work, but you can try this:

Go to System preferences -> System -> Advanced -> Start and recovery

There you find the Settings for Windows' Boot-manager.
If Wubi is installing Grub however, it probably won't work.

P.S.: I don't have an english version of Windows installed, so it may be that the names I gave you will be slightly different.

---

### Post by mikezila on 2009-05-06
If you used Wubi, then it's the Windows bootloader that you are seeing, and an extra entry has been added to it for the Wubi installation.  It should have been removed when you used the Wubi uninstaller.

---

### Post by Paddy Landau on 2009-05-06
> **triunenature said:**
> I do believe this is a Ubuntu problem, since ubuntu broke it... LoL
Well, when Windows broke my Ubuntu installation, I had to come here to have it fixed...

Anyway, try EasyBCD -- I found it useful when I had a similar problem.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

You can also get it here:

[http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html](http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html)

---

### Post by Insanity01 on 2009-05-06
what i'm gonna tell you know will work for sure, cause i did so to remove my openSUSE
 
You download easyBCD, you open it, on it you get a screen saying wich things are there to be booted, click options, click on the OS name you want to delete, click delete...fairly easy thing to do, but don't go mess around with easyBCD ;)

EDIT: Just realised the guy's post above me says exactly the same thing... lol

---

### Post by samtaleterapi on 2009-05-07
thank you for all the ideas
unluckily i dont have an xp cd because my laptop is an acer that has the installation files on a seperate partition instead of a cd
i tried downloading easybcd but only got quad registry cleaner that crashed my system
in the system proporties, advanced, start and system regeneration, edit start preferences (i also do not have an english version of xp) the boot sequence is

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

is there something i can remove and solve the problem?

thanks
rasmus

---

### Post by mikezila on 2009-05-07
C:\wubildr.mbr = "Ubuntu"

remove that and reboot

---

### Post by samtaleterapi on 2009-05-10
yeah that worked just fine
thanks everyone
rasmus

---

### Post by bonkadventure2 on 2009-05-10
I have been looking for how to do this too. Now, I don't need to anymore, but whatever. I still use Ubuntu. I was trying to install Wubi 9.04, so I uninstalled and installed 9.04, which failed because the ubuntu 8.10 entry already existed, so it couldn't make TWO ubuntu entries. :)

---

### Post by Lolli Pop on 2009-05-24
Download Tune-Up Utilities:

[http://www.tune-up.com/products/tuneup-utilities/](http://www.tune-up.com/products/tuneup-utilities/)

Install It And Run Registry Cleaner, It Should Find The Registry Entry (If There Is One) And Remove It.

---

