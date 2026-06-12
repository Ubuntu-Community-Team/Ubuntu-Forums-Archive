---
title: "autorun.inf automatically creates files"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by ngubk on 2011-04-08
I have a file named autorun.inf in my /home/user/download folder and in another partition(dev/sda4). It automatically creates a bunch of files(ctadxh.exe,jtxx.exe...) with random names, and the number of these files increase with time. I use sudo rm autorun.inf but after a few sec, it shows up again. The content of autorun.inf is like this:
[AutoRun]

;umavfclehkNtfgbqUgVlcucfR

;mVyk sArWrcWpgSr
shelL\EXPlore\comMand= cywcco.exe
;oJLGqB
sheLL\oPen\DeFAULt=1
;UiBwc murNAb 
open =cywcco.exe
;gYcCr YvKNot GrqDGIOkmmt hvvrjoxE BgjcCIvJddqoeoqWrmHx xTuUxmOgtHa 
shell\Open\comMaND =cywcco.exe
;
shell\AuToplAy\cOmmanD =cywcco.exe
;wEevE  uvoJjd 

And it's slightly different after each time i delete it though. Please provide me a way to delete it completely. Thank you very much

---

### Post by grahammechanical on 2011-04-08
I do not know the answer to this but I hope you do not have a Windows operating system installed. This might be a virus or a trojan.

autorun.inf files are usually on program CDs/DVDs and will automatically run a setup installer program on a Windows system to install a windows program. Perhaps you know this. Why would this file be on a hard disk?

If you do have a Windows operating system installed then the program causing the trouble may be on the Windows partition. It might be replicating itself to different parts of the hard disk. You delete one of these copies and the original trojan file replaces it. I do not know enough about this stuff to advise you but I think that you should be tracking down the file/program that is creating these inf files as soon as you delete them.

Regards.  Be glad the Linux does not run exe files.

---

### Post by ngubk on 2011-04-08
Oh! that's great! It's because i run virtualbox-winxp and share folders with ubuntu. I just have to reinstall virtual win xp and everything's as good as new. Thank's a lot

---

### Post by tgm4883 on 2011-04-08
That is most definitely a threat

---

