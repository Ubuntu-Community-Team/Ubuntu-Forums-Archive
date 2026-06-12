---
title: "I need to connect to an external drive on another computer"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2008-04-26
Hi guys,

I am a newbie, just completed setting up my home network. I am needing to be able to connect to an external drive that is connected via usb to my desktop computer also running gutsy from my laptop. I have smb access to the desktop computer, and in order to mount the drive from that computer I have setup a launcher on its desktop. 

My question is can I setup the share folders to allow me to mount that drive from the laptop (given of course that the desktop box is running) 

I tried the following in a terminal 

 sudo mount smb://desktop/media/seagate 
[sudo] password for kim:
mount: can't find smb://desktop/media/seagate in /etc/fstab or /etc/mtab
kim@laptop:~$ 

So obviously if this is possible then I have to add something to the fstab or mtab. Any ideas on the best way to add the required commands? 

(In windows I simply set up a network link)

Also If I intend to completely ditch MS (which is my hope) then am I better off using Samba or NFS for networking at home?

---

### Post by superprash2003 on 2008-04-26
info on mounting here [http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php](http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php) 
  You could use samba itself.. since you have been using it all this while..

---

### Post by tropdoug on 2008-04-27
had a look that that, good information, but in this case the drive is merely a storage drive, not a windows system. So then after reading a bit more, I realised that I can add my media folder as a share (on the desktop) and as long as the external drive is mounted, I should be able to connect to it to use files, as required through the normal process, and I can. So that works. I think I should use gparted later to repartition that drive move all the files into the new partition and then delete the vfat partition and turn the lot over to ext3. 

Anyway thanks for the help.

---

