---
title: "Re-installed Ubuntu, how to get old files back?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by totalanonymity on 2011-03-07
I had created a separate /home partition for Ubuntu and when I re-installed I only deleted the 10 GB I had allotted for the OS and re-installed in the same spot and now I can't access my old files? What do I do?

I'm new to this. Completely. So, if your reply involves code and such, please do your best to explain very well for my novice self.

---

### Post by oldfred on 2011-03-07
If /home is a separate partition the easy was is as you install you specify that partition as /home but DO NOT format that partition as part of the install.

Other wise you have to mount your /home into fstab. You need to have used the same userid so the name is the same.

You only need to do the last few commands of any of the move /home to a new partition since you already have moved it.

Follow any one of these which every makes more sense to you, but they are essentially the same.
To move /home uses rsync  (create mount may be missinig)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Sometimes you get permission issues:
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

### Post by totalanonymity on 2011-03-07
I'm still rather confused. I'm supposed to move the partition around according to all those directions? I have a full hard drive, so...

---

### Post by oldfred on 2011-03-07
You should not have to move partitions around, just mount it using fstab.

If too confused, a new install may be quicker but not required.

---

### Post by grahammechanical on 2011-03-07
When you reinstall you give the partition where you want the OS to be the mount point of /

Then you tell the installation that you have a /home partition by selecting the partition as you did the / partition and you give it the mount point of /home and do not tick format.

Then in Places the Home Folder will be the /home partition where all your files are. It works. I know. You did not tell the installer that you already had a /home partition. It created a new Home Folder on the / partition.

None the less that missing partition should be visible in the panel on the left when you go to Places>Home Folder. You can access those files. Unless you are not telling us everything we need to know.

Regards.

---

### Post by totalanonymity on 2011-03-07
I, yet again, ruined something by attempting to try every method to change the Plymouth splash screen in 10.10 and GRUB disappeared and I couldn't understand many instructions and tried my best and then GRUB rescue came about, and now I'm just doing a clean install, and no more messing with Plymouth (second time in 24 hours it removed GRUB for me).

Learned my lesson! But hey, isn't that what Linux is all about? :)

---

