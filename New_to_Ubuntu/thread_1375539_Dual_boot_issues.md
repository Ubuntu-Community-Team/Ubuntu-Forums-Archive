---
title: "Dual boot issues"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by solomon316 on 2010-01-08
Hello again everybody, here I am again with another problem.  I have been running ubuntu 9.1 and I love it.  I was running a dual boot with windows xp, only using windows for my zune.  I went and reformatted the windows partition and installed windows 7 (the wife wants it)  Now, my grub boot loaded disappeared.  My laptop boots straight into windows 7 and I cannot get into my ubuntu at all unless I boot with the distro disk.  How can I get my grub bootloader back?  BTW, before installing win 7 the dual boot between the 2 OSs worked perfectly.  Please help

---

### Post by Chilli Bob on 2010-01-08
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)


Try step 4 again and see if if it fixes grub.

---

### Post by solomon316 on 2010-01-08
I tried this.  when I type find /boot/grub/stage1  it comes back with file not found.....

---

### Post by audiomick on 2010-01-08
Hi.
I think you are trying to follow a guide for grub legacy when you have grub2 on the computer. If your 9.10 was a fresh install, not an update, it will be grub 2. The re-install process has changed.
Look at herman's how to
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

and/or the ubuntu grub2 documentation
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by solomon316 on 2010-01-08
my apologies, it was an upgrade from 9.04 to 9.10....  my disk is 9.04   sorry i didn't post that

---

### Post by audiomick on 2010-01-08
Ok, so it should still be grub legacy.

Maybe you could follow the steps here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
to see what the state of affairs is. Post the results back here, if you can't make sense of it.

---

### Post by solomon316 on 2010-01-09
I ran sudo grub      grub> find /boot/grub/stage1      termianl came back with cannot find file...  I am lost with a lot of this.....

---

### Post by solomon316 on 2010-01-09
BTW I am in a community internet center in afghanistan.....  I have no internet connection for my laptop to download anything....  I installed ubuntu 9.04 and upgraded it to 9.10    I love Ubnutu but with Win7 take over everything, I just need to get my grub back...thanks again guys....

---

### Post by yanceypd on 2010-01-09
If you can gey into terminal try
 sudo update-grub

---

### Post by talsemgeest on 2010-01-09
> **solomon316 said:**
> BTW I am in a community internet center in afghanistan.....  I have no internet connection for my laptop to download anything....  I installed ubuntu 9.04 and upgraded it to 9.10    I love Ubnutu but with Win7 take over everything, I just need to get my grub back...thanks again guys....
Unfortunately, to reinstall the grub (grub 2 for ubuntu 9.10), you will need the Ubuntu 9.10 live cd. Once you have a live cd, follow the instructions for Ubuntu 9.10 [here](http://ubuntuforums.org/showthread.php?t=1014708).

---

### Post by solomon316 on 2010-01-10
Ok, maybe I cannot search well at all but I have new issues.....  I started with a dual boot of winxp and 9.04 then did the online upgrade to 9.10   Upgraded to win 7 lost my grub loader......   Had probs with win 7 (windows, go figure) installed 9.04 trying to get grub back....  Now, grub lists 9.04 and 2 installs of 9.10   when i highlight either 9.10, i get error 17 could not mount partition....  How do I fix this?  I just want to use my 9.10, having problems with everything but 9.1   only have live cd for 9.04 (online upgrade to 9.1

Thanks guys

---

### Post by talsemgeest on 2010-01-10
> **solomon316 said:**
> Ok, maybe I cannot search well at all but I have new issues.....  I started with a dual boot of winxp and 9.04 then did the online upgrade to 9.10   Upgraded to win 7 lost my grub loader......   Had probs with win 7 (windows, go figure) installed 9.04 trying to get grub back....  Now, grub lists 9.04 and 2 installs of 9.10   when i highlight either 9.10, i get error 17 could not mount partition....  How do I fix this?  I just want to use my 9.10, having problems with everything but 9.1   only have live cd for 9.04 (online upgrade to 9.1

Thanks guys
All I can think of is that you need to get an ubuntu 9.10 live cd. 9.04 does not have the tools necessary to fix the 9.10 bootloader, and vice-versa.

---

### Post by oingk on 2010-01-10
maybe someone can point him to a place on the net to download it and exaplain in a simple way how to make a live CD.

then this person can ask from the gentlemen at the internet community to let him make only one download. Or he can even probbably download without asking them. He can just download it on his USB memory stick. And when he goes home, he can burn it onto a DVD.

I hope this helps, good luck.

---

### Post by oingk on 2010-01-10
The others can correct me if I'm wrong, but you can download ubuntu 9.10 here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

