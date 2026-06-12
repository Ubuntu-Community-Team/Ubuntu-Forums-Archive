---
title: "Need to create backup image"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Supa Fly on 2008-12-20
Hi everyone

I'm running 32bit 8.04 and I would like to make a backup image of my installation so that if I break the system I don't lose the 300mb of updates i just downloaded.

Does anyone have any suggestions for an application I can use to do this?

I have very little experience with Linux so GUI programs would be better.

Thanx

---

### Post by drs305 on 2008-12-20
I like partimage, although it may require a bit more typing than you are looking for and takes a few tries to get comfortable with. It makes an image of the entire partition but doesn't include empty space. You can also compress the image. Since it is an image, you can't retrieve specific files from the backup - it's all or nothing.  I've used it many times to restore my system to a previously-working state and it has always done the job.

Here is a good guide to using it:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by Duck2006 on 2008-12-20
> **drs305 said:**
> i like partimage, although it may require a bit more typing than you are looking for and takes a few tries to get comfortable with. It makes an image of the entire partition but doesn't include empty space. You can also compress the image. Since it is an image, you can't retrieve specific files from the backup - it's all or nothing.  I've used it many times to restore my system to a previously-working state and it has always done the job.

Here is a good guide to using it:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

+1

---

### Post by hyper_ch on 2008-12-20
simplest thing would be a second harddrive

then boot the live cd and make a 1:1 copy with dd.

---

### Post by ahood on 2008-12-20
There is also clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by BDNiner on 2008-12-20
I have had success with Acronis True Image with previous versions of Ubuntu. It lets you create a rescue partition that you can restore the OS from. But it doesn't play nice with Grub for some reason now. The last PC i tried it on, it kept trying to mount the image instead of restore it so i gave up.

Clonezilla is my fav since then.

I wonder if there is a way to create an install CD with all the updates until lets say today?

---

### Post by Supa Fly on 2008-12-20
I've taken a look at both clonezilla and partimage and I have 1 question.

I only have one harddrive and a DVD-writer.  Is it possible, with this setup, to create a backup to a DVD or do I have to use another partition?  I ask this because (in the case of clonezilla) it says clonezilla runs as a liveCD.  If it runs like that, how would I use the backup image (that I would like to create on a DVD)?

The drive is rather small so I would prefer to avoid using another partition if I could.

---

### Post by MyR on 2008-12-20
I have also been looking for an app that makes an image of the entire hdd without the need for a live cd. True Images does this on windows. Does anything like this exist for linux?

---

### Post by Duck2006 on 2008-12-20
> **Supa Fly said:**
> I've taken a look at both clonezilla and partimage and I have 1 question.

I only have one harddrive and a DVD-writer.  Is it possible, with this setup, to create a backup to a DVD or do I have to use another partition?  I ask this because (in the case of clonezilla) it says clonezilla runs as a liveCD.  If it runs like that, how would I use the backup image (that I would like to create on a DVD)?

The drive is rather small so I would prefer to avoid using another partition if I could.

Why not boot from a usb flash drive and that leaves your DVD to sent the image to, or boot from the DVD and send the image to a usb flash drive.

---

### Post by mapes12 on 2008-12-20
> I'm running 32bit 8.04 and I would like to make a backup image of my installation so that if I break the system I don't lose the 300mb of updates i just downloaded.
The easy way IMHO without requiring image software:

**METHOD 1 - USING APTONCD**

1. Have /home [on its own partition]("http://ubuntuforums.org/showthread.php?t=46866")
2. Install aptoncd - search for it in Synaptic.
3. Create an iso file of all your downloaded packages and updates using aptoncd
4. Keep it safe somewhere e.g. in your new /home partition

SYSTEM CRASH!!

1. Reinstall your version of Ubuntu from the original installation CD.
2. CARE! When you get to the Partitioning screen DON'T use the default "Guided - Use Entire Disk". Select "Manual" and for each partition highlight it then tell the installer where to install each part of the installation i.e. which partition to use for "/",  /home and Swap. Select the option to format all other partitions EXCEPT /home.

When your done reinstalling Ubu then reinstall aptoncd from Synaptic. Run it then select the "Restore" option.

Then, if reinstalling the aptoncd packages from a CD or DVD simply change the Synaptic "Origin" button to that media selection. If reinstalling the aptoncd packages from the iso file they will be installed back in your "var" directory but you will need to run this to install them: ```
sudo -i /var/cache/apt/archives/*.deb
``` This works in 8.04 but I can't guarantee the same result with any other version.

[B]
METHOD 2 - USING A TAR FILE[/B]

As in Method 1 we have /home on a separate partition which we will also backup as below.

I have a second HDD on my system but you should be able to adapt this to any media storage.

Backup Routine:

Terminal -
> sudo mkdir /HDD2
# creates a folder in the filesystem called HDD2

> sudo mount /dev/sdb1 /HDD2
# mounts the 2nd HDD Linux partition to the file system via the above directory

Backup /home - (and creates sub directories Backup and Home, just to keep the backups separate but you can have whatever path you like within HDD2) 
> sudo tar cvpzf /HDD2/Backup/Home/bkp-home.tgz /home

Backup /(root) -
> sudo tar cvpzf /HDD2/Backup/System/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media  --exclude=/mnt --exclude=/sys /
# The first two excludes are so that we don't make a second backup of /home and we don't want to backup the second hard drive where we are making the backup to for obvious reasons. The rest of the excludes are either virtual directories or will be reconfigured by the Ubu reinstall in the first place - see below.

SYSTEM DAMAGE!!!!

Reinstall Ubuntu

Then:-

Restore -
Terminal -
> sudo mv /HDD2/Backup/Home/bkp-home.tgz /
> sudo mv /HDD2/Backup/System/bkp-root.tgz /
# The above will move the tarfiles from the second HDD back into the root file system

Then move yourself into "/" like this: > sudo su > cd /Then unpack the tar files:
> tar xvpfz bkp-root.tgz -C /
> tar xvpfz bkp-home.tgz -C /

Restart the PC.

Voila! Up and running again.

N.B. Form more info on the switches in the tar command run > man tar in Terminal

---

### Post by Dedoimedo on 2008-12-20
A few names that come up to mind:

PartImage and CloneZilla as mentioned. Got a tutorial if you like...

But the simplest: Remastersys.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

See me tutorial: Remastersys - Create custom Ubuntu (live) CD - Tutorial
[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

Cheers,
Dedoimedo

---

### Post by Supa Fly on 2008-12-21
Thanx mapes12 APTONCD looks like it will do what I'am looking for. Would like to know is it possible to put my information on a DVD or flash stick instead of keeping it on a /home partition with APTONCD?

---

