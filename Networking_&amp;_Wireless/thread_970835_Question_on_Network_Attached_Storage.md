---
title: "Question on Network Attached Storage"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by P4iNz on 2008-11-04
Alright so I have figured out by now that my skills with samba are completely shot. I haven't used it since forever and a year ago. I want to mount two partitions I have on my Linksys NAS200 aka "FileFarm" the two partitions I want to be able to mount are Disk1 and Disk2. I am able to see the Public parts of the disk, so samba is connecting to that portion just fine. Now I need to tell samba to log into FileFarm using username password and I don't remember how to do this. If one of you would be so kind to help out.

---

### Post by P4iNz on 2008-11-04
Anyone help me out on this I have tried to configure samba running into some errors any suggestions would be greatly helpful.

---

### Post by GoldDog on 2008-12-02
I have the same difficulties and have received the same answers-none.

---

### Post by oaqster on 2009-01-16
recently joined these forms & have been going through some older threads and came across this, just in case you guyz have not found an answer yet, here is how im able to mount drives from my nas200 at startup, just add the following line to your /etc/fstab

//ipaddress_of_nas200/PUBLIC\040DISK\0401 /media/nas01/ smbfs uid=nas_uid,password=nas_pass 0  0

i know its kindof anoying that linksys decided to use spaces in the public share name for the drives, but escaping the spaces with "\040" did the trick for me.  if you dont like putting the user name & password for your nas in the fstab file, you should be able to create a user/group with the same id/pass locally and provide the userID in fstab, i havent tried this though so im not a 100%

also the user provided in the fstab should have full access to the PUBLIC DISK 01 or 02 on your nas.

---

