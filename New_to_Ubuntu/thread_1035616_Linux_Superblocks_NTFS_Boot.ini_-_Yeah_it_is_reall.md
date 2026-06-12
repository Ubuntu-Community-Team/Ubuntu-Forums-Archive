---
title: "Linux Superblocks NTFS Boot.ini - Yeah it is really *uck**"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Tjcrazy on 2009-01-09
I brought a new hard drive and it arrived 2 days ago. It was a 7200rpm and 160gb HD. I tried to RAID0 it with another 5200rpm, 160gb HD. Something in that process went terribly wrong, because I could not start up windows because of a stupid:
'**Disk Boot Error, Please Insert System Disk And Press Enter**'
Error. I then de-RAIDED (A new word :D) the two hard drives and formatted them. I then kept trying to boot into windows (Which is still on a non-formatted 180gb drive). I've checked all the cabling and wires etc.
I then try the Windows XP Recovery disk, I run **chkdisk -r** on the drive, it reports everything OK. SO I then try **BOOTCFG /rebuild** it says it cannot read/write the disk and to run chkdsk. I run chkdsk again, it reports it as OK. SO I am stuck in an infinite loop... :'(
I decide that play time is over, and get my ubuntu 8.10 cd out and install that on the 5200rpm, 160gb HD. I can instantly see the 180gb HD and mount it, with no errors. I can see all my files, open and there all 100% OK. :D. I can even watch a 3gb HQ movie on it with no trouble.
Now I am thinking... Hmmm, whats the trouble here then. I then see that the drive has no BOOT.INI file at the root. I don't know how to fix that, so I run **sudo apt-get install ntfsprogs** and run **sudo e2fsck /dev/sdb1** (the 180gb HD) it reports it has bad superblocks. Now, I am REALLY confused.

Can you amazingly gifted OCers help me? I can read all the files but I cannot boot OR successfully e2fsck the HD (180gb). All I want to do is boot into windows. 
Before people ask, I cant back anything up since I dont have any External HDs atm (Only a 4gb Pen Drive)

I brought the Hard Drive hear, so I hope you people can help me!

Tim

---

### Post by blueridgedog on 2009-01-10
Just a suggestion, since you have the windows on a 180gig dirve and two 160gig drives, one with ubuntu and the other empty(?), surely between the two 160gig drives you can backup any files you want off of your windows system and do a clean install.

---

