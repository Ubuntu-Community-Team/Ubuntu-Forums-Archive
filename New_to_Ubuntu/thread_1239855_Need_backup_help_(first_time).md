---
title: "Need backup help (first time)"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-14
Getting ready to make a backup of the OS. I need to know the best way to do this and which files/directories to backup. Partitions are  / , /home, /data. I plan to put the backup in /data for safe keeping.

---

### Post by s3a on 2009-08-14
You should look into backintime.

[http://backintime.le-web.org/](http://backintime.le-web.org/)

That's good for the important data. As for configuration files, if you ruin your installation, just re-install and mount your home partition without reformatting it and everything will be the way it was.

---

### Post by starcraft.man on 2009-08-14
> **chris1950 said:**
> Getting ready to make a backup of the OS. I need to know the best way to do this and which files/directories to backup. Partitions are  / , /home, /data. I plan to put the backup in /data for safe keeping.

There isn't a best way, there are many ways to get to where ya want to go though. See: [BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem") Good wiki page, I should know, edited it myself :). Read the intro and then pick the method that suits you.

---

### Post by chris1950 on 2009-08-14
3Sa

I tried that before and got two OS's installed each in a different partition.

---

### Post by chris1950 on 2009-08-14
Thnx  Now I need to decide between grsync and sbackup. Will install both and try each then make decision.

---

### Post by rossmoore on 2009-08-14
Ooh, backintime looks good. I looked at TimeVault, but it never quite worked for me. I ended up using a bash script that called rsync and used hard links - which is exactly what backintime seems to do, only in a friendlier way. I'll be checking that out shortly, I think.

---

### Post by mapes12 on 2009-08-14
> That's good for the important data. As for configuration files, if you ruin your installation, just re-install and mount your home partition without reformatting it and everything will be the way it was.Exactly! The only problem I have found though is that you're then faced with a tonne if updates to download. To get round this I use two methods as belt and braces so to speak:

1. I keep a regular partition image of "/". I use a live PING cd to do this and store the image on a separate HDD. There's great tutorial on YouTube for using PING. If i mess up my system I simply reinstall my backup image to my "/" partition. Grub and everything is preserved. The machine boots into Ubu first time and no/very little updates to download again.

2. I wrap up the main components of "/" in a simple tar file. The CL for me is: ```
sudo tar cvpzf /HDD2/Filesystem/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media  --exclude=/mnt --exclude=/sys /
```It looks complicated but all I do is cut and paste this into Terminal. Hit enter and watch the sparks fly. The first two excludes are so that we don't make a second backup of /home and we don't want to backup the second hard drive where we are making the backup to. There are reasons why other directories are not backed up which I spent ages researching. And it works. If I mess up my system and option 1. above doesn't work (which it hasn't as yet) I just reinstall Ubu from my original installation cd making sure no other partitons are formatted except "/" then move my tar file into "/" then unpack it like this:```
sudo su
``` ```
tar xvpfz bkp-root.tgz -C /
```Ubu is then all back as it was inc all the updates I've downloaded.

I also keep backups of /home using GRSYNC onto another HDD. If you use GRSYNC then I found it best to give it root permission. You can do this by right click applications>edit menu then select Grsync>Properties and in the command box enter "gksu" before grsync. It will then launch with sudo permission. Also, when backing up home beware the deadly .gvfs hidden file. It causes havoc with reinstalls. Fortunately, Grsync seems to ignore it because it's a virtual file but to be sure I put an exclude (--.gvfs) in Grsync to avoid it.

As another poster commented there are many ways to backup and my head was swimming. So I setup a test machine to try things out. The above options came out best for me. I know others will have other solutions but I hope that the above may be of some use.

---

### Post by Mark Phelps on 2009-08-14
+1 for PING -- use it all the time.  And, if you read their Appendix, you will find that you can install the PING loader to your Ubuntu partition, and using GRUB, can then select that to run -- eliminating the need to boot from CD.

It's really a backup/restore utility.  It's similar to GHost but it doesn't allow for browsing a saved image, and it's not intended to be used to clone installations or drives for moving to a new drive or machine.  But for simply backing up and restoring an existing installation, it works just great!

I've found it invaluable whenever I decide to experiment with my Ubuntu install.  Do a backup (takes 15 minutes at most). Mess around.  If the system is then hosed, reboot to GRUB, select PING, select the latest backup, do the restore -- and 15 minutes later I'm back to where I was before the backup.  

Can't get much simpler than that.

---

### Post by mapes12 on 2009-08-14
> if you read their Appendix, you will find that you can install the PING loader to your Ubuntu partition, and using GRUB, can then select that to run -- eliminating the need to boot from CD.
Hi Mark

I've read through the PING info on their site but I'm struggling to find out how to do this please?

Any pointers?

Best....

Mark

---

### Post by LewRockwell on 2009-08-14
We use Clonezilla because it's a stand-alone utility that works with whatever

.

---

### Post by HermanAB on 2009-08-14
Howdy,

Note that since it is usually very easy to re-install Ubuntu, backing up the whole OS is rather pointless.  It should be sufficient to just backup your data which should all be in /home and forget about the rest.

---

