---
title: "kodak printer drivers"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by ECET on 2011-03-07
OK....I know that some companies don't provide us linux folks with the drivers we need....so I have looked online...can't seem to find any drivers for my kodak 5200 series....please tell me someone out there has a fix.....I'm so sick and tired of having to go into M$ to print stuff......Thanks......

---

### Post by bkratz on 2011-03-07
Similar thread sometime ago, for the 5250 but maybe worth a try.

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9016982&postcount=20](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9016982&postcount=20)

---

### Post by ECET on 2011-03-07
thanks bkratz....I went to link...downloaded it...but it gave me an error saying "not i386".....I have no idea what that means......but thanks for the link, it almost helped!......anyone else?.....

---

### Post by plucky on 2011-03-08
> **ECET said:**
> thanks bkratz....I went to link...downloaded it...but it gave me an error saying "not i386".....I have no idea what that means......but thanks for the link, it almost helped!......anyone else?.....

What version of Ubuntu are you running? 

From a terminal ```
uname -a
``` and post output.

I just downloaded that file and Software Cemtre opened and asked if I wanted to install. I am running Ubuntu Maverick 10.10.


Good Luck

---

### Post by ECET on 2011-03-08
thank you...I'm running 10.4 and after entering the code I got this:  2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

thanks for any info you may be able to provide.....

---

### Post by TBABill on 2011-03-08
That i386 means that what you tried was meant for the 32 bit version of Ubuntu, but you are running 64 bit (x86_64).

---

### Post by ECET on 2011-03-08
so...basically I can not use this driver......bummer....ok, well if anyone else has a link, or the ability to help me with this printer, please do....thanks.....

---

### Post by TBABill on 2011-03-08
You can probably do a "force architecture" command to make it work, but I don't have the experience toying with it to guide you. But if you search for that term you may find something that can help you use it.

---

### Post by plucky on 2011-03-08
For Brother printers a requirement for 64 bit systems is to install 32 bit libraries.
Try installing ia32-libs first and see what happens when you install the deb.

> Related distributions
    Debian 64 bit version, Ubuntu 64 bit version
    Related products/drivers
    printer/PC-FAX drivers
    Requirement
    ia32-libs or lib32stdc++ is required to be installed.

Good Luck

---

