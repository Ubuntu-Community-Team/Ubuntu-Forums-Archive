---
title: "HOW TO: Hardy File Sharing fix"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by timforlinux on 2008-05-10
I finally got my Ubuntu Hardy file sharing working.
My networking quit working while I was using Gutsy - after some update.  It didn't work initially with hardy either.  Now I have three hardy pcs networked ok.
  To do so, I had to edit /etc/exports and /etc/hosts.  (files)
In the exports file I added:
/home/tim/Shared 192.168.0.100 (rw,no_root_squash,async)
/home/tim/Shared 192.168.0.103 (rw,no_root_squash,async)
/home/tim/Shared 192.168.0.105 (rw,no_root_squash,async)
at the end of the file.  As you see there is one line for each computer that may access the main one (.100).  First is the directory that is being shared from this computer, and then the address of who may access it, then some parameters I don't fully understand but work.  Some say to use sync instead of async - i don't know?.

In the hosts file, after the first two lines already present:
  127.0.0.1 localhost
  127.0.1.1 tim-desktop.ubuntus
 I added:
192.168.0.105 common-desktop
192.168.0.103 marti-desktop
192.168.0.100 tim-desktop
  The first is the address of a computer on the network, the second item is the name it appears as.

  I derived this fix while attempting to follow a guide to nfs file sharing: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
  I do a lot of things sort of intuitively - I'm not sure why the things I did worked, but now the computers can see each other.  On each computer I also went to each shared folder (in nautilus - Sharing Options), UNmarked it shared, then marked it shared again.  Then I restarted each computer.  Haven't tried my MAC or Windows computer yet.

  It still seems to me that file sharing should 'just work' but it didn't on my computers.  Hope this helps someone else save some time.  It also seems that the networking is really using both nfs AND windows file sharing, and these changes help the nfs part work.  Make sure nfs_common is installed on your unbuntu hardy.

happily,
tim

---

### Post by bobd72 on 2008-05-10
I will be very interested to hear how you go with the Windows machine.  I have been trying for 2 days to get Hardy working with cifs to establish a share on boot with absolutely no success.  Please post if you are able to get it to work

---

