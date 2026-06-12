---
title: "messed up my installation, what to do?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by veelivar on 2008-12-23
I have been fllowign this -> [http://ubuntuforums.org/showthread.php?t=268985&highlight=torrentflux](http://ubuntuforums.org/showthread.php?t=268985&highlight=torrentflux)

and I forgot the password I set for torrentflux, so I uninstalled torrect flux to try again this time it is behaving differently wand not setting up the database as it did the first time and aptitude is showing errors when I try and remove install etc.  I have tried this a few times now.

Short of compleatly re-installing ubuntu again is there anything I can do to clean up my installation? and then start again?  I thought aptidude would manage it but it is not really doing it.

It is a general problem I have run into before and I hate having to re-install the whole os cos I messed one thing up.  Especially as I get my box closer to what I want and have more stuff on it.

Cheers,

---

### Post by echo314 on 2008-12-23
If you could provide the error from console output that would be helpful in diagnosing the problem, it may be a simple as reconfiguring dpkg. 

During the partitioning phase of installation, instead of using one partition for the entire partition, set an 8gig one for /, and then set a larger one for /home. This way, all your personal data and info is located on a partition other then the OS, and you can reinstall the OS without fear of changing data.

---

### Post by mapes12 on 2008-12-23
You will need to provide more specific details about your problem. For future System screw ups you may find the following will get you back up and running quickly:

**METHOD 1 - USING APTONCD**

1. Have /home on its [own partition]("http://www.psychocats.net/ubuntu/separatehome")
2. Install aptoncd - search for it in Synaptic.
3. Create an iso file of all your downloaded packages and updates using aptoncd
4. Keep it safe somewhere e.g. in your new /home partition

SYSTEM CRASH!!

1. Reinstall your version of Ubuntu from the original installation CD.
2. CARE! When you get to the Partitioning screen DON'T use the default "Guided - Use Entire Disk". Select "Manual" and for each partition highlight it then tell the installer where to install each part of the installation i.e. which partition to use for "/", /home and Swap. Select the option to format all other partitions EXCEPT /home.

When your done reinstalling Ubu then reinstall aptoncd from Synaptic. Run it then select the "Restore" option.

Then, if reinstalling the aptoncd packages from a CD or DVD simply change the Synaptic "Origin" button to that media selection. If reinstalling the aptoncd packages from the iso file they will be installed back in your "var" directory but you will need to run this to install them:

```
sudo -i /var/cache/apt/archives/*.deb
```
N.B. The above command works in 8.04 but I haven't tried it in other versions.


**METHOD 2 - USING A TAR FILE**

As in Method 1 we have /home on a separate partition which we will also backup as below.

I have a second HDD on my system but you should be able to adapt this to any media storage.

Backup Routine:

Terminal -
```
sudo mkdir /HDD2
```
# creates a folder in the filesystem called HDD2

```
sudo mount /dev/sdb1 /HDD2
```
# mounts the 2nd HDD Linux partition to the file system via the above directory

Backup /home - (and creates sub directories Backup and Home, just to keep the backups separate but you can have whatever path you like within HDD2)
```
sudo tar cvpzf /HDD2/Backup/Home/bkp-home.tgz /home
```
Backup /(root) -
```
sudo tar cvpzf /HDD2/Backup/System/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
```
# The first two excludes are so that we don't make a second backup of /home and we don't want to backup the second hard drive where we are making the backup to for obvious reasons. The rest of the excludes are either virtual directories or will be reconfigured by the Ubu reinstall in the first place - see below.

SYSTEM DAMAGE!!!!

Reinstall Ubuntu from original CD. Again at the Partitioning stage use "Manual" as in Method 1 above. Then restore your system as follows:

Restore routine -

Terminal -
```
sudo mv /HDD2/Backup/Home/bkp-home.tgz /
```
```
sudo mv /HDD2/Backup/System/bkp-root.tgz /
```
# The above will move the tarfiles from the second HDD back into the root file system

Then move yourself into "/" like this:
```
sudo su
```
```
cd /
```
Then unpack the tar files:
```
tar xvpfz bkp-root.tgz -C /
```
```
tar xvpfz bkp-home.tgz -C /
```
Restart the PC.

Voila! Up and running again.

N.B. For more info on the switches in the tar command run```
man tar
```
in Terminal

---

### Post by veelivar on 2008-12-23
Thanks for the info I'll have a play and make sure I get used to what I am doing a bit then go for a better set up.

As to this problem.  I uninstalled again and purged as well.  I noticed that soem of the old config in /etc/torrentflux had not been removed for I did it manually.  Then I cleaned aptitude.  Then I reinstallaed torrent flux with:

sudo aptitude install torrent flux

During this installation it failed to restart apache with this error:

apache2: Syntax error on line 278 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/torrentflux.conf: No such file or directory
   ...fail!

---

### Post by veelivar on 2008-12-23
ok it seems that the first tiem I installed torrentflux it created config files in /etc/torentflux/ one of which was an apache config file.

That file is no longer being created, it seems very weird.

---

