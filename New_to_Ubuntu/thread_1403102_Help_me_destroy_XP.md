---
title: "Help me destroy XP"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Laeluu on 2010-02-09
Originally, I was dual-wielding (as I like to oh-so-eloquently call it) Windows XP Corporate and Ubuntu...XP for Photoshop and iTunes.

Recently, I have achieved epic-win on my part--I have my ipod working perfectly, and have a working copy of CS4 running on wine.

Dear Ubuntuforums, how do I destroy XP off my computer? I have a partition with about 50gb for ubuntu, 150 for windows (I kept my music on windows), but I don't really care about anything on windows if it's deleted--I have all my music backed up, as well as important files, etc.

Thanks so much! (:

---

### Post by kidux on 2010-02-09
Use GParted to delete the partition and add it as an Ubuntu one, maybe extending /home.

---

### Post by Laeluu on 2010-02-09
I kind of figured, but I don't really know how to *GET* to gparted. I tried doing a search for the file name, but that didn't work, and it's not in any of my normal folders or whatnot.

---

### Post by Dayofswords on 2010-02-09
> **Laeluu said:**
> Originally, I was dual-wielding (as I like to oh-so-eloquently call it) Windows XP Corporate
Windows XP Corporate?

after a quick google, landing at a microsoft.com forum post:
[http://social.microsoft.com/forums/en-US/genuinewindowsxp/thread/e13cff04-a5f2-4f9a-b6b1-557745e29247/](http://social.microsoft.com/forums/en-US/genuinewindowsxp/thread/e13cff04-a5f2-4f9a-b6b1-557745e29247/)
> 
Your statement: "There is a computer shop here in town that might install a genuine fresh copy of XP Corporate for $50.00" is not true. There is no such thing as a "XP Corporate" available for $50.00...its just another non-genuine, bogus offer.

Hope you find your original Gateway reinstallation CD so you can become "genuine"!

---

### Post by louieb on 2010-02-09
Don't even think I would delete the windows partition. Just use Gparted and format it with the ext3 or ext4 file-system. Use it for a data partition.  Put your music and whatever back on it. 

That way - if you have reinstall Ubuntu - your data is out of the way.

run gparted from a live CD - its under System>administration>Partition editor

or install it```
 sudo apt-get install gparted
```

---

### Post by Cheezespread on 2010-02-09
You can find gparted in System -> Administration I believe. Else you can open up a terminal and try ```
sudo gparted
```. You are with root privilages now. So be a bit careful.

If the above command gives you any error , do let us know.

---

### Post by Laeluu on 2010-02-09
I got gparted working and I successfully deleted XP, but I really would like to just have one partition on my computer, mainly because whenever I was accessing other partitions it was going slower, plus I had to enter my password and mount it each time I wanted to listen to music, etc.

I read something else and it says that I have to unmount my device before extending the partition; how would even go about that?

---

### Post by TheViLliN on 2010-02-09
I agree.  Just remove the partition using GParted perhaps. Extend it to your current partition or use it for a new storage partition. You should use the live boot cd and gparted to "extend" the partition so your main boot partition is unmounted. 

You might have to add the program depending on you version of ubuntu.

```
sudo apt-get install gparted
``` 

After edit your GRUB boot menu to remove the entry for Windowz.

```
sudo nano /boot/grub/menu.lst 
```

---

### Post by kidux on 2010-02-09
> **Dayofswords said:**
> Windows XP Corporate?

after a quick google, landing at a microsoft.com forum post:
[http://social.microsoft.com/forums/en-US/genuinewindowsxp/thread/e13cff04-a5f2-4f9a-b6b1-557745e29247/](http://social.microsoft.com/forums/en-US/genuinewindowsxp/thread/e13cff04-a5f2-4f9a-b6b1-557745e29247/)

Corporate is simply XP Pro with a multi-machine CD key, nothing more.

---

### Post by barkej on 2010-02-09
> **Laeluu said:**
> I got gparted working and I successfully deleted XP, but I really would like to just have one partition on my computer, mainly because whenever I was accessing other partitions it was going slower, plus I had to enter my password and mount it each time I wanted to listen to music, etc.

I read something else and it says that I have to unmount my device before extending the partition; how would even go about that?
Woohoo! Kick XP to the curb. LOL.

You might try running System > Administration > Disk Utility as a means of removing the partition.

---

### Post by Merk42 on 2010-02-09
Run Gparted from the LiveCD.

When you boot using the LiveCD, your partitions aren't mounted so you can make those adjustments.

---

### Post by barkej on 2010-02-09
> **kidux said:**
> Corporate is simply XP Pro with a multi-machine CD key, nothing more.

Exactly. Many large companies use Corporate XP legally. Unfortunately many computer shops sell bootleg copies of it as originals.

---

### Post by Laeluu on 2010-02-14
Every thing is done! (:

This is getting a bit more picky--and it's no big deal if it's not solved--but the option to run XP on my startup screen is still there. When I try to run it, nothing happens (obviously). Suggestions on how to make it go away?

---

### Post by perce on 2010-02-14
> **Laeluu said:**
> Every thing is done! (:

This is getting a bit more picky--and it's no big deal if it's not solved--but the option to run XP on my startup screen is still there. When I try to run it, nothing happens (obviously). Suoggestions on how to make it go away?

According to [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")you can run 
```
sudo update-grub
```

---

### Post by running_rabbit07 on 2010-02-14
> **Laeluu said:**
> Every thing is done! (:

This is getting a bit more picky--and it's no big deal if it's not solved--but the option to run XP on my startup screen is still there. When I try to run it, nothing happens (obviously). Suggestions on how to make it go away?

If you are using Karmic ```
sudo update-grub
```

Hardy, Intrepid and Jaunty ```
gksu /boot/grub/menu.list
``` skim down the list and find the entry for the Windows XP chainloader and delete it.

---

### Post by Laeluu on 2010-02-17
It's not on the list, but it keeps showing up anyways? This is what I get:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

(Thought I posted this already, sorry.)

---

