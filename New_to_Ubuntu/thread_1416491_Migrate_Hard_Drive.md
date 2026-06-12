---
title: "Migrate Hard Drive"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by expatCM on 2010-02-26
My wife has been reminding me for the last couple of weeks that her hard drive is failing.  No doubt about that ...  it is.  It is now time to deal with this.

It is an older machine and an IDE drive.  What I would like to do is to put another similar drive on the machine as Slave, boot from the CD and then map / copy one drive to the other.  Remove the present Master, change the jumper on the new Drive to Master and ...  happy wife.

I had the idea that this can be done using the dd command.  I looked at man dd and get the idea that this may not be correct since the man page suggests that this is used for copying files.

Could anyone please tell me the command line syntax to copy one drive to another in order to solve this problem.   

I guess I would have to edit the UUID in fstab before it would work but nothing else?

---

### Post by Peter09 on 2010-02-26
I belive there are utilities in Synaptic to clone hard drives, I am not sure what they are called. I think one is call CloneZilla. I'm not sure wether you need to download this and make a bootable CD of it - might be worth investigating.
 
I'm sure others will give you more detail.

---

### Post by yeats on 2010-02-26
dd does what you're thinking it does - a bit-for-bit copy.  Clonezilla is also a very user friendly option (pop in a live CD and follow the prompts).  Either will get the job done!

---

### Post by Sir Jasper on 2010-02-26
Hi,

The free version of HDClone should be a simple and, with its safety features,  effective way to clone (a failing hard drive) to a larger replacement hard drive.

My regards

PS google hdclone for more information.

---

### Post by Kakers on 2010-02-26
> **chrissharp123 said:**
> dd does what you're thinking it does - a bit-for-bit copy.  Clonezilla is also a very user friendly option (pop in a live CD and follow the prompts).  Either will get the job done!

Yes, only problem with dd though is you don't know if it has crashed or frozon... so you kinda just have to wait. Downloaded Clonezilla myself recently, still have to try it out yet. But from what I have seen this would probably be the better option

---

### Post by louieb on 2010-02-26
Two ways I have done it 
1) backup and restore with partimage - does not work if your using the ext4 file-system. Otherwise work great. 

2) Gparted [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") has the advantage of being able to resize a partition (to a larger size only) when you do the copy. And works with most file-systems. 

Both will require you to reinstall GRUB.

---

### Post by expatCM on 2010-02-26
Thank you for all the comments.

I am just downloading Clonezilla after reviewing the options.  Clonezilla expressly states support for ext4 which attracted my attention.

HDClone appears interesting but I am uncertain about ext4 support and also note that they cap the transfer rate which is sad.

Gparted ....  I never knew that you could use this to clone a drive.  The support of this function is a bit minimal though so I decided to skip that.

dd is fine I am sure but if you do not know the syntax well then it is hard to figure out from the man file.

"Both will require you to reinstall GRUB." .....  now that is a little worrying ... 

I guess I am about to do some finding out by doing since I still have not answered what happens to the UUID - does it need to be restated in fstab or is it simply cloned ...

---

### Post by theozzlives on 2010-02-26
I think Clonezilla will do what you want. I've cloned Virtual Disks, Windows Disks, and Ubuntu Disks with it.

---

### Post by egalvan on 2010-02-26
> **expatCM said:**
> 
I guess I am about to do some finding out by doing since I still have not answered what happens to the UUID - does it need to be restated in fstab or is it simply cloned ...

dd will clone everything (that you tell it to), including the UUID's.

you could also clone the UUID's yourself...
get them with 

```
blkid
```

or use gparted to get the UUID's...

copy them down somewhere...

then re-write them to the new partitions once the cloning/copying is done.

---

