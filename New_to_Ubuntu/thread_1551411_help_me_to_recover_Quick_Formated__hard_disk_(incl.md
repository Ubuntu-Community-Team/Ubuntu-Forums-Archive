---
title: "help me to recover Quick Formated  hard disk (including encrypted partition)"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by medya on 2010-08-12
Guys , I beg everyone to help me, my data are so essential and so important ( my life is about to be ruined) .

intro: 
my dsl internet was out, I had to install a windows to use dial up internet (my dial up modem doesnt work in ubuntu) so in the process of installing windows , I accidentally ,"quick formated" my 320 GB hard disk . which included 5 or 6 partitions, among them :
- an encrypted partition , (I used ubuntu's defualt partiotion ecnryption)
- a few EXT3 and EXT4 partitions .

now windows setup Quick formated all of them to NTFS
right after the quick format I reilized my mistake and I quited the windows setup .

is there any chance that I can get my data back ?
what do you suggest me to do exactly ?
will those companies who recover data, be able to get data out of my encrypted partition too ? 

please guide me .


p.s : I am not a total idito , I had plugged an old hard disk and was planning to install windows on that old hd. but stupid windows thought it is not big enough space for it, so it had suggested me to format other big hd. :( and I had blindly accepted :(

---

### Post by Jazzy_Jeff on 2010-08-12
> **medya said:**
> Guys , I beg everyone to help me, my data are so essential and so important ( my life is about to be ruined) .

intro: 
my dsl internet was out, I had to install a windows to use dial up internet (my dial up modem doesnt work in ubuntu) so in the process of installing windows , I accidentally ,"quick formated" my 320 GB hard disk . which included 5 or 6 partitions, among them :
- an encrypted partition , (I used ubuntu's defualt partiotion ecnryption)
- a few EXT3 and EXT4 partitions .

now windows setup Quick formated all of them to NTFS
right after the quick format I reilized my mistake and I quited the windows setup .

is there any chance that I can get my data back ?
what do you suggest me to do exactly ?
will those companies who recover data, be able to get data out of my encrypted partition too ? 

please guide me .


p.s : I am not a total idito , I had plugged an old hard disk and was planning to install windows on that old hd. but stupid windows thought it is not big enough space for it, so it had suggested me to format other big hd. :( and I had blindly accepted :(

Hopefully someone can help you with this. You may have to take it in for recovery which is usually expensive. From this point forward BACKUP ALL YOUR IMPORTANT FILES!! Hard drives will crash at some point.

---

### Post by mastablasta on 2010-08-12
if you haven't wrote ANYTHING on the formated disk it will be possible to recover the files. But to get a good programme to do that you will have to pay for it.
 
for windows - recovermyfiles.com works.
maybe this one for Linux
[http://www.easeus.com/datarecoverywizard/](http://www.easeus.com/datarecoverywizard/)
 
anyway plenty programmes available just not sure if there is any good open soruce ones.
 
Here is some article i found (2006): 
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)
 
Maybe Knoopix Linux distro has some CD made specifically for file recovery. 
 
In same article this one is offere as good &easy Linux GUI solution:
[http://www.data-recovery-linux.com/](http://www.data-recovery-linux.com/)
 
but for pay.
 
don't know about encrypted files or parition, but if recovery is full and sucessfull then these should be recoverable as well.
 
edit if you have a spare HD, install OS on it and then try one of the programmes (even trial version) to see if it can even locate the files and partitions on the other disk.

---

### Post by frostschutz on 2010-08-12
> **medya said:**
> I accidentally ,"quick formated" my 320 GB hard disk . which included 5 or 6 partitions, among them :
- an encrypted partition , (I used ubuntu's defualt partiotion ecnryption)
- a few EXT3 and EXT4 partitions .

now windows setup Quick formated all of them to NTFS
right after the quick format I reilized my mistake and I quited the windows setup .


If you had several partitions on the disk, and then the disk was formatted to one single big partition, then it's possible the partitions are unhurt except for the first one. Use a Live CD, try testdisk to restore the partition table and see what it finds.

---

### Post by medya on 2010-08-12
> **mastablasta said:**
> if you haven't wrote ANYTHING on the formated disk it will be possible to recover the files. But to get a good programme to do that you will have to pay for it.
 
for windows - recovermyfiles.com works.
maybe this one for Linux
[http://www.easeus.com/datarecoverywizard/](http://www.easeus.com/datarecoverywizard/)
 
anyway plenty programmes available just not sure if there is any good open soruce ones.
 
Here is some article i found (2006): 
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)
 

Maybe Knoopix Linux distro has some CD made specifically for file recovery. 
 
In same article this one is offere as good &easy Linux GUI solution:
[http://www.data-recovery-linux.com/](http://www.data-recovery-linux.com/)
 
but for pay.
 
don't know about encrypted files or parition, but if recovery is full and sucessfull then these should be recoverable as well.
 
edit if you have a spare HD, install OS on it and then try one of the programmes (even trial version) to see if it can even locate the files and partitions on the other disk.



infact here i dont even trust those companies to recover my files , I unplugged the Hard disk power and cable. so I make sure , I write nothing on my Hard disk .

I m planning to buy a 1 TB hard disk ,
is it a good idea to copy bit-to-bit of my hard disk to the new hard disk before I give it to a company or before I try recover ile pgorams ? my data are really important and I wanna try to get as much data as possible .

so if YEs , what application to use to copy bit to bit ? 


and my other question :
I used crypt-setup to encrypt a partition , and now it is quick formated to NTFs. what can I do about it ?

---

### Post by medya on 2010-08-12
> **frostschutz said:**
> If you had several partitions on the disk, and then the disk was formatted to one single big partition, then it's possible the partitions are unhurt except for the first one. Use a Live CD, try testdisk to restore the partition table and see what it finds.

I think each partition is indiviudally quickformated to NTFs

---

### Post by mastablasta on 2010-08-12
you don't need to give the disk to any company. you just need to get one of those programmes and use them. no one will see your files that way. trial versions usually just show the recoverable files, but you will have to purchase it to actually recover the files. 
 
unfortunatelly i forgot which one i succesfully used at home... i don't have that computer with me anymore.
 
 
btw to all others. windows used to have "unformat" command. whatever happend to that command? Does linux have something similar?
 
 
Important thing is not to write anything on the disk. because you might overwrite the any formated files still hiding there.

---

### Post by medya on 2010-08-12
guys I need you guys , to tell me about the crypt-setup partition which uses LUKS, how to recover that?

---

### Post by joereith on 2010-08-12
[http://hotfile.com/dl/53814405/a345da4/Diskeeper.2010.Pro.Premier.14.0.896.32-bit_by_kbksrb.rar.html](http://hotfile.com/dl/53814405/a345da4/Diskeeper.2010.Pro.Premier.14.0.896.32-bit_by_kbksrb.rar.html)

[http://hotfile.com/dl/50547291/4aad47e/Active.Partition.Recovery.v5.3.717.rar.html](http://hotfile.com/dl/50547291/4aad47e/Active.Partition.Recovery.v5.3.717.rar.html)

Either of these will get your data back.

---

### Post by medya on 2010-08-12
> **joereith said:**
> [http://hotfile.com/dl/53814405/a345da4/Diskeeper.2010.Pro.Premier.14.0.896.32-bit_by_kbksrb.rar.html](http://hotfile.com/dl/53814405/a345da4/Diskeeper.2010.Pro.Premier.14.0.896.32-bit_by_kbksrb.rar.html)

[http://hotfile.com/dl/50547291/4aad47e/Active.Partition.Recovery.v5.3.717.rar.html](http://hotfile.com/dl/50547291/4aad47e/Active.Partition.Recovery.v5.3.717.rar.html)

Either of these will get your data back.

can you explain about them ? are they able to help about the encrypted partition too ?

---

### Post by mastablasta on 2010-08-12
if any of these programes can see it it can probably  recover it. once it recovers it you should be able to access the key that is used to open it (with your password). Full recovery ot me means that key is also recovered for that particular partition

---

