---
title: "New AMD - NAS build"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by burnetbj on 2009-05-18
Hello People

I really some help on a few questions here

I and trying to build my first NAS box was thinking of Ubuntu server but as I have no knowledge of CLI, i was thinking of trying FreeNAS for the (GUI) 

My question is can someone please chime in with some confirmation of a Motherboard known to work with this [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103255](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103255) and be Linux complaint either FreeNAS or Ubuntu

I have a Spare ASUS EN6600GT and RAM will purchase CPU after i can track down a decent board

I have some pretty high end PC parts now I just wanted a NAS for storage and the 45w dual core CPU looked prime for this

My current CPU's are all 100w so was looking for something low power

If someone with a little server experience could help would be greatly appreciated 

please point me in a direction of a board that can go RAID 5 with 1Tb x 4 with posted CPU and either has onboard video the is Linux compatible or has PCI-e for the 6600

Thanks in advance

I have seen tons of boards out there i just dont have the time or money to be trying out boards that wont work with linux as I am new to linux as it is and never used a NAS setup so I am already in for a workout ....if the hardware works that would be a huge +

---

### Post by burnetbj on 2009-05-19
Possibly this ?

[http://www.ewiz.com/detail.php?name=MB-M3N78EM](http://www.ewiz.com/detail.php?name=MB-M3N78EM)

has RAID 5 and its AM2+ nVidia based 

Seems like it would be OK but who knows

Doesnt need to be mini atx was just looking at going small ....really doesnt matter

---

### Post by burnetbj on 2009-05-20
Well since this is getting no where quick I feel like scrapping the project. I have a AMD 3000+ venice I am going to use with a ASUS A8N32-Deluxe with a EN6600gt TOP with 2 Gb of RAM as they are left overs and in good shape with all the features I need and i have been able to run all hardware under 7.04 so I feel better just going with a quick release server case and my left over hardware 

Booo to the NAS people out there for the lack of help 

I will get over it now and start working on getting my new setup going


Still would have been nice having a tiny new gadget to talk about

---

### Post by asmoore82 on 2009-05-20
will this NAS need to provide windows access too?

I hear a lot of folks using SMB for a linux to linux setup which is quite "interesting"

linux to linux should use NFS
linux to windows should use SMB
linux to mac should use AFP or ?NFS?

backups should use rsync - no real need for a "NAS" just for backups.

---

### Post by burnetbj on 2009-05-20
I am not sure what I will be using right now as I am green horn to say the least. I am just trying to make a headless file server that I can store family pics, music , movies around 600Gb so far was shooting for 1Tb for now on a low power yet strong running system that would be a great starting block for practicing CLI and Network 

There wont be any Windows files sharing at this point its all Linux to linux, I have 5 PC's right now 2 of them with everything on them as back up. I am going to try and get everything on a RAID 5 and and try to figure out rsync with my main machine having a copy of eveything I need with another copy in a RAID that everyone can access with a hot swap setup incase i lose a HDD

---

### Post by asmoore82 on 2009-05-20
sounds fun,
NFS is basically linux's "native" network filesharing that is too often forgotten
in the utter mess of mixed OS setups.

---

