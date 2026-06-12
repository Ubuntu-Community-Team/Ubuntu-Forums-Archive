---
title: "XP pro + Vista + Ubuntu x2 home network"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by patnshan on 2007-05-02
Hello,
I recently entered the world of Ubuntu and like it a lot.  I am having trouble setting up a simple home network.  I cannot see shared folders across the network, even though I've enabled the folders to be shared.  I have internet connections through all the PC's, regardless of which OS. 
Here's what I have:
1. Linksys WRT54GL (with hyperWRT) managing cable internet and network connections
2. Dell 1505 Laptop running Vista connected wirelessly 
3. HTPC dual boot XP Pro and Ubuntu 7.04 connected wired with FAT32 partition on drive for file storage
4. XP home desktop connected wired
5. Old HP PIII desktop running Ubuntu connected wired

What I want to be able to do:
Minimum:
1. share a printer connected to one of the desktops with all in network
2. share files on the FAT32 drive in the HTPC with all the networked computers
If possible:
Allow all computers on my network complete access to all the other computers, of course with the right passwords. 

What is the best way to get this to work?  I have tried windows network setup and it does not work.  I have read about Samba, but I fear it is too complicated for what I want it to do.  I am using Trend Micro PC-Cillin Internet security on computers 2, 4, and 5.  I am using Comodo free firewall and Avast antivirus on computer 3 (PC-cillin only has 3 licenses).

I look forward to any guidance you could offer.  

Thanks,

Pat

---

### Post by Matchless on 2007-05-02
Hi,
    I am no expert, but what you want to do is very possible as I have exactly that working. I will just give you an overview of what I did. Firstly you must mount the fat32 drive in every installation of linux, this entails creating a mountpoint and then adding an entry in the /etc/fstab file, otherwise you will not be able to see the drive in linux, but will see it in windows if on the same PC. Secondly you will need to share the drive to allow other PC's on the network to see the drive. You have to install samba and nfs on the linux PC's, samba to share with windows pc's and nfs to share with other linux pc's.
On the windows pc's you need to share any folders and the same on the linux pc's. Sharing on linux PC's need sharing via samba and nfs enabled and you can select public and writable sharing for both to start off with.
To share a printer is easy, connect to a linux pc and install the drivers, then enable sharing of the printer (samba and /or NFS) enable share printers on the network in the printer gui and other linux pc's should see the printer without installing any drivers on them. On windows PC's you will have to install the drivers and point the pc to the printer on the networked linux pc. If you connect the printer to the windows PC, then you need to install the drivers on the linux pc's as well as the windows pc's.
Hope this gets you on the way. As a tip use the search function in the ubuntu forums and you will find all the exact details in various threads.
This may seem like a mouthfull and it actually is, as there are more variations to what I mentioned above, but do not dispair. I suggest you take it one part at a time. First try to get one linux pc to see a folder on a windows PC. Make sure that your networking is properly set up and that you can ping both pc's from both sides. Now always reboot both PC's after any setting changes have been made. On Kubuntu go to System Settings, Remote Places and Samba. If sharing has been enabled on a folder or drive on both PC's you should see the seperate workgroups of both pc's and be able to open them.
Try this and you should be on your way.Good luck

---

### Post by patnshan on 2007-05-02
Matchless,
Thanks very much for the reply.  I will certainly make sure the FAT32 drive is mounted in linux on the desktop it is installed in.  I am unsure how to mount it in the others, given that my network is not seeing the drive yet.  
I will install Samba and nfs and see what it brings me.  I will post back when I have tried it. 
Regards,
Pat

---

### Post by patnshan on 2007-05-03
So I installed samba on the linux PC that has the shared drive on it.  I now am able to see the drive on the other linux PC (without installing Samba on that linux PC:confused: )  This is a great start, regardless of why it works!

As for the windows laptop, I installed nfs on the linux system as well, but I cannot see the shared drive on it.  I also cannot see the vista notebook as part of the network on the linux PC's.  What do I need to do to configure it correctly?

Thanks,

Pat

---

### Post by Matchless on 2007-05-04
Pat,
     Just some clarity as I see it. Samba is installed on the linux PC so that it can share with windows PC's. NFS is installed on linux pc's to share with other linux pc's. I have  also noticed and was informed that linux pc's can also share via Samba, but that it is not really recommended as the most efficient.
As to the sharing between windows and linux, to start off you must be sure that the pc's are actually talking to one another, ping both ways. I use Kubuntu and then "Remote places", not sure what the same is in Ubuntu. Initially the sequence of the steps can cause some problems:
You must keep in mind that you can easily share drives or folders between linux and other linux PC's, but need to ensure that if you are sharing between windows and linux pc's you should have these drives or folders on a fat32 partition, as linux writing to an ntfs partition can cause problems.
1) Assume 2 PC's A & B need to share
2) First treat A as the server which has a folder to share
3) Make sure this folder or drive is shared on A
4) Under sharing ensure that this folder is shared via Samba and NFS and level is public and writable. (low security)
5) Now reboot A
6) Then reboot B
7) Now check on B if you can see the shared folder on A
If this sequential booting is not done it could cause your network to not be properly communicating, depending on how it is set up and thus cause you to think you have done something wrong.
Hope this gets you going a bit further.

---

