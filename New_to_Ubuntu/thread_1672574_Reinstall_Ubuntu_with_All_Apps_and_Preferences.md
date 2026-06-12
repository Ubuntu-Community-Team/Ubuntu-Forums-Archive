---
title: "Reinstall Ubuntu with All Apps and Preferences?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Alamantus on 2011-01-21
Hello anyone!

I am looking to reinstall my Ubuntu to my HD with all of my applications and settings the way they originally were (it is already installed, but I want to reinstall it [SIZE="1"][because I messed something up while working with Gparted - but that's not my problem so don't worry about it][/SIZE]).

Is there an easy way to do this? Or better yet, can I copy the whole Ubuntu partition to an external hard drive, reinstall Ubuntu, and then paste the partition I copied back into the fresh install, overwriting all the old ones?

I simply want to have *everything back the way it was before I reinstalled it*.

---------------------------------------

[SIZE="1"]***Some background on why I need to do this, though it has little to no bearing on my question:***
I tried to install Meego to my netbook. My netbook was already dual booted with Windows XP and Ubuntu 9.10, and Meego doesn't play nice with Ubuntu. It refused to install, saying there was not enough free space even though I had just freed up a lot of space for it (13 Gigabytes). So long story short, to install Meego alongside everything else, I need to uninstall Ubuntu, start with just windows, then install Meego, and then lastly reinstall Ubuntu. And that's why I'm asking my question.[/SIZE]

Thanks in advance for the answer!

---

### Post by Linyx on 2011-01-21
Check this out > [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Also > [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by Verbeck on 2011-01-21
try remastersys
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Alamantus on 2011-01-21
Oh wow! That sounds like a great solution! Thanks!

Do I just apt-get it or something?

---

### Post by Linyx on 2011-01-21
> **Alamantus said:**
> Oh wow! That sounds like a great solution! Thanks!

Do I just apt-get it or something?

Check out my 2nd link for that...

Also > [http://linux.softpedia.com/get/Utilities/Remastersys-26479.shtml](http://linux.softpedia.com/get/Utilities/Remastersys-26479.shtml)


Good luck

---

### Post by Alamantus on 2011-01-21
> **Linyx said:**
> Check out my 2nd link for that...

Also > [http://linux.softpedia.com/get/Utilities/Remastersys-26479.shtml](http://linux.softpedia.com/get/Utilities/Remastersys-26479.shtml)


Good luck
Ohhh, haha, duh. Sorry about that - didn't read far enough. 

Thanks a lot!

---

### Post by Linyx on 2011-01-21
> **Alamantus said:**
> Ohhh, haha, duh. Sorry about that - didn't read far enough. 

Thanks a lot!

never mind...

you can mark thread-as-solved now...:p

---

### Post by Alamantus on 2011-01-21
Ok, so.... Suppose I can't get into Ubuntu because I already messed up the GRUB...
Would simply copying the entire partition and pasting it into the new install (replacing all the old folders) work the same way...?

---

### Post by Linyx on 2011-01-21
> **Alamantus said:**
> Ok, so.... Suppose I can't get into Ubuntu because I already messed up the GRUB...
Would simply copying the entire partition and pasting it into the new install (replacing all the old folders) work the same way...?

I think ,NO,

Grub repairing is very easy, you just has to Follow 2 Commands from Live-Session,Nothing More....

Edit:- Moreover if you want a Complete disk/Partition Image > [http://www.backuphowto.info/linux-backup-hard-disk-clone-dd](http://www.backuphowto.info/linux-backup-hard-disk-clone-dd)

---

### Post by Alamantus on 2011-01-21
> **Linyx said:**
> 
Grub repairing is very easy, you just has to Follow 2 Commands from Live-Session,Nothing More....


Oo, ok cool! What are the commands I have to do?

---

### Post by Linyx on 2011-01-21
> **Alamantus said:**
> Oo, ok cool! What are the commands I have to do?

It depends on your need...For example if you had installed windows after installing Ubuntu, so the Windows boot-loader will replace Grub from the MBR, so you won't see ubuntu anymore.. At this time you had to re-install Grub again or If you want to Use Windows Boot-loader instead of Grub, you can use a nice GUI tool for Adding entries and its Configuration via Easy-BCD > [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

If you are intrusted in Grub, check this out > [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

In the Above link follow the topic #13 [B][B][COLOR=Navy]Reinstalling GRUB 2 from the LiveCD
[/COLOR][/B][/B]

---

