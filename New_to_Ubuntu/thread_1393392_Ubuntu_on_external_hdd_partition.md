---
title: "Ubuntu on external hdd partition?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by DasFlo on 2010-01-29
Hey everyone,

I'm new to the world of Ubuntu and Linux.
I successfully installed Ubuntu Netboox Remix (9.10) on my eeepc last night. 
I was also quite proud of myself when I managed to shut it down via console. :P

Anyways, I now would like to install Ubuntu on a external 1TB HDD I got today.
HOWEVER, I still want Windows to be able to see and use the 900gigs of the HDD that won't be reserved for Ubuntu. 

Could someone please point me to a guide that gives detailed instructions on how to do something like that? If there is no such guide, I'd of course also be thankful for any instructions you guys could come up with!

Thanks
Flo

---

### Post by mikewhatever on 2010-01-29
Windows will be able to use out of the box, whatever is not formatted as linux file system, so, I don't think there is anything to do here. As for the installation, it should be exactly the same as if that was an internal hdd. The only difference is where to install GRUB, the boot loader. The default location is hd0, the MBR of the first hdd, and it doesn't suite your purpose. You have to choose a different location, for example hd1.

---

### Post by Nedrah on 2010-01-29
Thanks!
You see, my problem is that I don't know how to set up the partitions in such a way that only 100GB are formatted with the linux file system while 900GB remain ntfs. I also do not now how to change the installation hdd for grubs. I don't want to risk messing something up and ending up being unable to boot into win7 (which I *have* to use for some things).

---

### Post by audiomick on 2010-01-29
Hi.
There are a number of links here
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

which look like they could help you along.

---

### Post by manothi on 2010-01-29
you can use a hiren boot cd or any other bootable disk management application to create the two partitions without messing up anything.

check this link for hiren info and howtos:[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

good luck

---

### Post by mikewhatever on 2010-01-29
> **Nedrah said:**
> Thanks!
You see, my problem is that I don't know how to set up the partitions in such a way that only 100GB are formatted with the linux file system while 900GB remain ntfs. I also do not now how to change the installation hdd for grubs. I don't want to risk messing something up and ending up being unable to boot into win7 (which I *have* to use for some things).

Ah, I thought installing on your eeepc had been somewhat educational. Anyway, there are too many variable to find a detailed howto for you exact setup. Generally speaking, you shrink the existing ntfs partition, and then use the unallocated space to install Ubuntu. In order to deal with GRUB, press 'Advanced ...' button ([-->image<--]("http://farm3.static.flickr.com/2494/4082797551_bbef800cf8.jpg")), and replace the default with hd1.

Check out the link below for a good installation guide.

[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)

---

