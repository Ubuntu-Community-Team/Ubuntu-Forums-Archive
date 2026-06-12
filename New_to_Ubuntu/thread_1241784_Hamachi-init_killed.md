---
title: "Hamachi-init killed"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by justrivers on 2009-08-16
I'm having issues with Hamachi. The makefile and the tuncfg work fine but whenever I run 'hamachi-init' the terminal prompt immediately follows up with 'killed' so I cannot start the process. I've tried running it as 'hamachi-init' and as 'sudo hamachi-init', both respond killed.

System log shows this:
 Pid: 3530, comm: hamachi-init Tainted: G  

I can provide the full log detail if needed.

help...

---

### Post by lien_meat on 2009-08-31
I am also having the same issue running 9.10 all updates.  Never had this problem pre-karmic.  I'll post if I figure anything out, but I'm hoping someone else figures it out cause I don't think I will be able too.

---

### Post by LordJoNil on 2009-09-08
I have the same problem, using the Karmic alpha 5. Is there a good way to investigate what is really happening?

---

### Post by svetlisashkov on 2009-09-13
And I can confirm this too with karmic fully updated to 13 Sep 2009.

---

### Post by mapes12 on 2009-09-13
Hi Guys

Looks like someone needs to file a bug report: [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Would do it myself but I don't use Hamachi

If you're looking for Remote Desktop access then I use this: [https://launchpad.net/remote-help-assistant](https://launchpad.net/remote-help-assistant)

---

### Post by musikgoat on 2009-09-13
Can we file a bug report on a closed source software?  Wont it be invalidated pretty much immediately?

---

### Post by mapes12 on 2009-09-13
> **musikgoat said:**
> Can we file a bug report on a closed source software?  Wont it be invalidated pretty much immediately?You can file a bug report at any time in the lifecycle of a Ubu version.

If it's not reported it will not get fixed. The devs do not look around forum posts for issues. Hence the bug report database.

---

### Post by curtlee2002 on 2009-10-01
It is NOT a bug.  Hamachi's binary is compressed with upx. You just need to uncompress it.

Good Luck Guys

note: /usr/bin is were hamachi's binary was on my computer. 
```

sudo apt-get install upx-ucl
cd /usr/bin
sudo upx -d hamachi
                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
    830676 <-    331144   39.86%    linux/386    hamachi

Unpacked 1 file.

```

---

### Post by musikgoat on 2009-10-04
Sweet, that worked great!!

---

### Post by NachoKB on 2009-10-24
> **curtlee2002 said:**
> It is NOT a bug.  Hamachi's binary is compressed with upx. You just need to uncompress it.

Good Luck Guys


You are right, thanks.

Does anybody know why is it necessary? (I remember installing it without this step).

nachokb

---

### Post by 37452 on 2009-10-29
hi guys, sorry to bother up
i try to install hamachi with a guide from

hxxp://www.supware.net/HamachiUbuntuHowto/

n the problem comes when i try to 

$hamachi-init

the comment shows

hamachi-init: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

and when i install the upx-ucl and try to

/usr/bin$ sudo upx -d hamachi
 it shows

                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
upx: hamachi: NotPackedException: not packed by UPX

Unpacked 0 files.

any idea what's wrong with my step...
sorry if my english is bad
thx in advance

---

### Post by 37452 on 2009-10-29
hi guys, sorry to bother up
i try to install hamachi with a guide from

hxxp://www.supware.net/HamachiUbuntuHowto/

n the problem comes when i try to 

$hamachi-init

the comment shows

hamachi-init: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

and when i install the upx-ucl and try to

/usr/bin$ sudo upx -d hamachi
 it shows

                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
upx: hamachi: NotPackedException: not packed by UPX

Unpacked 0 files.

any idea what's wrong with my step...
sorry if my english is bad
thx in advance

---

### Post by justrivers on 2009-11-05
I used the unpack as mentioned above and my issue was fixed.  Thank you.  I never had that problem in Jaunty but in Karmic i had to do the unpack even when it was an upgrade from Jaunty where hamachi was already functioning.

---

### Post by Tman21901 on 2009-11-09
> **37452 said:**
> hi guys, sorry to bother up
i try to install hamachi with a guide from

hxxp://www.supware.net/HamachiUbuntuHowto/

n the problem comes when i try to 

$hamachi-init

the comment shows

hamachi-init: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

and when i install the upx-ucl and try to

/usr/bin$ sudo upx -d hamachi
 it shows

                       Ultimate Packer for eXecutables
  Copyright (C) 1996,1997,1998,1999,2000,2001,2002,2003,2004,2005,2006,2007
UPX 3.01        Markus Oberhumer, Laszlo Molnar & John Reiser   Jul 31st 2007

        File size         Ratio      Format      Name
   --------------------   ------   -----------   -----------
upx: hamachi: NotPackedException: not packed by UPX

Unpacked 0 files.


having the same problem, any ideas as to how to fix it?

---

### Post by HuoMaKe on 2009-11-11
> hamachi-init: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Try installing libstdc++6:

```
sudo apt-get install libstdc++6
```

Let me know if that works.

---

### Post by volodymyr on 2009-11-11
> **HuoMaKe said:**
> Try installing libstdc++6:

```
sudo apt-get install libstdc++6
```Let me know if that works.

It does not help. I also have the same problem. I had hamachi running on 9.04 and after update to 9.10 it fails with the following error:

hamachi: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I am running x64 ...

---

### Post by volodymyr on 2009-11-11
What is really strange, is that I have the version 6 of packet libstdc++6 installed:

```
sudo apt-cache policy libstdc++6
libstdc++6:
  Installé : 4.4.1-4ubuntu8
  Candidat : 4.4.1-4ubuntu8
 Table de version :
 *** 4.4.1-4ubuntu8 0
        500 http://ch.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by volodymyr on 2009-11-11
And I have libstdc++.so.5 in the same directory as hamachi resides:

```
/usr/bin$ ls | grep libstdc
libstdc++.so.5

```

---

### Post by volodymyr on 2009-11-12
Still trying to beat this issue. I created a link:

```
sudo ln -s /usr/lib32/libstdc++.so.6.0.13 /usr/bin/libstdc++.so.5
```

To put sym link libstdc++.so.5 to a libstdc++.so.6.0.13 but it does not work. Here is what I get anymore: 

```
/usr/bin/hamachi
/usr/bin/hamachi: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

---

### Post by Kar.ma on 2009-11-12
Hi, I just want to let you know that the "upx job" worked for me. I used hamachi without any problem with 8.10, now I'm trying 9.10 and it showed me the "Killed" issue, but now it works fine. 

I use Ubuntu in i386 version, so maybe amd (or was it x64?) version is related to other people's problem?

---

### Post by volodymyr on 2009-11-12
Most likely. I trued "upx job" and it did not worked for me :(

---

### Post by volodymyr on 2009-11-12
SOLVED: [http://www.shcherbyna.com/?p=402](http://www.shcherbyna.com/?p=402)

This solution helped me ;)

---

