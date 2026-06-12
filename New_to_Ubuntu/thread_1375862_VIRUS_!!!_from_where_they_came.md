---
title: "VIRUS !!! from where they came????"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-01-08
i can't believe my self !! even linux has viruss !! anybody knows how to remove such these files with exe extension?? .every time i removed .it return again in all my folders, this partitions was formated with ntfs 
i need some help

---

### Post by HappyFeet on 2010-01-08
Go to your home folder and edit>preferences>behavior tab and check off **Include a delete command that bypasses trash**. Then you can right click those files and permanently delete.

---

### Post by fromthehill on 2010-01-08
linux doesn't prevent you from downloading anything
if you go to some dodgy site and download virus.exe linux will not stop you

those files can't do you any harm though
they're windows executables

---

### Post by MichealH on 2010-01-08
That might be your problem Formatting with NTFS or Having Wine may cause and/or excecute  these if you have Wine It would be a safe option because it may infect your and  Wine you know what Windows (or in this case a duplicate of a bare Windows) is like when it gets infected ;)

---

### Post by supercatexpert on 2010-01-08
Linux can also be infected with the viruses which run under Windows by wine.
From the picture you posted, I guess that you might install wine, and used it to run an infected executable file. You can try to kill the processes of wine (like wine, wineserver, etc). Then delete the directory of wine under your home directory (~/.wine), wine can rebuild the directory by itself (notice that data may lose).
There are about 200 kinds of viruses which can infected Linux. I think, if you really infected by the real Linux Virus, you can try to buy some lotteries. ~~~:)

---

### Post by MBG1987 on 2010-01-08
thanks 4 the replies!

No, i'm not using WINE, actually i'm using VBox to run xp on ubuntu,just for tests and ,i think that xp cause this problem,so i will remove windows xp if that the  reason , but what about those files they are existing in all folders and it will be very difficult to delete them, is there an anti-virus or such app???

---

### Post by Captain_tux on 2010-01-08
A Windows virus will not and CANNOT affect a Linux system.

---

### Post by jonobe on 2010-01-08
For anti-virus: CLAMAV is a popular one for linux.


But don't Panic!

As others are saying above: .exe files are completely inert on Linux, so you're immune as far as these type are concerned.  Do what you want with them, just don't pass them on to those less privileged than you (ie Windows users);)

---

### Post by ankspo71 on 2010-01-08
Hi,
To answer the question in the title of your post, I think it might have come from an email attachment. [http://www.bitdefender.com/VIRUS-1000466-en--Win32.Worm.Mabezat.J.html](http://www.bitdefender.com/VIRUS-1000466-en--Win32.Worm.Mabezat.J.html) 
I found it by searching for winrarserialinstall.exe.  ( if that is the same virus)

---

### Post by bodhi.zazen on 2010-01-08
> **Captain_tux said:**
> A Windows virus will not and CANNOT affect a Linux system.

It is possible, in theory, if you run the virus by running wine as root =)

With that said, there are no currently active viruses in the wild. Up to now the Linux viruses have been a "proof of concept" type of a thing and your Linux system (unlike windows) was patched long ago.

---

### Post by lisati on 2010-01-08
I haven't used Wine much but the last time I checked there was an option in its settings to allow access to /. It might be a good idea to check that it is disabled if you don't need to access your regular Linux files from Wine. Just as a precaution.

---

### Post by Marisa H on 2010-01-08
So in Ubuntu you can tell if you have a virus because there are random executables with no purpose?

---

### Post by fromthehill on 2010-01-08
> **ankspo71 said:**
> Hi,
To answer the question in the title of your post, I think it might have come from an email attachment. [http://www.bitdefender.com/VIRUS-1000466-en--Win32.Worm.Mabezat.J.html](http://www.bitdefender.com/VIRUS-1000466-en--Win32.Worm.Mabezat.J.html) 
I found it by searching for winrarserialinstall.exe.  ( if that is the same virus)

WHY did you even save an attachement with a name like that :P

---

### Post by Captain_tux on 2010-01-08
> **bodhi.zazen said:**
> It is possible, in theory, if you run the virus by running wine as root =)

Ah, you're adding caveats to the discussion ;)

But yes, you're right... hence why Linux doesn't run as root by default.

---

