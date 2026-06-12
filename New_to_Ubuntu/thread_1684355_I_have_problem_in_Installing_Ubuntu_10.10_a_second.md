---
title: "I have problem in Installing Ubuntu 10.10 a second time."
date: 2011-02-09
forum: New to Ubuntu
---

### Post by dstleanage on 2011-02-09
Hello Everybody.
This is the first time I'm Posting a Thread. And I hope somebody can help me with this.

1. I installed Ubuntu 10.10 for the first time using my entire disk in the laptop.

2. Secondly I installed Windows XP after dividing the HDD into partitions.

3. Installed XP into C drive and later tried to install Ubuntu into D drive after booting from CD ROM support.

4. But the Ubuntu setup does not get loaded. It gives an ISO error. I managed to view the process in command prompt view.

5. In that all the processes end up in "error" status. And at last the system gets stuck until I restart the machine manually. 

6. But i manged to install Ubuntu inside Windows. 

7. I want to install Ubuntu apart from Windows or install Ubuntu completely.

Need help for this process.

---

### Post by taseedorf on 2011-02-09
Burn a new ubuntu cd at the slowest possible speed (4x)  and retry

---

### Post by matt_symes on 2011-02-09
Hi 

In the future check the md5 hash sum before burning CD's. I think you have been unlucky and downloaded a corrupt iso.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Under windows

[http://www.cyberciti.biz/faq/linux-verify-md5-checksum-of-iso-file-using-windows-xp/](http://www.cyberciti.biz/faq/linux-verify-md5-checksum-of-iso-file-using-windows-xp/)

Kind regards

---

### Post by dstleanage on 2011-02-09
> **taseedorf said:**
> Burn a new ubuntu cd at the slowest possible speed (4x)  and retry


Hello,

Thank you very much for the solution.

But the CD which I'm using is a 1 which I got from 1 institute. Shall I try to install after buying the Ubuntu DVD? Will it be ok?

---

### Post by mastablasta on 2011-02-09
> **dstleanage said:**
>  
But the CD which I'm using is a 1 which I got from 1 institute. Shall I try to install after buying the Ubuntu DVD? Will it be ok?
 
yes it will be OK. but, have you no way of downloading the CD? Maybe a friend or relative?

---

### Post by matt_symes on 2011-02-09
Hi

If you are having trouble with CD's try creating a bootable USB and installing from that. Sometimes i have issues with bootable CD's as well but the same ISO on a USB will work. I have never bothered to look into why.

Under Ubuntu 

System->Administration->startup disc creator.

Under windows...

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Kind regards

---

