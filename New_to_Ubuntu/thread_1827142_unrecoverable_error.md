---
title: "unrecoverable error"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by lbenn1950 on 2011-08-17
I fdisk my old laptop and formatted the drive in DOS. When I booted from the cd the Unbuntu splash screen came up and the little circle was spinning but then I get an error msg. Irrevocable error and needs to exit. Need help on this one. And where do I find the min. sys. req. This laptop is an old Dell inspiron 1000 with only 512k mem. You know I could be wrong on the mem. thing. It will run Winxp service pack 3.  Any ideas?

---

### Post by ClientAlive on 2011-08-17
> **lbenn1950 said:**
> I fdisk my old laptop and formatted the drive in DOS. When I booted from the cd the Unbuntu splash screen came up and the little circle was spinning but then I get an error msg. Irrevocable error and needs to exit. Need help on this one. And where do I find the min. sys. req. This laptop is an old Dell inspiron 1000 with only 512k mem. You know I could be wrong on the mem. thing. It will run Winxp service pack 3.  Any ideas?

 I think it may depend on which release of Ubuntu for what the sys reqs are. Here's a link to some information though:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

512 MB RAM should be ok for just about any Ubuntu installation.

When I put Ubuntu on this laptop it was kinda touch and go (this one's about 5 yrs old now). I started with Ubuntu 11.04, have 10.04 LTS now and like it a lot better.

The first thing that comes to my mind is the disk format. I'm pretty sure Ubuntu will format the disk as part of the installation process. That may be the best route to go - to let it do it that way. I've heard fat 16 is supported but have never tried it. When I installed on this laptop I ran the install right after wiping the disk with DBAN (nothing further). Personally, I chose the default ext4 file system though.

From what I understand, the difference in file system choices has to do with whether windows can use it or not. Again though, never tried it, just things I've read.

I'd try wiping the disk and then do an install right from there. Let the installation program format for you and see if there's an option to choose the file system you desire. I know that you can, optionally, go in and manually format partitions in one of the installation steps - I think it early on, like the 3rd or so step. If nothing else that should allow you to choose the file system type you wish.

Hope it helps.

Jake
------------

PS: Here's a couple links you may find useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

And the search page for it:

[http://www.google.com/search?client=opera&rls=en&q=partitioning+with+ubuntu&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#sclient=psy&hl=en&client=opera&hs=Tum&rls=en&channel=suggest&source=hp&q=partitioning+with+ubuntu&aq=f&aqi=&aql=&oq=partitioning+with+ubuntu&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=cd9f4072bf751801&biw=990&bih=632](http://www.google.com/search?client=opera&rls=en&q=partitioning+with+ubuntu&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#sclient=psy&hl=en&client=opera&hs=Tum&rls=en&channel=suggest&source=hp&q=partitioning+with+ubuntu&aq=f&aqi=&aql=&oq=partitioning+with+ubuntu&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=cd9f4072bf751801&biw=990&bih=632)

---

### Post by Elfy on 2011-08-17
Firstly if you really do have 512k memory then it'll not work.

Secondly - did you check that the downloaded iso was good? IF you used a torrent then it should be if not you can check it with md5sum

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


Then once you know the download is good you can check the burn integrity

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

If you still get a problem 

[https://help.ubuntu.com/community/BootFromCD#After%20I%20Select:%20%27Start%20or%20Install%20Ubuntu%27,%20it%20fails%20to%20boot](https://help.ubuntu.com/community/BootFromCD#After%20I%20Select:%20%27Start%20or%20Install%20Ubuntu%27,%20it%20fails%20to%20boot)

You might find that booting with some boot parameters might get it to work

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by pi.boy.travis on 2011-08-17
If you have 512k of RAM, you might want to look into Debian 1.3, or Debian 2.0 maybe. . .

---

