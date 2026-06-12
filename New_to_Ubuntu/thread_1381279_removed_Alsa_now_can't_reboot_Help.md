---
title: "removed Alsa now can't reboot Help"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Peterfc on 2010-01-14
After continual sound issues with Skype, and Pulse being the sound system now for Karmic i decided to remove Alsa to try and get Skype working properly. I have tried advice from searching this Forum and the Skype Forum. The sound on skype was never as good as on a windows machine. After removing Alsa i then rebooted but i could not reboot. After 12 hours it's time to ask for help.

On another machine i downloaded and created a new Iso and proceeded to install another 9.10 in another partition. When i get to the Partition manager i get a message.

Below is the messages i get when i try to do another install.

Thanks for reading

1. Write previous changes to disk before you can select an new partition. 
Any previous changes have to be written to disk 

You cannot undo this operation 
Please note that the resize operation may take a long time.

After clicking Forward 

2. The test of the file system with type ext3 in partition #1 scsi1 (0.0.0)(sda) found uncorrected errors
If you do not go back to the partitiong menu and correct these error the partitioning will be as is.

3. No ROOT FILE SYSTEM
No root file system is defined
please correct this from the partitioning menu.

---

### Post by sandyd on 2010-01-14
> **Peterfc said:**
> After continual sound issues with Skype, and Pulse being the sound system now for Karmic i decided to remove Alsa to try and get Skype working properly. I have tried advice from searching this Forum and the Skype Forum. The sound on skype was never as good as on a windows machine. After removing Alsa i then rebooted but i could not reboot. After 12 hours it's time to ask for help.

On another machine i downloaded and created a new Iso and proceeded to install another 9.10 in another partition. When i get to the Partition manager i get a message.

Below is the messages i get when i try to do another install.

Thanks for reading

1. Write previous changes to disk before you can select an new partition. 
Any previous changes have to be written to disk 

You cannot undo this operation 
Please note that the resize operation may take a long time.

After clicking Forward 

2. The test of the file system with type ext3 in partition #1 scsi1 (0.0.0)(sda) found uncorrected errors
If you do not go back to the partitiong menu and correct these error the partitioning will be as is.

3. No ROOT FILE SYSTEM
No root file system is defined
please correct this from the partitioning menu.
2. -> fsck -y /dev/sdax (enter in your partition)
3. Double check if you have selected the partition and chosen it to be "/". If you have, it is because of #2 that you are expericencing this problem

---

