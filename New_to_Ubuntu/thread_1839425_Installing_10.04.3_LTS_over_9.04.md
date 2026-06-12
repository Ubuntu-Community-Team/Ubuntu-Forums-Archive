---
title: "Installing 10.04.3 LTS over 9.04"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by davidside on 2011-09-05
I  am currently dual-booting with Windows 7 and Ubuntu 9.04. I would like to install 10.04 over 9.04 but wasn't sure the best way to do this. Can I just reformat the partition that 9.04 is on and then install 10.04 there?

I have attached a screenshot from gparted. 

Thanks!

---

### Post by drs305 on 2011-09-05
Yes. For a completely fresh installation, just choose the manual partitioning option when installing from the CD and make sure you designate sda5 with / as the mountpoint. Tick the format box just to make sure sda5 is reformatted. The installation will see your swap partition so there is no need to make a new one.

---

### Post by cotcot on 2011-09-05
Obviously you do not mind to loose the documents etc from the /home partition of 9.04. Maybe consider to have a separate partition for /home. This allows you in the future to install a newer version over the older including reformatting the /root partition but keeping your /home.

---

### Post by davidside on 2011-09-05
What should I choose in the "Use as" drop down menu?

Cocot, most of what I have on 9.04 is junk and I don't mind losing it. What you say is good advice. Can you give me some pointers on how to create this on my new install? Thank you.

---

### Post by cotcot on 2011-09-06
Take some time to study this.

I always do partition formatting with the Gparted LiveCD.

In your case I suggest to 

- save any important docs you have on the windows partitions

Load the Gparted LiveCD

- move the swap to the end of the disk
- create an extended partition for the unallocated space
- create in the extended partition a logical partition for root (\) of 10 GB 
- create a second logical partition in the extended partition for home (\home) of the remaining space (about 22 GB in your case)

After finishing the partitioning; shut down and restart with the ubuntu CD (or usb).

When you install ubuntu after this do not format any partitions anymore. Just 'mount' the 1O GB partition as \ and the 22 GB partition as \home. The installer will allow you to do this. I have not used the installer of 11.04 because I have it as upgrades. I do not what changed in the installer. But I have added a link that might set you on the road.

Success



[[COLOR="Blue"]Extended partition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition")

[[COLOR="Blue"]Separate home[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

[[COLOR="Blue"]Installing ubuntu[/COLOR]]("http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/")

---

