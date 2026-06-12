---
title: "Boot Mounting Problem"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-22
I tried to google for the solution, but all I keep finding are tutorials on how to mount, not what I'm looking for.  I hope that there is a simple solution to what surely others must be experiencing.... I have this problem on 2 machines now, and frankly am now motivated (because of my wife) to fix it.

The problem:

I have multiple disk partitions.  Previously I had ubuntu automatically mount some drives that have since been changed.  I installed something else in the drive 
([SIZE="2"]((Reason = Doing a windows install broke my grub, and the only way I could fix it was to install another ubuntu, unused, in another partition, to fix grub - yeah, I'm sure there was a better solution, but grub2 confuses me.))[/SIZE])

Now when I boot ubuntu it says that the drive is not available, and I have to press "S" to skip it to continue booting.

How do I either fix the mount point, or eliminate it?

Thank you.

---

### Post by yankysunny on 2010-11-22
So this is wht u done?
Ubuntu[one partition] -> Windows[separate partition] -> Ubuntu [separate partition]
So which Os u r booting into now?

---

### Post by jacob.david on 2010-11-22
After booting into Ubuntu open a command prompt and type the following
sudo update-grub
This will probe all OSes and modify the menu accordingly. Restarting after that should work fine with all the OSes listed in the grub menu.
If that doesn't fix the issue.Paste the contents of the files under the folder /etc/grub.d and tell us how many partitions you have and which OS you have installed in each of them.

---

### Post by luckylucky on 2010-11-22
Funny... I actually almost feel ashamed to admit to having installed windows again on my machines.  I've been window-less for years.  The only reason I got them back was because of Netflix.  Damn DRM.  Gotta have winblows again.  You wouldn't believe the hassles I've had reinstalling winblows... but that's another story.

Yeah, basically like what you said.  Years ago I got into the habit of creating a few smaller partitions, usually left blank, to be able to install and play around with new linux flavors/distros.  By having a partition or two free I can play and/or upgrade (every 6 months) without disturbing my main productivity machine.  In the end I would highly recommending this practice for all of you reading this.

Anyhow, so I installed windoze into a partition, broke grub, banged head until bright idea surfaced to just install another ubuntu into another partition, which basically fixes grub.

But now the problem I am left with is that every time I boot (into my daily used ubuntu) it nags me that it doesn't like a drive since it is not what it expected.  I have to hit "S" each time to bypass it & continue booting.

So yup, Windows & Ubuntu & Ubuntu & storage (just a big ext4 partition for storing stuff)

---

### Post by yankysunny on 2010-11-22
So which partition does it says that it is not available ?

---

### Post by oldfred on 2010-11-23
Post this and we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.


All you had to do is reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

