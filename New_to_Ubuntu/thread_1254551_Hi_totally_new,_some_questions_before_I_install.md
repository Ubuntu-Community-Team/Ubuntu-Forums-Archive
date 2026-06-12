---
title: "Hi totally new, some questions before I install"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by kronos262 on 2009-08-31
I downloaded the Netbook remix, as I am about to recieve my New MSI Wind U100 Netbook, in about a half hour.
 
I been looking at all the dual boots, and was wondering, if I install Ubuntu, do I have to reinstall windows xp?
 
I never done a dual boot before so this will be my first time. 
 
Also my only experience with linux, was Yellow Dog on the PS3. I am looking to learn Linux more so I can eventually just use that, so I thought with my new netbook it be the perfect oppurtunity.

---

### Post by diablo75 on 2009-08-31
I've not used the netbook remix edition so I can only assume the install is identical or very close to how it works with the traditional versions.  And that means that when you do the install, it will offer you the option of resizing your windows partition down to make space for Linux and install GRUB after that so you can dual-boot.  It's pretty easy and effortless... though I have, on some occasions, had a problem with the Guided partitioning with hard drives that have more than one partition already on them (particularly hard drives that have a "hidden" recovery partition for restoring the original factory software).  If that ends up being the case, manual partitioning isn't very hard to do but I would google how to go about doing that if it comes down to it.  At the very least, you'd want to create a root partition, and a swap partition.

---

### Post by drs305 on 2009-08-31
kronos262, Welcome to Ubuntu and the Ubuntu forums.

Just a word of advice if you decide to chose to install Ubuntu "side by side" with Windows (Step 4, Partitioning). You must click on the bottom partitioning depiction and use the slider to increase the size of the Ubuntu partition. If you don't it will allocate only 2.3GB, which is not enough. It's a reported bug.

Here is a post detailing how to avoid this:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

---

### Post by kronos262 on 2009-08-31
Cool thanks.
 
That is whay I figured but I wanted to make sure. 
 
I was watching a lot of youtube videos last night lol. 
 
I have manually partitioned drives before (my externetal HDD) so I know whow to do that. 
 
I am debating on if I want to do the MAC OS X on it too. I read it runs really well on the MSI wind.
 
Which UPS just dropped off lol.

---

### Post by bodhi.zazen on 2009-08-31
> **kronos262 said:**
> I downloaded the Netbook remix, as I am about to recieve my New MSI Wind U100 Netbook, in about a half hour.
 
I been looking at all the dual boots, and was wondering, if I install Ubuntu, do I have to reinstall windows xp?
 
I never done a dual boot before so this will be my first time. 
 
Also my only experience with linux, was Yellow Dog on the PS3. I am looking to learn Linux more so I can eventually just use that, so I thought with my new netbook it be the perfect oppurtunity.

The netbook remix is available to run "live" and I suggest you try it before you install it.

The major change in UNR is actually the user interface, there is not much under the hood if you will (ie no specific kernel modifications or optimizations for netbooks).

There are a few respins available that offer these optimizations and of all the options I have had the best success with [http://www.jolicloud.com/](http://www.jolicloud.com/)

I find a standard installation of Xubuntu is preferable to me, so try before you install.

Other then that, yes you can dual boot without any problem.

Do you know how to install Ubuntu ? Repartition your hard drive ? Boot from a usb drive (use unetbootin) ?

[GraphicalInstall - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by LewRockwell on 2009-08-31
[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by kronos262 on 2009-08-31
So how do I run it live?
 
I put the img on my flash drive using the tutorial. 
 
When I click the WUBI icon, nothing happens.

---

### Post by LewRockwell on 2009-08-31
> **kronos262 said:**
> So how do I run it live?
 
I put the img on my flash drive using the tutorial. 
 
When I click the WUBI icon, nothing happens.

our personal opinion and advice...use the wubi-buntu-landmine at your own risk

backup, Backup, BACKUP

(we would assume you've thoroughly researched "ubuntu" and "wubi"...)

.

---

### Post by kronos262 on 2009-08-31
> **LewRockwell said:**
> our personal opinion and advice...use the wubi-buntu-landmine at your own risk
 
backup, Backup, BACKUP
 
(we would assume you've thoroughly researched "ubuntu" and "wubi"...)
 
.
 
 
I figure out how to run it live, so I am doing that now. 
 
So if I have anymore questions I will come back.

---

### Post by kronos262 on 2009-08-31
Totally not a fan of the remix.
 
I think I rather go with the full version, as it seems really not customizable.

---

