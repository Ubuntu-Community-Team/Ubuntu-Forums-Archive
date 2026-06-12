---
title: "How to Mount Network Drive"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by rashwan on 2008-08-10
Hello,
am running ubuntu 8.04 works fine and i can access other Windows shared drives but when i open Shared Windows drive it mount itself on the Desktop and as soon as i reboot it disappear have to open it again to mount it
can i force it to auto mount itself next time i reboot ??
thanks for helping newbie

---

### Post by Iowan on 2008-08-11
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To on mounting CIFS shares. [Another]("http://ubuntuforums.org/showthread.php?t=202605") on using Samba.

---

### Post by generious on 2008-08-11
I'm still a bit of a newb when it comes to ubuntu.
Anyways this is what i have setup on my laptop and it works grand for me.

Make sure you have the share setup on the system that is hosting your share

Second create a mount directory for it.
Mine is home/generious/Main_PC_Films

edit your Fstab
sudo gedit /etc/fstab

//192.168.1.101/NameOfTheShare /home/Yourname/MountingDir smbfs auto, username=YourName, Password=YourPassword, uid=1000,umask=000,user   0 0

example of mine
//192.168.1.101/home/generious /home/generious/Main_Pc_Films smbfs auto, username=YeahRight, Password=YeahRight, uid=1000,umask=000,user   0 0

This will auto mount it for you after each reboot
I'm aware the password is still in my fstab

---

