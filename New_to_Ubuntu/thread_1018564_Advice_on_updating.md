---
title: "Advice on updating"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Dave.YNA on 2008-12-22
Hello All!
         I am just looking for some advice on what people think will be the best course of action for updating my toshiba nb100 netbook. It came with a tweaked version of 8.04 on it which works pretty well. 

I am currently happy with how it is running so I don't see a need to upgrade to 8.10 in the short term but as time goes by, I am more likely to want to upgrade to get the latest experience and features. The problem is that I am worried most things will stop working if I do a fresh install like most people recommend. 

General tips and tricks to upgrade as painlessly as possible would be appreciated and im sure will help others in similar situation.

I look forward to the responses

---

### Post by LowSky on 2008-12-22
I have done the update rout over fresh install, and can say it does work, for some. I don't know the inner workings of your laptop but it could be problematic. 8.04.1 is supported for a good long time, so you wont miss out on too much. Most of the applications you can upgrade  by enabling the backports option in software sources (to be fair some people have had issue with back ports not working as well).

My best suggestion is to start learning everything you can, know how to use the command line, what application you use all the time and how to install the updates by using the source code or packaged .deb files you find online.

---

### Post by sajnox on 2008-12-22
An easy way to know if it's going to work or not is booting with a LiveCd and check if all the hard works properly. If so, you can run the update process.

But, as I alaways say "Dear User, if you don't know precisely why you are updating. Don't do it"

---

### Post by Nepherte on 2008-12-22
If you find it more important that everythings runs smoothly as it is now rather than newer software and a possible breakage, stick to 8.04. Ubuntu 8.04 is a Long Term Support version meaning that it will get security updates over a longer period than a normal version (8.10, for example). Sit out this period and upgrade only when you really have to. By that time, you might have become a lot more experienced and more than capable of dealing with breakage.

---

### Post by NewJack on 2008-12-22
When I first started using Ubuntu, I felt the need to upgrade to the newest version right away.  As time has gone on though, I have changed that way of thinking.  If my current install does everything I need, why upgrade.  Unless there are some major improvements to the OS or to the programs that it comes with there is no reason to.  

Personally, I'm holding onto Hardy until Jaunty rolls around.  Hopefully, it will give me a reason to upgrade :)

---

### Post by namdung on 2008-12-22
> **Dave.YNA said:**
> Hello All!
         I am just looking for some advice on what people think will be the best course of action for updating my toshiba nb100 netbook. It came with a tweaked version of 8.04 on it which works pretty well. 

I am currently happy with how it is running so I don't see a need to upgrade to 8.10 in the short term but as time goes by, I am more likely to want to upgrade to get the latest experience and features. The problem is that I am worried most things will stop working if I do a fresh install like most people recommend. 

General tips and tricks to upgrade as painlessly as possible would be appreciated and im sure will help others in similar situation.

I look forward to the responses

Firstly there is difference between updating and upgrading. You update a software to a newer version or new patches and you upgrade your Linux version to a new one eg. 8.04 to 8.10.

I second the others on sticking to Ubuntu Hardy which is currently 8.04.1. This is a LTS version which is much stable. The next version 8.04.2 is coming out in Jan 09. Intrepid and the other versions may have new features but may contain more bugs. I myself downgraded to Hardy after issues with Intrepid. 

You may want to try out the new version with a Live CD or using Virtualization software like virtualbox etc to be sure before upgrading.

---

### Post by Xiong Chiamiov on 2008-12-22
> **LowSky said:**
> My best suggestion is to start learning ... how to install the updates by using the source code or packaged .deb files you find online.
Hooray for dependency hell!

Personally, I'd clone the partition, run the upgrade on one of them, then ditch the old if the new works, and vice versa.  I've always got lots of space hard drive space, though.  If it works for you, don't mess with it.

---

### Post by HermanAB on 2008-12-22
Don't fix it if it ain't broke.  Linux is pretty stable and secure.  I update  most of my machines about once a year, some of them once in 3 years.

---

### Post by kansasnoob on 2008-12-22
> **Dave.YNA said:**
> Hello All!
         I am just looking for some advice on what people think will be the best course of action for updating my toshiba nb100 netbook. It came with a tweaked version of 8.04 on it which works pretty well. 

I am currently happy with how it is running so I don't see a need to upgrade to 8.10 in the short term but as time goes by, I am more likely to want to upgrade to get the latest experience and features. The problem is that I am worried most things will stop working if I do a fresh install like most people recommend. 

General tips and tricks to upgrade as painlessly as possible would be appreciated and im sure will help others in similar situation.

I look forward to the responses

So far, after 4 Hardy to Intrepid dist-upgrades, my success rate is 100%. That's double what it was doing Gutsy to Hardy dist-upgrades.

But IMHO I would start by burning an Intrepid Live CD. then try the Live CD (of course choosing "Try Ubuntu without any change to your computer") from the boot options.

If it seems to work well with your hardware then I'd go to System > Administration > Partition Editor and make sure no "locks" are shown. It's common for SWAP to be "on" so you'll have to click the swap partition and then "tick" swapoff.

Then shrink *some* partition to allow about 10 GB to install 8.10. That way you can give it a true "test-drive".

If you run the Live CD and decide to install post a screen shot of Gparted (aka: Partition Editor) and I'll give you some advice on partitioning. Or, given my success with Hardy to Intrepid upgrades you could just try a dist-upgrade!

One thing! Always make sure you create backups of important data!

Even the best procedures can go wrong!

---

