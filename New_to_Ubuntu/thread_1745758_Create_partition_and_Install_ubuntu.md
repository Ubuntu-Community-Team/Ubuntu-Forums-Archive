---
title: "Create partition and Install ubuntu"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-05-01
I want to format whole harddisk into ntfs system.
I want c:,d: e: and f:
I want linux on d:
I want windows on c:
But now I only have ubuntu live cd and I will get windows cd after some days.
Using live cd how to partition into those 4 drives and install ubuntu on 2nd drive??
Please provide full steps.

---

### Post by Lateralis on 2011-05-01
Firstly, before you do anything, ensure you have a complete backup of all of your important files stored on an external medium, e.g. CD, DVD, pen drive(s) or external hard drive.  

Secondly, Ubuntu uses two different partitions: one partition for the "root" and a second partition for the hard drive "swap" partition.  If you wish to make use of hibernate and standby it is best to ensure that your swap is at least twice your RAM size.  The file format of the swap partition is unique to Linux.  The Ubuntu root will also need to be a file system like ext4 and NOT NTFS.  

Thirdly, drives in Linux are not recognised according to the familiar Windows c:, d: etc. designation.  

Fourthly, it is best to partition the hard drive using the in built Windows tools.  Leave some space on the hard drive unpartitioned - you'll use this during the Ubuntu installation.

---

### Post by Linux&amp;Gsus on 2011-05-01
I don't know what the Ubuntu LiveCD has on it by default. But I personally would probably install GParted. AFAIK you can install a program even when running a LiveCD, but it'll only be temporarily, as long as the session lasts.
Or, if you have the option, just download the GParted LiveCD and run that one to partition your HDD:

With GParted you can partition your disk to your liking. But you should not use NTFS for your Linux partition. EXT4 is a better choice. For Windows, of course, NTFS is the right choice. Also, make sure that your C drive is at the beginning of the disk.

In Linux, you need to get over the idea of the Windows style partition naming. There is no C D or E drive. So, i don't know what you have in mind exactly. But I would give Linux 3 partition. "root" is where all the program and the OS itself is, "Home" is where your data is stored, and a "swap".
Also for Windows I would have a separate data partition.

But the exact layout really depends on your needs and the size of the drive.

AND, if this is not a new drive you are using, make sure you have all your data safely backed up first. Before you do anything else. Otherwise it'll be lost.


EDIT: Lateralis was faster... :)

---

### Post by RobikShrestha on 2011-05-01
By c, d e and i meant sda0, 1 etc
I do not have windows cd right now but i will in a couple of days.
So, I would like to partition using gparted into 5 partitions: root and swap for linux (how much should i set aside for them, i have 4 gb ram, guess 8 and 8???). Is root where all the folders like /apt are saved?? I want the partitions with the *.deb files (i.e. the partition where the softwares are installed from software center) to be large.

If I create 5 contiguous partitions, say,
sda0: for windows
sda1 for root
sda2 for swap
sda3 for music
sda4 for backup
How do I install ubuntu on sda1??

---

### Post by Linux&amp;Gsus on 2011-05-01
> **RobikShrestha said:**
> So, I would like to partition using gparted into 5 partitions: root and swap for linux (how much should i set aside for them, i have 4 gb ram, guess 8 and 8???). Is root where all the folders like /apt are saved?? I want the partitions with the *.deb files (i.e. the partition where the softwares are installed from software center) to be large.

Yes, "root" is where your programs and the OS will be installed.

Define "large"...
Usually I have about 15-20GB for "root". But it also depends on how big your drive is and what your needs are. Also, if you don't define a "/home" partition, your data will go on that /root partition, as well, in your /home folder.

8GB for swap is too much. If you don't want to hibernate your computer I would give it maybe 1GB. If you do want to hibernate about 5GB. Maybe others have more ideas on that part.



> **RobikShrestha said:**
> 
sda3 for music
sda4 for backup

What do you mean by those partitions called music and backup?
First, if you want to access those with Linux and Windows you need to format them as NTFS, as Windows wont read/wrote EXT4.
Second, why backup? Are you thinking of a backup on the same drive where you have your data? You are aware that if the drive fails your backup is lost, as well. So, unless I missing something, this is a rather dangerous solution for your backup.



> **RobikShrestha said:**
> How do I install ubuntu on sda1??

First install Windows on the first partition. Then, start your computer with the Linux disk in the drive and select "Install" instead of "Try" Linux, when it comes to that point. Just make sure then you install it on the correct partition. :)

---

### Post by RobikShrestha on 2011-05-01
1. I have no option but to install ubuntu first. But I want those "music" and "backup" partitions workable for ubuntu and windows. "Backup" is just a name (not the actual backup. I would do them on DVDs).

2. I want the software center *.deb files to be available even if I re-install ubuntu. So, how would I backup those files? Is burning those .deb files on CD enough? Is there a way to automatically keep those deb files on another partition?

3. If I first install ubuntu on sda1, will I be able to install windows on sda0 later on? I want my windows to recognize other partitions except of course of the ubuntu.

4. I think I would use super grub or live cd to recover the grub later on (i.e. after I install windows). At that time, will "sudo update grub" be enough to recover grub? or is there anything extra to do?

---

### Post by Quackers on 2011-05-01
Firstly there's no such thing as sda0. Partitions start at 1.
It is easier if you install Windows first. If you intend to install Windows 7 it may use 2 partitions, but you won't know that until you install it.
If you re-install Ubuntu at any time you will lose the installed programs. Make backups.

---

