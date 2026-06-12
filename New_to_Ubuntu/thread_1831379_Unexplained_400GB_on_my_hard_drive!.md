---
title: "Unexplained 400GB on my hard drive!"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by chrisp3047 on 2011-08-23
Hi there,

I ran disk usage analyser on Ubunutu 11.04, and it told me that I have used 838GB and have available 69GB.

But when I click 'scan filesystem' it says the size of the entire filesystem is 404GB. This accounts for all my 'known' data on the drive.

Could someone explain how I can find out what is using up the rest of my hard drive?

There is over 400gb that I don't understand what it is! I've looked at the recycle bin and cache, and these are small amounts. I'm starting to get worried that it's a virus??? Or a problem with my hard-drive?

Thanks to anyone who can help.

---

### Post by apacketofsweets on 2011-08-23
Highly unlikely it's a virus, 99% of Linux virus (of which themselves are incredibly rare) are aimed at servers, so my guess is the communication between the hard drive and Ubuntu or the software you're using has gone a bit haywire.

---

### Post by Azdour on 2011-08-23
Hi,

Have you read the replies on your original closed thread:

[http://ubuntuforums.org/showthread.php?p=11162922](http://ubuntuforums.org/showthread.php?p=11162922)

There's a few posts requesting you to do things to try and help us identify your issue.

As a side note to the moderators :) This does not seem to be a duplicate since [http://ubuntuforums.org/showthread.php?t=1827006](http://ubuntuforums.org/showthread.php?t=1827006) is closed which is why I'm guessing the OP has created a new thread...

---

### Post by oldfred on 2011-08-23
I find because I link in other partitions into /home that some tools include the totals of the linked in partitions.

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

---

### Post by mcduck on 2011-08-23
Isn't this already third duplicate thread? I've already answered this question in one thread, which then got locked as a duplicate: [http://ubuntuforums.org/showthread.php?t=1831279]("http://ubuntuforums.org/showthread.php?t=1831279")

Anyway, the short answer is that the Disc Usage Analyzer doesn't by default scan a single partition, but the whole filesystem with all mounted partitions, remote locations etc. It's not really intended for checking used/available space on a certain partition but instead for analyzing the disc usage of your files & directories relative to whatever partition or directory you tell it to scan.

Also the DUA has a know bug that it also counts virtual filesystems, so if you use encrypted home directory it will count both the actual encrypted files that are on the hard drive and the unencrypted ones that really only exist in the memory.

---

### Post by Azdour on 2011-08-23
Hi,

I believe this is the only thread that is alive, the other two have been closed...

---

