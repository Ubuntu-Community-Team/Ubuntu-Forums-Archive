---
title: "mounting /home in NTFS partition"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by jbuczek on 2010-11-26
In my pursuit of making a dual boot XP and Ubu 10.10 machine play nice I'm wondering:

If I mount /home in a partition formatted as NTFS will Ubuntu eventually throw up?

Alternatively will XP eventually throw up if I redirect MY DOCUMENTS to a partition formatted as EXT2 or EXT3.

I want my documents to be in the same place under either boot.

Assume the I'm hoping to eventually be able to go 100% Linux.

TIA

---

### Post by drs305 on 2010-11-26
Your Ubuntu /home has to be on a linux filesystem so it can support permissions. This means that it cannot be installed on the Windows NTFS partition. 

Similarly, Windows wouldn't be able to natively read it's My Documents folder if it were on an ext2/3/4 filesystem.

What you can do is mount your Windows partition, then create a symlink to whatever Windows folder you want and put it on your Desktop or wherever. It would look and act like it was a folder in your Ubuntu installation.

For instance, let's say your windows name was drs305 and your Ubuntu name was ds305. In Ubuntu, you have mounted Windows on /media/windows. You could make a symlink to your Windows Desktop with the following command:
```

ln -s /media/windows/Documents\ and\ Settings/drs305/Desktop /home/ds305/Desktop/WindowsDesktop

```
Now it would appear that the folder WindowsDesktop, containing everything on your Desktop in Windows, is sitting on your Ubuntu Desktop. This is a pretty rough example; you could have your entire Windows folder sitting on your Desktop as a symlink, but you get the idea.

---

### Post by C.S.Cameron on 2010-11-27
Thanks Master Roaster:
I think I will bookmark this thread.

---

