---
title: "how much space needed to partition for system files?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-07
I am having issues with the upgrade from 10.4 to 10.10

I have 10.24 GB allocated for system files /

and I opened gparted it says 9.34 is used.  

There isnt anything fancy or bloated files in here.  It just has clean 10.04 ubuntu desktop installed, and gpart.  Thats it.

During upgrade from 10.4 to 10.10. It says it is out of disk space :confused:

from [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
If you choose to create a separate /home partition, allocate between 5 and 10 GB for the / partition—that's about all you'll need for the Ubuntu system and programs. The rest should be for your personal files (in /home). 

what is the recommend hard drive size for system files?

I have around 105.23 available on /home drive.  How can I allocate more space to system files section /

thank you

---

### Post by papibe on 2011-08-07
Interesting. There are requirements for a new installation, but not for a [distro upgrade]("https://help.ubuntu.com/community/LucidUpgrades").

I would recommend booting using the Ubuntu Live CD (includes GParted). Then using GParted:
[LIST]
[*]Shrink your /home partition.
[*]Move the shriked partition to the left (end of the disk).
[*]Increase the / partition using the adjacent freed space left by /home.
[/LIST]
It would be a good idea to backup your important files before attempting this.

I hope it helps.

---

### Post by oldfred on 2011-08-07
I have /home inside my / and have used about 7GB, almost all my data is elsewhere.

You must have added something as normally without any additions your install is a little over 4GB.

You can do some housekeeping:
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

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by 007casper on 2011-08-08
thank you so much for all your help.

@oldfred - awesomeness!

---

