---
title: "Multiple Drives, Multiboot, FTP and AZBox Elite?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by ken0069 on 2010-01-10
OK so I've been having problems getting Ubuntu 9.10 to allow me to share files on another hard drive in this computer with other computers on my network.  I've read a ton of stuff on here but so far no one has given me anything that works?  I've got a Cradlepoint router that is my DHCP server, I've got file sharing enabled on my network and from my Ubuntu box I can see and access files on OTHER WINDOWS computers on my network.  However, when I try to access the Windows drive on this one while I'm booted on Ubuntu, all I can share is the "Downloads" folder.  I've looked and looked and I haven't been able to find any setting to allow me to share those partitions?

So a little while ago I downloaded a new firmware update to my AZBox while I was booted in Windows XP and I stored it in a downloads folder on the D:\ partition on that Windows drive.  So now I'm booted up in Ubuntu and I can access that folder from my Ubuntu desktop but I can't access it from Filezilla to FTP it to my AZBox for installation?  The left column in Filezilla does NOT contain either partition of that 250GB drive that Windows XP is installed on and I can't find it in the file structure in that column?

Anyone have any ideas on these?

---

### Post by cariboo on 2010-01-10
How do you have your Windows partitions mounted? Do they mount automagically on boot or do you have to double click them to mount?

Do you have samba installed, and /etc/samba/smb.conf configured correctly?

Do have the correct permissions set on the ntfs mount points?

---

### Post by ken0069 on 2010-01-10
> **cariboo907 said:**
> How do you have your Windows partitions mounted? Do they mount automagically on boot or do you have to double click them to mount?

Do you have samba installed, and /etc/samba/smb.conf configured correctly?

Do have the correct permissions set on the ntfs mount points?

That partitioned drive shows up in "Places" and when I click on them I can see the stuff on both partitions and then they are on the Desktop.  So they don't automatically get put on the desktop at boot.  I have to open them first.  

Yes, samba is installed but I have no clue as to whether it's configured correctly or not?  Wasn't aware that had to be done after it was installed?

Also don't have a clue as to where to set permissions on the NTFS partitions?  I've right clicked on everything I could find with those drives visible but there's nothing that has jumped out at me as to how to share them on my network like it was with the Downloads folder.  

I know how to do all this on Windows and it's all just point and click, but Ubuntu is NOT Windows.

---

### Post by ken0069 on 2010-01-11
Oh, and I figured out how to access those partitions from Filezilla so you all can forget about that one!

Still need to share those partitions on my network though as I have three multiboot computers that are all running Ubuntu along with various versions of Winders!;)

---

### Post by steveneddy on 2010-01-21
Mounting drives:

from a link in my sig:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Manually_Mount_and_Unmount_a_device](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Manually_Mount_and_Unmount_a_device)

File sharing:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Filesharing](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Filesharing)

and finally:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

good luck

---

