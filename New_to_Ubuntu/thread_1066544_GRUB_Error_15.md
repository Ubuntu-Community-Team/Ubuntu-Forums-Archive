---
title: "GRUB Error 15"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by chaosTechnician on 2009-02-11
So, I'm an idiot, and realized it just a little bit too late. :)

I used GParted (from System Rescue CD) to set up partitions to install Ubuntu as a secondary OS on my laptop (primary is WinXP).
I installed Ubuntu (mounted the .iso using Daemon-tools in Windows) but didn't have a swap partition set up so I decided to boot back up System Rescue, use GParted, rearrange the partitions (including deallocating where Ubuntu was installed), and tried to boot back into Windows to start the Ubuntu installation again.  (Bad idea, I know--as soon as it didn't work, I understood what I did...)
When I boot, I now get the following error right away:
> GRUB Loading stage1.5
GRUB loading, please wait...
Error 15

While I'm (sometimes) somewhat computer savvy, I'm very new to the whole Linux thing, so I'm stuck.  Is there a way to either remove GRUB or otherwise let me back into Windows to I can get it and Ubuntu back (and have my computer turn on normally)?

If it helps:
/dev/sda1 (NTFS) is where Windows is installed
/dev/sda2 (FAT32) is a HP_Recovery partition (since apparently distributing laptops with actual software CDs isn't standard anymore)
/dev/sda3 (EXT2) is where I'd like to put Ubuntu
Then there's a little unallocated for a swap partition

I do have a Desktop, if I just need to redownload the .iso and actually burn it, but my Internet connection at home sucks so I'm trying to avoid what could become an 10+ hour download.

Thanks,
Feeling Stupid. :)

---

### Post by utnubuuser on 2009-02-11
Hi - Can't help you with the loop-mounting, but insofar as installing Ubuntu on /dev/sda3....

Are you better off removing that partition, thereby creating unused space and when, (or if in your case), you install from the CD, simply selecting "guided - use largest continuous free space?
As far as I know, this results in an ext3 file format which is better as a main partition. Ext2, I've read, is often used for the /home partition because it's non-journaling.

---

### Post by KuroYoma on 2009-02-11
This is a problem I ran into a lot.  What you need to download and burn is Super Grub CD.  I swear by it and can't live without it, i push my systems to far.  Has never failed me yet.  select the linux menu then the grub menu then have it fix grub tell it were your linux partition is.  sda3 and you are good to go.

---

### Post by chaosTechnician on 2009-02-11
Once I downloaded the Ubuntu install CD and actually burned it, I was able to reinstall Ubuntu and, in the process, repair GRUB.
I did replace hda3 with an ext3 partition (thanks for the advice) during installation.

---

### Post by KuroYoma on 2009-02-12
Glad to here that everything worked out for you. =)

---

