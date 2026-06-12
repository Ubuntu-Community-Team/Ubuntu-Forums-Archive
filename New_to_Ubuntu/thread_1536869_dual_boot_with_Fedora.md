---
title: "dual boot with Fedora"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by beew on 2010-07-22
Hi,

I am wondering where I can find instructions to dual boot Ubuntu 10.04 and Fedora 12/13 with Ubuntu already installed.

I found some information scattered about in the Fedora forum but  it is rather dated.  My understanding is that whatever worked for earlier versions of Ubuntu wouldn't work for Lucid because it has switched to GRUB2 while Fedora is still using GRUB.

 There are many places where one can find instructions for dual booting  windows and some versions of Linux but apparently there isn't much  information about dual booting different Linux distros. Moreover, it seems that dual booting between Windows and Ubuntu is a lot easier and more straight forward than to dual boot between Ubuntu and Fedora based on what I read. One would expect better compatibility within the Linux family  :confused:

Thanks for any help in advance.

---

### Post by wojox on 2010-07-22
It's easy bee. Just create your partition for Fedora. Let it install Grub to your MBR over writing Grub2. 

Boot into Fedora finishing the installation.

Then you'll want a Live-CD of Ubuntu to reinstall [Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") 

Once that done you can boot into Ubuntu and run 

```
sudo update-grub2
```

And it will find your Fedora partition and add it to Grub2. :D

---

### Post by beew on 2010-07-22
Thanks, will try that out.:p

---

### Post by moore.bryan on 2010-07-22
You could also just install Fedora to a new partition and have it install grub-legacy onto that partition. In Ubuntu, run "sudo update-grub2" and it'll pick-up your new Fedora install.

---

### Post by ubudog on 2010-07-22
> **wojox said:**
> It's easy bee. Just create your partition for Fedora. Let it install Grub to your MBR over writing Grub2. 

Boot into Fedora finishing the installation.

Then you'll want a Live-CD of Ubuntu to reinstall [Grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") 

Once that done you can boot into Ubuntu and run 

```
sudo update-grub2
```

And it will find your Fedora partition and add it to Grub2. :D

Awesome. Thanks.  I was looking for this for a long time.

---

### Post by wojox on 2010-07-22
No problem ubudog. I guess I should have read the Ubuntu-Lovers group I'm part of you started and could have helped you earlier.

---

### Post by ubudog on 2010-07-23
All that counts is that I have it now.  Thanks!

---

### Post by beew on 2010-07-23
Hi,

I have Ubuntu already installed, my installation has a separate /home partition to store data. I am wondering if it is possible to dual boot with Fedora in such a way that they share the same /home folder?

Thanks in advance for any advice.

---

### Post by tarps87 on 2010-07-23
My suggestion would be not to share the home partition, or at lest not with the same user on both installs.
My reasoning for this is based on when I tried it due to different programs and config files it soon became unstable an unmanageable, you could however share the folders in home, such as documents, music and I believe desktop will be fine to.

---

### Post by oldfred on 2010-07-23
+1 for tarps87 on sharing /home

Do far I only boot Ubuntu, but I have space for a couple more 25GB system partitions. I do not share /home but do share /data where I have moved all the data folders from /home and link them into /home in all my installs with a small script I made from a list of history copied to a bash file. My /home is now only 1Gb.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by beew on 2010-07-23
tarps87 and Oldfred,

Thanks for the warning and advice.:p

---

### Post by ubudog on 2010-08-04
EDIT: Oh crap, wrong forum.

---

