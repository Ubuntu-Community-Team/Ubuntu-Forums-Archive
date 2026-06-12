---
title: "File Server Question regarding Format."
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-04
Hi Gang

I'm thinking about upgrading a backup system to a file server system.  (In-house backup drive failed tonight, is why!)

I've never given this much thought because I have an external hard drive for each computer sized to hold both internal hard drives and always used whatever file system the internal hard drives had for the backup drive.  My In-house larger backup drive that holds redundant backups from all the externals (including my Ubuntu Linux boxes) was formatted ntfs since it's connected to an old Windows machine in a different building used only for that purpose.
I also have off-site storage and have no idea WHAT file system they use, whatever it is I'm sure it's UNIX based.

OK, I'm thinking of buying a NAS file server (info on it's in another post) and if I use a file server, it will have to be used by 6 Linux machines, 2 Windows machines.  I was planning on formatting it in ext3, thinking the file system has little to do with the files stored on it.  But someone mentioned that Windows machines cannot see ext3 file systems?  That might be on USB drives, but this is a Network Drive and the files will be sent to the machines via TCP/IP.

This is NOT a Server Server, but simply a File Server, data storage not program storage, except for uninstalled programs or backups of installed system programs.

I've already been backing up my /home directory through the LAN to a Windows Drive formatted in ntfs and retrieve that data when I louse up my experimental machine I use for testing things on.

So now I'm really confused!!!!!

Can somebody pull the dark clouds from the cobwebs in the ole gray matter here?

TTUL
Gary

---

### Post by nandemonai on 2008-12-05
If your running a file server it makes no difference what fs type is used on the 'server' as like you mentioned, it will be over TCP/IP.

If your buying one (rather than making your own from another machine) I'd try for one that supports both Windows Networking (samba) and NFS. They usually come all setup and good to go so I doubt you'd be formatting it yourself anyway.

That way you can use NFS instead of samba for the *nix machines which I've found is faster.

If you have a spare machine and a decent sized drive or two I'd recommend just sticking a server install of ubuntu on that and setting up samba/nfs.

Usually a lot cheaper if you have the hardware lying around anyway. :D

---

### Post by handydan918 on 2008-12-05
> If everyone crosses against the red light, then there’s nothing to be afraid of. 

Except a road-train at 100kph....

---

### Post by nandemonai on 2008-12-05
> **handydan918 said:**
> Except a road-train at 100kph....

Touché ;)

---

### Post by Kellemora on 2008-12-05
Hi nandemonai

Computers I have plenty of, Schmartz I don't have much of, and therein lies my problem.

FWIW:  I have downloaded and installed Edubuntu on one of my machines in order to try and understand how a server should be set up.  Figured doing so would help me understand and learn quicker.  But in my case, it even confused me even more.

To make matters even harder, I cannot even get rsync to see a drive (or shared folder) not locate on a drive connected to this computer.  Yet I have 8 computers (6 Ubuntu, 2 Doze XP) networked using Samba.  They don't appear in Places/network very often, but I can mount all of them manually using IP numbers.  And ALL Computers, drives and shares show up under smbtree, so the network itself is just fine.  I can manually copy things hither and yon with no problems.  Just can't get rsync to work.

My thoughts behind getting a NAS this time around is that it uses tcp/ip and might just work without problems.

The particular NAS I was looking at is a 1TB LaCie 301257U which supports FTP, HTTP, SMB, AFP & Apple Bonjour, it has 2 hot swap Sata II drives, unfortunately it's set up as RAID.
It's CHEAP under 300 bucks, but it says I need a computer with 512megs of memory, which indicates to me it MIGHT be FAKE RAID which is even worse.

Don't laugh, besides the on-line computers I have a few more old computers that sit around and do nothing except hold shared hard drives for redundant backups and fans to keep them cool, for my old LAN which I pulled off-line when I made the switch to Ubuntu.
I believe they are too old though to be used as a file server, so I didn't mention them.

I've read just about everything I could find on-line about setting up a computer as a file server and I'm not afraid to admit that most of the directions are over my head still.
I'm 61 years old also, not that that has slowed me down much.
I've only been using Ubuntu now for a tad over 3 months and have my whole office running under Ubuntu, except for front office which requires Doze XP for the proprietary hardware used up there.  Most Manufacturers don't support Linux yet!

I would consider building a file server, if I knew how!
Could you point me to someplace that might be sub-beginner level tutorials?

Thanks

TTUL
Gary

---

### Post by nandemonai on 2008-12-06
[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

That will certainly get you started ;)

---

### Post by Kellemora on 2008-12-06
Thanks N

Much better than the stuff I found in the Wiki and other places!

I've already read some of it and it explained things I was totally lost regarding!

Thanks a Million (no 1099 will be issued, hi hi)

TTUL
Gary

---

### Post by Paqman on 2008-12-06
Most NAS boxes that you buy off the shelf will be Linux-based machines and will use ext3. Since they are generally intended to serve to Windows machines they use SAMBA, which is an open source system for using the Windows smb/cifs network protocol. So even though the disks are formatted as ext3, the files get dished up in a way that Windows machines are happy with. Linux machines can also quite happily mount smb/cifs shares (just install the package smbfs and follow [these instructions]("http://ubuntuforums.org/showthread.php?t=288534"))

I can highly recommend the QNAP TS-209 if you're in the market for a NAS. It's one of the best IT purchases i've ever made.

---

### Post by Kellemora on 2008-12-06
Hi again Paqman!

I purposely REMOVE smbfs because it blocks the view of some shared folders.

Windows has no problem seeing shared folders on Ubuntu or reading them, if the program supports the file type of course.

I've tested this many times using smbtree!

Without smbfs every single shared machine and folder appears, no problem.  If smbfs is installed, some of the machines and many of the folders no longer appear in smbtree and also are not accessible by IP numbers.

NAS boxes use the TCP/IP protocol.
The particular cheap john I was looking at has the following built in networks:  FTP, HTTP, SMB, AFP, and Apple Bonjour.

I was going to use it as the file server, rather than as a backup, just because it only comes with RAID and as you already know, I don't trust RAID at all.
I can pick up the same brand NAS much smaller no RAID, single drive, but it don't have the networking capabilities, and I don't have enough SCHMARTZ to know if that's important or not.
In other words, I see no difference between it and a USB External Drive other than it uses TCP/IP over Ethernet.  My Ethernet is already quite busy with 8 computers on-line.
Where USB is used only for a few things.  And I may be showing my ignorance here too, since they are probably all tied together inside somehow anyhow, hi hi...........

If I could figure out how to automate rsync using Cron, the way it stands right now, I would be a happy camper!
I've tried grsync with the same problem.  It cannot see a mounted drive on another computer when automated, but works just fine manually.  Running rsync from a terminal line that is!
But nonetheless I'm learning things slowly, ever so slowly and eventually figure out what I'm doing wrong!

It's these confounded computin' contraptions I tell ya!
I'll take my Friden Machine and Victor Adder any day of the week, hi hi..........  Oops, showing my age!

TTUL
Gary

---

