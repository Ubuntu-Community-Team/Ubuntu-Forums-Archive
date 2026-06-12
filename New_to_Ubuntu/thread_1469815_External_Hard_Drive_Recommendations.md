---
title: "External Hard Drive Recommendations?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by prettymess on 2010-05-02
Hey, I'm currently running Ubuntu 9.04 and I'd love to upgrade and completely clean out my lap top, so I can start fresh, but I can't afford to lose any of the music I have on this computer.  

I basically just need an external hard drive for back up reasons, but I don't really know what to look for.  I'm kind of hoping for something in the $50 price range as I don't need anything too big (capacity wise).  

I googled "external hard drive" and came up with [this]("http://www.google.com/products/catalog?q=external+hard+drive&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=16101611208907016687&ei=FKHdS9CaNoyQ8gS_tLWtBw&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CCEQ8wIwAA#ps-sellers").  The reviews seem good, but I'm still kind of weary for some reason.

Anyone have any experience with that one or have any recommendations?  I guess I'm looking for anything around or over 100GB.

---

### Post by quadproc on 2010-05-02
[QUOTE=prettymess;9218902...
I basically just need an external hard drive for back up reasons, but I don't really know what to look for.  I'm kind of hoping for something in the $50 price range as I don't need anything too big (capacity wise)...
[/QUOTE]
It would be useful to know what kind of interface you need.  I suspect that you'll want the fastest you can get for backup purposes and that is probably eSATA.  External drive assemblies are also available with USB and FireWire (various speeds) interfaces.

I had a really bad experience with a Buffalo external drive; it was unreliable and its replacement did not work with eSATA!  So I bought an inexpensive external case/power supply and put a SATA hard disk of my choice into the case.  I think that it took about 10 minutes to install and it worked fine the first time.

quadproc

---

### Post by egalvan on 2010-05-02
here is a listing of external drives on Newegg.com
that company has been around for a LONG time, and has an excellent rep.

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=414&name=External-Hard-Drives](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=414&name=External-Hard-Drives)

here is an example...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145321](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145321)


Hitachi, Seagate, Western Digital, Samsung

are some of the better manufacturers.


Also, I suggest running any hard drive for at least a week before trusting precious data...
One way is to copy one or two hundred GB of data onto the drive,
then copy the data back and forth on the drive itself...
dumping everygthing into onr folder makes this a little easier.
There are also "burn-in" types of programs that will do the job.

the majority of drive failures occur in the first week,
then they will usually last for the stated life.
(this used to be called "infant mortality", but I haven't seen that term in a while..)

---

### Post by srs5694 on 2010-05-02
I agree with egalvan's advice. A couple more points:

First, Linux works fine with most external hard disks. I have seen one or two reports of drives that just plain don't work because of weird interfaces, though. Therefore, I recommend buying from a place with a good return policy. (NewEgg is good in this respect, although as a mail-order outfit it's probably less convenient than returning something to a local store.) If you buy by mail, check customer reviews; load as many as possible on one page and search for "Linux" (or distribution names -- "Ubuntu", "Debian", "Fedora", "SUSE", etc.) to see if anybody's used the drive under Linux. Note that if it works under one distribution (Fedora, say), it'll almost certainly work under another (Ubuntu in your case).

Second, most hard disks use 512-byte sectors. Those that don't, such as some recent Western Digital drives, fake it. A few external drives use an interface that makes the drive seem to have 1024-byte or larger sectors. This is fine if you know what you're doing; however, some popular tools, such as libparted and utilities based on it (GNU Parted, GParted, etc.) aren't 100% relible with non-512-byte sectors. Thus, if you end up with such a drive, you may need to use lower-level utilities, such as fdisk or gdisk for partitioning and mkfs for creating a filesystem. This isn't the end of the world, but you should be aware of the issue so that if you have problems you'll have some idea of what to do.

---

### Post by prettymess on 2010-05-21
Thanks everyone for the help, I ended up going with: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822145321](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145321)

---

