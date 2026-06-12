---
title: "Sharing Lubuntu desktop HDDs with Windows 7 PC..."
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by Skillet98 on 2013-09-28
I have an old desktop running Lubuntu 13.04. That desktop contains three hard drives, one for the main Lubuntu file system, and two extra drives that are empty. I can access those drives just fine on the Lubuntu system.

I also have Samba installed, and I'm trying to share those two drives with the other PCs on my network. 1 is running Vista and 2 are running Windows 7. Only one of them is important as far as being able to connect, however.

My problem is, I can't seem to access the two drives I have shared on my Lubuntu machine. I can SEE them on my network... but trying to access either drive gives me an error that only reads "You do not have permission to access \\MEDIASERVER\Storage1. Contact your network admin to blah blah blah..."

Yes, I have both drives set to allow everyone on the network access to read and write... I also have them shared in Samba. As I said, I can see them... I just can't interact with them in any way.

Any help would be greatly appreciated.

---

### Post by Skillet98 on 2013-09-28
Alright, I may have found the problem... but I still don't know how to fix it. After mounting the drives on my Lubuntu machine, I can right-click them and change their permissions. I set them to allow anyone to access/read/write them, and click okay. But when opening that dialog to check those settings, they are set to only allow the owner again. How do I change this?

---

### Post by andyfied on 2013-10-28
Have you tried creating a directory on the drives and sharing just those?

To change the permissions you may need to run the file manager as root. Open a terminal and type ```
sudo pcmanfm
``` then it will ask for the root password. The file manager will then launch and you can change anything you want without restrictions or warnings so be careful! Close this version of pcmanfm as soon as you change the group permissions to read/write (I wouldn't allow remote execution of files.)

---

