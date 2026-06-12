---
title: "cant upgrade, says not enough disk space"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by insanity99 on 2010-06-01
i want to upgrade to ubintu 9.10 but it wont let me, after a few progress bars i get a message saying this 'The upgrade is now aborted. The upgrade needs a total of 3850M free space on disk '/'. Please free at least an additional 2469M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.'

here is what i get after typig df -h

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   11G  1.4G  90% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  224K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  144K  2.0G   1% /dev
tmpfs                 2.0G  120K  2.0G   1% /dev/shm
/dev/sda1             932G  821G  112G  89% /host
lrm                   2.0G  2.5M  2.0G   1% /lib/modules/2.6.28-15-generic/volatile


any idea why it is saying to do this?

thanks.

EDIT: oh and i am running through wubi.

---

### Post by MooPi on 2010-06-01
Your root partition looks small at only 13 gig with 90% in use. That is why you're out of space. You will need to increase the size of your partition or clear out dead weight on the partition(old useless files). Thanks for the edit. This link explains how to resize your wubi install.    [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

---

### Post by insanity99 on 2010-06-01
> **MooPi said:**
> Your root partition looks small at only 13 gig with 90% in use. That is why you're out of space. You will need to increase the size of your partition or clear out dead weight on the partition(old useless files). Thanks for the edit. This link explains how to resize your wubi install.    [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

ok so should i do this? 
> Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

Note that contrary to previous information, this script is not suitable for moving /usr - experienced users may be able to do this manually, at own risk, following a process similar to that outlined in the file. (Do not rename /usr until the very last moment, as rsync is installed there.)

is the size i type in the argument the new size i want the disk to be or how much i want to add to the size?

---

### Post by MooPi on 2010-06-01
If you want 15 gigs then 15000 approx. I would suggest a larger size due to your current status. This procedure moves the entire wubi install to a larger space so this is the final size and not an addition.

---

### Post by insanity99 on 2010-06-01
so since my current capacity is 224.6GB i should change it to about 250GB (256000mb)?

---

### Post by MooPi on 2010-06-01
That would consume your entire hard drive. Do you really want to do that ?

---

### Post by insanity99 on 2010-06-01
i dont know what to do, im confused to be honest. would it consume my HDD? i have a 1TB hard drive.

---

### Post by philinux on 2010-06-01
How much space do you think you will use for your wubi install?

---

### Post by MooPi on 2010-06-01
It would use the last remaing space available. I don't know your needs or how much you use Ubuntu but would suggest a smaller size. If your really interested in using Ubuntu on a regular basis then maybe you need a regular install instead of the virtual wubi install. Baby steps until your ready for the big jump is my suggestion.

---

### Post by insanity99 on 2010-06-01
so if i do that i want have space left on my hard drive for windows? i need space to install my software on windows, i use a lot of games and software for windows and need space to install more.

---

### Post by philinux on 2010-06-01
> **insanity99 said:**
> so if i do that i want have space left on my hard drive for windows? i need space to install my software on windows, i use a lot of games and software for windows and need space to install more.

Give wubi 50 gig for now.

---

### Post by insanity99 on 2010-06-01
but wont that cause a problem as i am using more space than that currently?

---

### Post by philinux on 2010-06-01
> **insanity99 said:**
> but wont that cause a problem as i am using more space than that currently?

Missed the 2 out meant 250.

---

### Post by insanity99 on 2010-06-01
ok, will this take a long time?

EDIT: i got this error message
'neil@ubuntu:~$ sudo sh wubi-add-virtual-disk /home 256000
Not enough free space (104733 MB < 256000 MB), aborting.'

---

### Post by philinux on 2010-06-01
> **insanity99 said:**
> ok, will this take a long time?

Too be honest I've seen a lot of borked windows installs mentioned on the forums due to wubi. Mainly due to unclean shutdowns. If you really like ubuntu I would do a proper dual boot install. 

I see wubi as a way to test out ubuntu before doing a proper install, not as a long term thing. Since the livecd is too sluggish for this purpose.

Backup, backup and backup which ever path you choose.

---

### Post by insanity99 on 2010-06-01
yeah i think i will do this, wanted to do it for a while now. i have never done partitioning though, the issue is i have an awful lot of stuff to backup, 2X1TB HDD's, both used at least 80%. to backup this would require lots of free space and a LOT of time right?

---

### Post by philinux on 2010-06-01
> **insanity99 said:**
> yeah i think i will do this, wanted to do it for a while now. i have never done partitioning though, the issue is i have an awful lot of stuff to backup, 2X1TB HDD's, both used at least 80%. to backup this would require lots of free space and a LOT of time right?

Yes but it's your important data. Hard drives do and will fail.

I only backup the important stuff. A bit of housekeeping first to get rid of unwanted stuff.

If you haven't see this have a good read.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by insanity99 on 2010-06-01
ok thanks for all the help, i am going to need to leave this for a day when i have a lot of free time on my hand.

thanks again for the help.

---

### Post by insanity99 on 2010-06-01
i decided to completely remove ubuntu and make a fresh install. it was a mess anyway, i booted windows and uninstalled ubuntu in add or remove but it hasn't seemed to free up the 230GB(odd) of space that the virtual drive was. is the virtual drive still there? if so where is it and how do i delete it?

---

### Post by insanity99 on 2010-06-01
can anyone help me with this?

---

