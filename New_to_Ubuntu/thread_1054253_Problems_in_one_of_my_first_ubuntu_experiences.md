---
title: "Problems in one of my first ubuntu experiences"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by nerotkd on 2009-01-29
Hello, first, sorry about my bad english, i'm from Argentina and my first language is spanish...

I tried ubuntu with the 6.06 live cd a few years ago, and now i want to install 8.10 and i have some problems...

I downloaded the iso, MD5-checked the download, and burned it in a empty cd rom...

When i reboot the pc i can see the menu with options... Then i select Install without made changes in my system (I dont remember the exact label)... And then... And then... I got a window saying Error reading boot cd, and in the upper left corner it says 104200EF

I have burned 3 times the iso (With MagicIso, InfraBurn... With differents burning speeds [from 4x to 24x])...
Also, i have tried with the 8.04LTS version and i have the same problem...

---

### Post by Dedoimedo on 2009-01-29
Do you have another cd/dvd drive?
Dedoimedo

---

### Post by nerotkd on 2009-01-29
Oh, i forgot to say... I tried to use it in other cd/dvd drive and i have the same problem. I haven't tried to burn it in other drive...

---

### Post by avtolle on 2009-01-29
Are you trying to install on the same computer upon which you tried 6.06? If so, you might try burining the iso as an image to a CD-R (if you used a CD-RW at first); older CD-ROM drives seem to handle CD-R disks better, and also the slower the better (4x has worked best for me on older hardware). You might also do a CD integrity check from the initial menu before trying to install to see if any errors are reported.

---

### Post by nerotkd on 2009-01-29
Yes, it's the same computer, and its a CD-R.. If i try to do the cd integrity test i have the same error...

---

### Post by avtolle on 2009-01-29
Since you are receiving the same error on the CD integrity test, it is my thought you have a bad burn. Try burning another CD-R using the other drive to see if you get the same error.

---

### Post by egalvan on 2009-01-29
> **nerotkd said:**
> 

I have burned 3 times the iso (With MagicIso, InfraBurn... With differents burning speeds [from 4x to 24x])...
Also, i have tried with the 8.04LTS version and i have the same problem...

First, have you run the "check CD for errors" option on the boot screen?
This clears the CD of being the problem.

If this passes, next run the "memcheck" option.
This clears most of the hardware of being the problem.

And even though it is likely not the cause of this problem...
your hard drive may be going bad.
Try to test it. manufacturer's web-sites have test software you can download.

My vote is flaky memory.

P.S.
try cleaning the inside of the machine... dust build-up can cause over-heating.
Again probably not the immediate cause, but still a good idea.

---

### Post by bobbob1016 on 2009-01-29
> **nerotkd said:**
> Hello, first, sorry about my bad english, i'm from Argentina and my first language is spanish...

I tried ubuntu with the 6.06 live cd a few years ago, and now i want to install 8.10 and i have some problems...

I downloaded the iso, MD5-checked the download, and burned it in a empty cd rom...

When i reboot the pc i can see the menu with options... Then i select Install without made changes in my system (I dont remember the exact label)... And then... And then... I got a window saying Error reading boot cd, and in the upper left corner it says 104200EF

I have burned 3 times the iso (With MagicIso, InfraBurn... With differents burning speeds [from 4x to 24x])...
Also, i have tried with the 8.04LTS version and i have the same problem...

Is your CD/DVD Rom unusual?  If the MD5 was ok, it could be some hardware.  Did you try the CD's  on another computer?  If a disc works on another computer it could be some weird hardware/bios setting.

Also, your English is fine.  Apart from a few small grammar mistakes like using "i" instead of "I", you used "made" instead of "making", "made" vs "making" is like "hecho" vs "haciendo".

---

### Post by nerotkd on 2009-01-29
I can't start the memcheck (same problem!)... I don't think that this is a mem or hd problem, they are in good status...

---

### Post by egalvan on 2009-01-29
> **nerotkd said:**
> Oh, i forgot to say... **I tried to use it in other cd/dvd drive and i have the same problem.** I haven't tried to burn it in other drive...

Another drive on the same computer?
This still leaves most of the hardware untested..

or on another computer?

This points to a bad burn.

Which computer did you burn on?
The burn may be bad because of bad hardware.

---

### Post by nerotkd on 2009-01-29
on another computer... Ok, i will buy today a new cd/dvd drive to test if the burn is bad...

Thank to all you for a so fast help!

---

### Post by egalvan on 2009-01-29
> **nerotkd said:**
> I can't start the memcheck (same problem!)...** I don't think that this is a mem or hd problem, they are in good status.**..

How do you know this is true?

---

### Post by egalvan on 2009-01-29
> **nerotkd said:**
> on another computer... Ok, i will buy today a new cd/dvd drive to test if the burn is bad...

Thank to all you for a so fast help!

Before you spend the time and money for new hardware...

can you download, md5sum check, burn and check the ISO on another computer?


(Unless you are looking for an excuse to buy new hardware :) )

---

### Post by nerotkd on 2009-01-30
I really need the new drive...
I bought it, but i forgot to buy a new sata cable, so, i can't connect it yet...
I will try with a slooower burn speed now...

---

### Post by ady2e on 2009-01-30
I know this is probably the wrong thread, but i am having serious difficulties getting my atheros ar5007eg to work.  the system is 32 bit as well.  i have found a few threads that walk through how to do it, but they are all using a inf file that i can not find.  (I can only find the 64 bit version)  does anyone know where the 32 bit is?  link?

Thanx a bunch.

---

### Post by twister077 on 2009-09-07
Hello everyone.
I'm using Ubuntu for 6 month now. Ubuntu was my first linux experience.
And I'm quite surprised about Ubuntu and linux. 

I've installed Ubuntu quite often on other PC's.
But now I stumble upon one tricky problem.

I've posted in the Dutch Ubuntu forum what I found out about this errorcode you're
having.
[http://forum.ubuntu-nl.org/installatie/ubuntu-live-cd-geeft-input-output-error-code-104280ef-aan/](http://forum.ubuntu-nl.org/installatie/ubuntu-live-cd-geeft-input-output-error-code-104280ef-aan/)

Use BabelFish or something to translate.

Keep up the good work. Stay open(source).

Best regard,
Twister077

---

