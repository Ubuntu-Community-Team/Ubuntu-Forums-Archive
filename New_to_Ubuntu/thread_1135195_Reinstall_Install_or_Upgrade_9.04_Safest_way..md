---
title: "Reinstall Install or Upgrade 9.04? Safest way."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by whiteman on 2009-04-24
A while back my windows computer refused to let me reinstall. So I made the jump to Total Ubuntu, my 8.10 disk worked great. I now have a network with my Macbook(wireless) and Ubuntu 8.10 and my wifes vista. everbody sees each other, Cups works great. We can all print, share etc. BUT NOW I want the new OS.9.04. How can I install it without losing all of my hard work. Right now everything works good, except I could hope for my webcam to work, and wine is a little drunk.(had to get rid of it)
What is the safest way to do this??????????
Is there a way to just upgrade?Sort of cherrypick?I see somepeople have lost "root term" I dont wanna lose this.

---

### Post by tom56 on 2009-04-24
The safest way if you want to keep all your old files and settings is to open Update Manager, install any available updates, restart and then click the Upgrade button.

---

### Post by por100pre1 on 2009-04-24
Any way can be good, but theres no 100% error proof method. Backup your /home folder to an external hard disk drive or other removable media before upgrading or reinstalling. I upgraded using Update Manager, no problems here. Just don't upgrade this weekend, there are many users doing the same. Wait at least till next week.

---

### Post by El Zoido on 2009-04-24
Whichever method you use, you should first make a backup of your Home-directory.

I used to upgrade my system and except for one time it did always work flawlessly.
Nowadays I'm mostly using a reinstall, as I feel that it's giving me a "cleaner" system, but of course I have to reconfigure everything afterwards.

If you are upgrading you might consider waiting a couple of days, so the servers aren't stressed anymore, could be a lot faster.

---

### Post by XubuRoxMySox on 2009-04-24
I think I know what to do, have a pretty good idea. I'm gonna back up my /home directory (including the hidden stuff) onto a CD *before I start*. Then I'll load the new live CD in, and when it gets to the partition stuff, I'll select Manual Partitioning, select the CURRENT /home partition to be the NEW /home partition and make sure it does NOT get formatted.

If it does get formatted accidentally, I still have my backup... but I DO have a question about the new file system. How do I know if I should "convert" to Ext 4, AND if I do, will my UNFORMATTED /home directory  still be usable by Jaunty?

Thanks,
Robin

---

### Post by AndyCooll on 2009-04-24
> **dixiedancer said:**
> I think I know what to do, have a pretty good idea. I'm gonna back up my /home directory (including the hidden stuff) onto a CD *before I start*. Then I'll load the new live CD in, and when it gets to the partition stuff, I'll select Manual Partitioning, select the CURRENT /home partition to be the NEW /home partition and make sure it does NOT get formatted
Of course you can only select to re-use your current /home directory if you created separate / and /home partitions when you did your last install. By default however, Ubuntu puts everything on one partition.

If you didn't do this last time then when you manually partition this time, create a separate / and /home partition. Then when the install is complete copy over the settings file from your backup CD.

:cool:

---

### Post by El Zoido on 2009-04-24
You can always convert ext3 to ext4 (but not the other way round).

For now however I would keep /home as ext3, though.

There seems to be a higher possibility for data loss on ext4 in case of a system crash.
As far as I can tell, we probably have to wait until the developers start adapting their software to ext4 until we can be safe.

---

### Post by Dileeshvar on 2009-04-24
The best way I suggest is to go for fresh installation
after you back up your /home dir and we have ext4 in jaunty 
so you can go for a whole new installation I guess

---

