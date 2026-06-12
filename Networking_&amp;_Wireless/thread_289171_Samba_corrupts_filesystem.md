---
title: "Samba corrupts filesystem"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by jammer69 on 2006-10-30
Howdy,

** I could really use some expert help here, or even take a stab in the dark if you dare.  I appreciate any advice.

This is not the first time this has happened.  I'll try to explain as best I can:

**Cause**:

I was transferring a ~4GB file (rambo.mpg) from a win2k shared folder to a fat32 shared folder on my Dapper box.  It aborted midstream after about ~3 GB or so and gave me some strange "Invalid Protocol" error (or something to that extent).  It left a "rambo.mpg.part" file in the /media/windows/My Documents/My Video/ folder and I deleted it to start the file transfer over again.

**Problem**:

1. Now, I cannot transfer that same file to that same shared fat32 folder (/media/windows/My Documents/My Videos/).

2. Also, even if I load up my XP box, I still cannot transfer that same file from that win2k box to my XP box folder (C:\My Documents\My Videos).

3. There is no rambo.mpg file anywhere shown in that folder.

4. I even searched for hidden/system files and the registry for keys (locks, etc) and nothing shows up.

5. I can however transfer that same file to any other folder (like C:\Windows\Temp) in XP.

6. Even if I rename that file to "rambo-firstblood.mpg" and try to transfer it to that same fat32 folder (My Videos), it won't.

7. I keep getting a "Cannot copy <filename>: The Parameter is Incorrect"

By the way, I had a similar issue happen a while back using samba on Ubuntu when transferring a large GB file (tar backup) to a Win2k share.  In this case, it copied alright, but when I tried to delete that file in win2k it gave me a permission error or something and locked the file.  I could not delete it.

What's the dealio?

**Solution**:

You fill in the blank and I fly to your house, shake your hand, and make your next mortgage payment for you.

Thanks.

---

### Post by dmizer on 2006-10-30
a couple of things are probably happening here:
1) file size limit for transferring via samba is 2gig.
2) file size limit for saving files on fat23 is 4gig (this is true in both windows and linux).

the file size limitation is a result of 32 bit file handling.

you can transfer the file fine in xp, because ntfs does not have the size limit restrictions, and windows network file transfer also does not have a limit.

if you are going to regularly be transferring files of this size across your network, you should look into alternative network share design (ftp, ssh?)

---

### Post by dmizer on 2006-10-30
update:

the file size limit is apparently related to smbmount.  you MIGHT (might) be successful by trying the mount samba shares link in my sig, because it uses cifs rather thans smbmount.

---

### Post by dannyboy79 on 2006-10-31
> **dmizer said:**
> a couple of things are probably happening 
2) file size limit for saving files on fat23 is also around 2gig (this is true in both windows and linux).
 

Just FALSE, the limit for a fat32 partition is 4gb. Here is the facts to back up my statement, [http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

---

### Post by dmizer on 2006-10-31
lol ... you know, that's what i originally had in my post, but i changed it because i read differently somewhere else.  should have stuck with my first reaction.

---

### Post by dannyboy79 on 2006-11-01
> **dmizer said:**
> lol ... you know, that's what i originally had in my post, but i changed it because i read differently somewhere else.  should have stuck with my first reaction.

no big deal, i often transfer files between my xubuntu laptop and my ubuntu desktop/server, does nfs transfer any faster than samba or ftp? i ask because I see in your sig you have a NFS server/client howto.

---

### Post by dmizer on 2006-11-01
> **dannyboy79 said:**
> does nfs transfer any faster than samba or ftp? i ask because I see in your sig you have a NFS server/client howto.

twice (at least) as fast as samba (ftp i think it'll depend on your server setup and network configuration), and no dropped packets to mess up the works.  took me all of 15 minutes to set up both server and client by following the howto.

---

### Post by dannyboy79 on 2006-11-03
> **dmizer said:**
> twice (at least) as fast as samba (ftp i think it'll depend on your server setup and network configuration), and no dropped packets to mess up the works.  took me all of 15 minutes to set up both server and client by following the howto.

can I setup winbloz with nfs? or would it only be for transferring between linux distros? thanks for the info

---

### Post by dmizer on 2006-11-08
> **dannyboy79 said:**
> can I setup winbloz with nfs? or would it only be for transferring between linux distros? thanks for the info

no problem.  i really don't know of any way to make nfs work in windows.  that doesn't mean it's not possible though.  my supply of windows (windows 2000) computers is marginal at best ... just an old 700mhz pIII laptop which no longer has a keyboard, usb, or pcmcia slots.  still boots though ... last time i checked.

in short, i'd have to google it.

---

