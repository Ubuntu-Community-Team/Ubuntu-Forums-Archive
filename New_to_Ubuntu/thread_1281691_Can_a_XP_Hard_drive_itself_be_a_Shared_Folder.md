---
title: "Can a XP Hard drive itself be a Shared Folder?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by philwwright on 2009-10-03
I was so close to ubuntu seeing my XP machine. I have smbmount, smbclient, installed.  Ubuntu and Samba are the latest version.

I followed the exact terminal commangs to set up the shared folder, but it keeps failing to Open the Computer and Retrieve the files.

The XP in Question has the OS harddrive, and an extra harddrive that I gave permission the share the entire drive.

My question to the forum expert was could I be having a problem because Ubuntu would not see a harddrive to be a folder???

I asked the question twice, and got the following answer:

"You are along the right lines.Just the finer details that need ironing out.  I suggest that you hunt the web to see what you can find to fine tune"

I had followed his instructions up to that point as exact I as I could.  I even told him that there was a health issue and time was short.

I searched the web for the various causes, and you know I am telling the truth, for the error message of Can't Mount, followed by Can,t Retrieve.

Please forward this message to someone in the Forum who charges for their time.  I will be more than glad to paid  for his time.

Please don't be mad at me for writing this and kick me out of the forum.  Phil

---

### Post by -=hazard=- on 2009-10-03
Just Mount the XP Drive. If you use Ubuntu 9.04 go in Places and there you should see all the drivers of your HD doesn't mater xp or any other OS.

---

### Post by carnagex420x on 2009-10-03
You can share drive on XP a couple ways, as a shared letter drive, or you can mount that drive to an empty folder and have it shared AS as shared folder.
Either way it works, but if you mount to an empty folder you have to worry about folder permissions if its down a couple directories. The thing to remember with samba is its not all that fast, there is an election that takes place between PCs and they need to identify each other. If you are going to Network Neighborhood to browse for your PC it will take 10-15 min. to register.

---

### Post by -=hazard=- on 2009-10-03
Ops I misunderstood, he wants to share from 2 different PC's?

-Edit-

Try this simple gui "system-config-samba" you can find it on repos. And after you setup the server on ubuntu, the simple way to share a folder is just right click on it and select Sharing Options.

---

### Post by carnagex420x on 2009-10-03
If hes trying to use samba thats my understanding?

---

### Post by -=hazard=- on 2009-10-03
> **carnagex420x said:**
> If hes trying to use samba thats my understanding?

I guess so... though his post is weird.

---

### Post by Mark Phelps on 2009-10-03
You're mixing terminology and that may be preventing you from getting clear answers.

A hard drive is a physical thing. Once it is formatted, it contains a Master Boot Record (MBR) and one or more partitions.

When you mount a "drive", what you're actually doing is establishing access to a partition that has been created on that drive.

So, if an XP "drive" contains only one partition, the answer to the question of whether you can mount the entire partition is yes -- I do this all the time.

If the "drive" is an external one and plugs into your machine via a USB connection, all you have to do to access it is plug it in and open the folder for the partition on that drive in Places.

If the "drive" is internal to another machine, it's more complicated because you actually have to get network access to the other machine host first -- because that machine "owns" its partitions.  In that case, you will need NFS, SMB, CIFS, or whatever other software you choose to use.

---

### Post by -=hazard=- on 2009-10-04
> **Mark Phelps said:**
> You're mixing terminology and that may be preventing you from getting clear answers.

A hard drive is a physical thing. Once it is formatted, it contains a Master Boot Record (MBR) and one or more partitions.

When you mount a "drive", what you're actually doing is establishing access to a partition that has been created on that drive.

So, if an XP "drive" contains only one partition, the answer to the question of whether you can mount the entire partition is yes -- I do this all the time.

If the "drive" is an external one and plugs into your machine via a USB connection, all you have to do to access it is plug it in and open the folder for the partition on that drive in Places.

If the "drive" is internal to another machine, it's more complicated because you actually have to get network access to the other machine host first -- because that machine "owns" its partitions.  In that case, you will need NFS, SMB, CIFS, or whatever other software you choose to use.

Practically we already said all this, but in few words :)

---

