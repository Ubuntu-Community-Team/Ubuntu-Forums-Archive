---
title: "Preinstall Groundwork"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by PPPilot on 2010-12-24
I am currently setup on the same drive as follows:

/dev/sda1 has Karmic installed

Extended partition:
/dev/sda6 has Lucid installed

/dev/sda5 is the swap used by both above

The mbr being used is on sda6 so Lucid is the default in Grub with Karmic shown second. 

I want to install Maverick on sda1 in place of Karmic but I want to keep using the mbr that defaults to Lucid. I know if I just install Maverick on sda1 it will install the mbr there and that grub.conf will have maverick as default.

My question is, How to best install Maverick on sda1 in place of Karmic but keep using the mbr on sda6? I know i will have to update this grub so that it will see Maverick on sda1 after all is said and done.

Thanks in advance for any help

---

### Post by mcduck on 2010-12-24
Actually the MBR is not on any of your partitions, it's *always* at the beginning of the disk, before the first partition. (MBR is, by definition, the first 512-byte sector of a partitioned drive, and contains information about the disk and all the partitions on it.)

So, you probably are talking about which partition contains the Grub install that you are currently using... Ubuntu's installer will allow you to skip installing Grub if you click the Advanced-button during the install.

---

### Post by PPPilot on 2010-12-25
mcduck,

Thanks for the good advice. I ran into a bit of trouble as even though my Live CD checked out with md5sum it would fail about half way through the install with a comunicatios error. I tried it a couple of times and then gave up. I always burn the Alternate Install CD just in case. I popped that in and all when well. I am doing this in Maverick so it seems to be ok. 


Thanks again....

---

