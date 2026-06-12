---
title: "silly nfs/smb noob question"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Circus-Killer on 2007-10-08
okay, today i have decided what i want to do with my ol' desktop. its old, and well, thats about it, old is enough reason to stop using it as a desktop. however, i have decided that i want to make it a fileserver for my house, so that all the machines on my home network can access the same files on the file server.

now, i know that the advantage of using smb is that both windows and linux machines can both connect to a samba server. but my question is, can a windows machine connect to an nfs server?

or maybe a more appropriate question would be, what should i use, nfs, ftp, or smb?

(basically, i want to store all my mp3s on the single fileserver, so that all my pcs and laptops can access the same files. (so i dont have to have the same huge library on each and every machine))

---

### Post by netztier on 2007-10-08
> **Circus-Killer said:**
> okay, today i have decided what i want to do with my ol' desktop. its old, and well, thats about it, old is enough reason to stop using it as a desktop. however, i have decided that i want to make it a fileserver for my house, so that all the machines on my home network can access the same files on the file server.

now, i know that the advantage of using smb is that both windows and linux machines can both connect to a samba server. but my question is, can a windows machine connect to an nfs server?

or maybe a more appropriate question would be, what should i use, nfs, ftp, or smb?

(basically, i want to store all my mp3s on the single fileserver, so that all my pcs and laptops can access the same files. (so i dont have to have the same huge library on each and every machine))

Well, that's a good idea to start with. I am doing pretty much the same thing with my own server. I suggest to use Gigabit Ethernet, a PCI SATA controller and to throw in some new large SATA disks for data ( I believe Wester Digital has a product range of SATA disk suitable for 24/7 operation) while using some old small PATA disk to boot from. You could even go for one of those 1-4GByte IDE-Flash modules you can plug right into the 40pin IDE socket on the motherboard - the are large enough to hold an entire installation of ubuntu-server.

Use some passively cooled graphics card and see if you can swap the CPU cooler for a large one that doesn't require active cooling but is happy with a low-rev (= low-noise) rear case fan that draws some air across it. Of course, if you have a well-ventilated closet to hide the server in, there's less need to worry about noise.

My venerable P-III 500MHz has two PATA 120 Gig disks in software RAID-1 and does 20-22MByte/s with NFS, and 15MByte/s to an Ubuntu CIFS client (haven't properly tested with an XP Client).

Write performance is around 10MByte/s on NFS and 16MByte/s with CIFS (don't ask me why - the difference is there, but I have no clue why). When files are served from the cache, NFS peaks out over 50Mbyte/s, while CIFS/Samba seems to stay with 15MByte/s.

In a nutshell: I believe NFS to be faster "in general". There something called "Windows Services for UNIX" (see [http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx](http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx)) which is - I believe - available free of charge. It includes an NFS client for Windows see the Withe paper [http://technet.microsoft.com/en-us/library/bb463214.aspx](http://technet.microsoft.com/en-us/library/bb463214.aspx), but I don't know anything about it's stability and performance nor how to configure it.

If you expect a broad range of different clients from Windows to MacOS, I suggest to use Samba/CIFS - it is widely supported, sometimes even by media-playing hardware clients.

 If a central media repository is what you want, the next thing to think of is a media streaming server: Look at **mt-daapd** which is an iTunes compatible DAAP/UPnP-AV server that can stream media to the network. There might be other apps that can also stream media, but some of them are not free (Twonky Media, for example).


best regards

Marc

---

