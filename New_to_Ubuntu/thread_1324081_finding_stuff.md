---
title: "finding stuff"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by wordmaster on 2009-11-12
Hi Y'all,

I have a dual boot machine with win2k and Ubuntu. In Ubuntu, if I go to "places" I can access all the drives on the computer, the windoze drive, the windoze data drive, the linux drive, the crossover drive, etc.

However, if I open a program, for instance Open Office Calc, and go to file and open, I can only see and access the linux drives. IF I am trying to open a calc file that is on the windoze drive, I cannot find it.

Am I just not looking in the right place? Can it just not be done? Is there a work around? Any help appreciated.

---

### Post by philinux on 2009-11-12
> **wordmaster said:**
> Hi Y'all,

I have a dual boot machine with win2k and Ubuntu. In Ubuntu, if I go to "places" I can access all the drives on the computer, the windoze drive, the windoze data drive, the linux drive, the crossover drive, etc.

However, if I open a program, for instance Open Office Calc, and go to file and open, I can only see and access the linux drives. IF I am trying to open a calc file that is on the windoze drive, I cannot find it.

Am I just not looking in the right place? Can it just not be done? Is there a work around? Any help appreciated.

Open the drive you want to work from first.

Option then is as you work above. Other is find file right click open with.

---

### Post by oldos2er on 2009-11-12
> **wordmaster said:**
> I have a dual boot machine with win2k and Ubuntu. In Ubuntu, if I go to "places" I can access all the drives on the computer, the windoze drive, the windoze data drive, the linux drive, the crossover drive, etc.

However, if I open a program, for instance Open Office Calc, and go to file and open, I can only see and access the linux drives. IF I am trying to open a calc file that is on the windoze drive, I cannot find it.

Am I just not looking in the right place? Can it just not be done? Is there a work around? Any help appreciated.

 Partitions need to be mounted before you can access their files. As Philinux said, you can click on them in the Places menu, which should mount them. If you want them mounted on system startup, you need to add them to /etc/fstab. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by sisco311 on 2009-11-12
You can use ntfs-config (GUI application) to permanently mount the partition. 

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by gdonwallace on 2009-11-12
In the duel boot with windows, the windows "share" (as that is how Ubuntu sees it, but not as a real share) will be mounted under either /mnt or /media

I would look in /mnt first.  Don't remember which one it is, but one of them should show you all your windows files.

---

### Post by wordmaster on 2009-11-15
Opening the drive I want to access first works great. Thank you!

---

