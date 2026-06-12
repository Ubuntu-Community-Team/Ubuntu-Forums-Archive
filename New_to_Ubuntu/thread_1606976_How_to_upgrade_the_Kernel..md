---
title: "How to upgrade the Kernel."
date: 2010-10-27
forum: New to Ubuntu
---

### Post by Jetso on 2010-10-27
I have Linux kernel 2.6.35-22, I saw mention of a 2.6.36 kernel out, and on Linux.org. So I was wondering: How you update it?

---

### Post by rado1 on 2010-10-27
Best way is to wait until it's shown in your upgrade manager. Than you know that it's save to update. If you have litlle experience with linux, do not try to upgrade kernel by yourself.Update manager will give you the stabile version.

---

### Post by coffeecat on 2010-10-27
If you are running the 2.6.35 kernel, you must be running 10.10/Maverick. Maverick will always have the 2.6.35 kernel in the main repository so it won't appear in regular updates. It might appear in backports or you could install it yourself manually, but why do you want the 2.6.36 kernel? Do you have hardware for which there are no drivers in the 2.6.35 kernel?

I see you have 'Ubuntu Development Release' in your personal profile. The best way to use the 2.6.36 kernel is to get involved with alpha testing of Natty Narwhal once it reaches alpha. You can upgrade to Natty already but unless you are an experienced user, there's not much you can do at the moment. Besides, the Ubuntu 2.6.36 kernel is at the -0 stage at the moment, so it's best to wait a bit.

By the way, in future please state which version of Ubuntu you are using when posting support threads, rather than leaving people to do detective or guesswork. With this post it was obvious, but if you want relevant help, give relevant information. **Edit:** Oops, sorry Jetso. Didn't notice it in your sig first time around.

---

### Post by amjjawad on 2010-10-27
> **coffeecat said:**
> By the way, in future please state which version of Ubuntu you are using when posting support threads, rather than leaving people to do detective or guesswork. With this post it was obvious, but if you want relevant help, give relevant information.

You could add that from your **User CP**.
If you check what's written under my avatar, you'll see:

Join Date: Oct 2009
  				 Location: Shawshank
  				 	  					Beans: 375 				
 ** 			       Ubuntu 10.04 Lucid Lynx**

---

### Post by rado1 on 2010-10-27
well amjjawad i thought that we're talking about jetso. In his profile is nothing about OS or his problems, so replay from coffeecat is good.

---

### Post by amjjawad on 2010-10-27
> **rado1 said:**
> well amjjawad i thought that we're talking about jetso. In his profile is nothing about OS or his problems, so replay from coffeecat is good.

And I post that for jetso not for coffeecat.

It's called "QUOTE TAG" for a reason ;)
I'm trying to explain to jetso how to add this info to his profile so every time he starts a thread, no one would ask him about his version.

---

### Post by amjjawad on 2010-10-27
> Dell Inspiron 1525 Running Ubuntu 10.10 and Windows Vista. Intel Celeron  2.00 GHZ, 3 Gb of RAM, 160 GB Samsung hard drive. Broadcom BCM4312  Network connector. 			

I'm not sure whether this was already there or not?!

---

### Post by rado1 on 2010-10-27
I do apologise to you ammjwad, didn't understood.
I'm sorry, my intencions were good, i hope you understand.

---

### Post by amjjawad on 2010-10-27
> **rado1 said:**
> I do apologise to you ammjwad, didn't understood.
I'm sorry, my intencions were good, i hope you understand.

Oh come on, no need to apologize, I totally understand :)

---

### Post by Warren North on 2010-10-27
I have learned to to wait a short while for upgrades.
I even wait a few weeks before I get an update.
I used download the latest of everything until I got burned.

---

### Post by lavinog on 2010-10-27
Another thing to consider is that the newer kernels may not be compatible with the ubuntu patches (like ureadahead)
So you might have to give up some ubuntu features if you use the latest kernel.

---

### Post by coffeecat on 2010-10-27
> **amjjawad said:**
> And I post that for jetso not for coffeecat.

It's called "QUOTE TAG" for a reason ;)

Indeed, but for a moment I thought you were responding to  me since you quoted me. It can be ambiguous.

What I like to do when quoting someone other than the OP, but posting a message to the OP is something like:

> [quote="Santa Claus"]Ho, ho, ho! What would you like for Christmas?

@OP's-name, compliments of the season from me too.[/quote]

Anyway, I see that the OP has put 10.10 in their sig which I totally missed first time around so apologies for that, and we seem to be telling each other how to use the forum. I wonder what Jetso makes of all this. :p

---

### Post by halj32 on 2010-10-27
first you have to add this "ppa:kernel-ppa/ppa" to your software sources
also this gpg key

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXXeOgEEAL13aaPSn+5Ad/Ob0g+2kq8vxIRefPI8MOeio2/8KacAJDJj6CKsP5CEPz5J
khrLLAY+H0KMwbQhzC2IUtVcpqMp6xHS1S4PP08phLnwebtqusycwH687rCQyRCJpNDpFScO
uI9IiIwUbjnOXVSf1r9uoEFUsAJru7/L4TVqCkCBABEBAAG0I0xhdW5jaHBhZCBQUEEgZm9y
IFVidW50dSBLZXJuZWwgUFBBiLYEEwECACAFAkl13joCGwMGCwkIBwMCBBUCCAMEFgIDAQIe
AQIXgAAKCRCoJnljSEsETxmvA/9hQCxrXCcdrdcVFnJQmW8zFcgzbIFtJGnZvocIpGvQ5E6O
cUy7kQnIoICbaQlydy6Las3vLKqN8M55nZM1LSlACiQmeWvZwIWjrbyIxPYuYJDLbs+jICfj
6azir6Ag7tEAk+nzzKHzbFK6ZhkJve1TGrWeMvKovi7KVTZvJtIt7A==
=S40k
-----END PGP PUBLIC KEY BLOCK-----

or get it from their site
then do an update
then you will find it in Synaptic
Im using the 2.6.35-1 (generic) on a Dell laptop I 1525
everything works good.. only a little problem with dual monitors some programs turn on both

goodluck

---

### Post by amjjawad on 2010-10-27
> **coffeecat said:**
> and we seem to be telling each other how to use the forum. I wonder what Jetso makes of all this. :p

Hahaha, agreed :)

I missed his signature as well or perhaps he added it after he read our posts.

Anyway, hope he managed to fix his problem.

---

### Post by Quackers on 2010-10-27
2.6.36.1 is for Natty Narwhal I believe.

---

### Post by Jetso on 2010-10-27
> **Quackers said:**
> 2.6.36.1 is for Natty Narwhal I believe.

Haha, that was always in my signature... But I do admit that on the side where it shows what OS I use, I never changed it from "Development Release" when I was using the 10.10 beta. I think I will just wait until Natty is released then risk screwing anything up. Frankly, I may be good with computers,especially for my age, but I can also do a good job messing them up. ;) 

P.S Coffeecat, I don't mind that at all. You all were trying to help each other out, which is always a good thing.

---

### Post by amjjawad on 2010-10-28
> **Jetso said:**
> Haha, that was always in my signature... But I do admit that on the side where it shows what OS I use, I never changed it from "Development Release" when I was using the 10.10 beta. I think I will just wait until Natty is released then risk screwing anything up. Frankly, I may be good with computers,especially for my age, but I can also do a good job messing them up. ;) 

P.S Coffeecat, I don't mind that at all. You all were trying to help each other out, which is always a good thing.

Sorry Jetso, me and coffeecat missed that on your signature. It happens a lot especially when you have lots of active open tags and you're reading 10 threads or more at the same time. :)

I believe in one thing and I learned that in 10 or 11 years with Computers (I might be older but I got my first PC when I was 20). The more you mess/screw with things, the better and the faster you learn.
Anyway, don't want write off topics but don't worry about "screwing things" :)

So, what's your plan? are you going to wait the next release or what? I mean the next update :)

---

### Post by Jetso on 2010-10-28
Well I might get a new computer soon that I could mess with more, than the one I have now, which is my only one.

---

### Post by amjjawad on 2010-10-28
> **Jetso said:**
> Well I might get a new computer soon that I could mess with more, than the one I have now, which is my only one.

WOW, what a plan?! I didn't expect that :D

---

### Post by stormchaser2063 on 2010-10-28
interesting, i just upgraded to 10.10 on october 10th. so far very happy with maverick, 10.04 was good but my cricket wireless aircard sometimes acted real strange, sometimes had to boot into windows first and with maverick i dont have to so windows has left totally. also evolution wouldnt act right for me in 10.04 and works good in maverick. i have a 10.10 cd so i probably will upgrade to the next version when its released but if it doesnt work right ill go back to maverick. so far maverick is awesome!!:P

---

### Post by amjjawad on 2010-10-28
> **stormchaser2063 said:**
> interesting, i just upgraded to 10.10 on october 10th. so far very happy with maverick, 10.04 was good but my cricket wireless aircard sometimes acted real strange, sometimes had to boot into windows first and with maverick i dont have to so windows has left totally. also evolution wouldnt act right for me in 10.04 and works good in maverick. i have a 10.10 cd so i probably will upgrade to the next version when its released but if it doesnt work right ill go back to maverick. so far maverick is awesome!!:P

The First Golden Rule in OS World is: "No OS Is Perfect." :)

---

### Post by ibuclaw on 2010-10-28
> **Jetso said:**
> I have Linux kernel 2.6.35-22, I saw mention of a 2.6.36 kernel out, and on Linux.org. So I was wondering: How you update it?

There may be some ppas out there that have a 2.6.36 kernel built for Ubuntu. Xorg edgers is one of them, at the price of X drivers that may not be so stable.

For the ones who don't mind a bit of labour, there's always the [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158").

Regards

---

### Post by coffeecat on 2010-10-28
@Jetso, I wouldn't normally post this in the beginner's forum, but since you are clearly not averse to a bit of experimentation, I'll make this suggestion on the understanding that if you break your system, I take no responsibility. :p

Rather than upgrade to 11.04, you can simply run the 11.04/Natty kernel in Maverick. I've done it. [When the Maverick 2.6.35 kernel]("http://ubuntuforums.org/showthread.php?t=1586254") broke the Fn brightness key functions on my Sony Vaio laptop, I first of all installed the Lucid 2.6.32 kernel and, hey presto, they worked again. What I didn't say in that thread is that I also tried the 2.6.36.0 Natty kernel and got them working again with that kernel as well.

The procedure is simple. You download the deb packages for the 2.6.36 kernel and install them manually. I tried the 2.6.36-0 kernel which was current at the time but as Quackers points out, the 2.6.36-1 revisison is now current. I don't know whether it works in Maverick but I guess it will. If you want some more information, post back, and I'll post some links.

One disadvantage you must be aware of is that by doing this, upgrades to the 2.6.36 will not come through automatically. There will be many updates and patches to this kernel once Natty development gets underway properly, and you need these to make sure security patches are included.

---

### Post by Jetso on 2010-10-28
Mmmm, coffeecat:

You mention I may break my computer... How? I've taken alot of risks my laptop, and most of them can be fixed with re-installation of Ubuntu, so if worse comes to worse, I still have Windows... 0.0

---

### Post by Jetso on 2010-10-28
Natty may also work better with my wireless card, which currently only works when my laptop is charching....:confused:

---

### Post by coffeecat on 2010-10-28
> **Jetso said:**
> You mention I may break my computer... How? I've taken alot of risks my laptop, and most of them can be fixed with re-installation of Ubuntu, so if worse comes to worse, I still have Windows... 0.0

You're unlikely to break your computer, but you might break Ubuntu. :wink: And, as you say, if the worst comes to the worst...

> **Jetso said:**
> Natty may also work better with my wireless card, which currently only works when my laptop is charching....:confused:

That's an odd one. Have you started a support thread specifically for your wireless problem? Rather than try the 2.6.36 kernel in Maverick for this, I've a better idea. Install the package linux-backports-modules-wireless-maverick-generic. This is a metapackage which will pull in updated wireless modules (drivers) for your current kernel. You may find your wireless works better - or not as the case may be. I don't guarantee anything but it's worth trying.

By the way, you don't have to enable any special repositories for this. Despite the 'backports' in the name, it's in the main repository.

---

### Post by Jetso on 2010-10-28
Ya, I actually did but never got any responses... here it is, it goes into more detail: [here.]("http://ubuntuforums.org/showthread.php?t=1600955") Mmmm I guess it's worth a try. Where do I get the .deb files?

---

### Post by coffeecat on 2010-10-28
> **Jetso said:**
> Ya, I actually did but never got any responses... here it is, it goes into more detail: [here.]("http://ubuntuforums.org/showthread.php?t=1600955") 

There I go again, not looking at your sig! Since you've got a Broadcom card, you might want to look at this page. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It seems you can use either the STA or b43 driver for your card, so you might want to try the "other" driver from whichever you are using.

> **Jetso said:**
> Mmmm I guess it's worth a try. Where do I get the .deb files?

You don't go anywhere, except to System > Adminstration > Synaptic, but hold on the backports-wireless package for now. I don't think it will help. Have a look through that link first.

---

### Post by Jetso on 2010-10-28
I meant for the Natty Kernel? Or is that what you mean? You mentioned installing them "Manually" So I thought I had to get them somewhere.

---

### Post by coffeecat on 2010-10-28
> **Jetso said:**
> I meant for the Natty Kernel? Or is that what you mean? You mentioned installing them "Manually" So I thought I had to get them somewhere.

OK, on your own head be it. I do not recommend this, mostly because I don't think it will help your wireless problem, nor any other problem for that matter. You would do well to wait until Natty is in alpha (not long now) and help with testing instead. But if you are sure you really want to run the 2.6.36 kernel in Maverick please re-read what I said earlier and think about it. Particularly think about what I said about the 2.6.36 kernel not being automatically updated for you. Also - I take no responsibility for any problems this might cause, but I console myself with the thought that if you break your system, it will be a good learning experience for you. :wink:

This is the download link:

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

And these are the three packages you need to download:

linux-image-2.6.36-1-generic_2.6.36-1.7_amd64.deb
linux-headers-2.6.36-1_2.6.36-1.7_all.deb
linux-headers-2.6.36-1-generic_2.6.36-1.7_amd64.deb

They are for a 64-bit system. If you have a 32-bit system, for the first and third packages you need to look for the same packages, but with _i386.deb at the end. The second package is fine for 32 and 64 bit systems.

Install them by double-clicking on each in turn, or open a terminal, cd to the directory where you downloaded them to, and...

```
sudo dpkg -i linux*deb
```

Be warned, the grub menu will default to the 2.6.36 kernel now.

---

### Post by Jetso on 2010-10-28
I completely understand about breaking Ubuntu... I'll have to think about... I might just wait for the alpha of Natty... If I do wait for Natty, where do you get the Alpha? I've never seen anything about Natty on Ubuntu.com? I'm sorry if I'm asking alot of questions, but you've been alot of help :P:P:P

Edit: I have a 32 bit system, so thanks for the warning, I'll add that to my sig. Haha

---

### Post by amjjawad on 2010-10-29
> **Jetso said:**
> I'm sorry if I'm asking alot of questions, but you've been alot of help :P:P:P


This place for asking questions so don't be sorry :)

Don't forget to mark this thread as SOLVED in case it's :D

---

### Post by coffeecat on 2010-10-29
> **Jetso said:**
> I might just wait for the alpha of Natty... If I do wait for Natty, where do you get the Alpha?

Before I tell you that, there's another thing for you to think about. You are new to Ubuntu, but that doesn't mean you are not welcome to test the alpha of the next release. What you must be aware of is that, even for experienced users, the early stages of the development are unstable and things do break. For an inexperienced user things are likely to break badly. But that's not a problem; it's all part of the fun of testing a pre-release.

However, that leads to a serious point. It is advised time and time again on this forum and by the Ubuntu dev team that if you test a development version of Ubuntu, you are testing a development version of Ubuntu - that is, you are looking for bugs that can be dealt with. You **should not** rely on your testing pre-release installation of Ubuntu for day-to-day work. And what that means for you is that you would need to create another partition on your machine for Natty testing. Keep your Maverick partition (with the 2.6.35 kernel :wink:) for ordinary use and for getting more acquainted with this fascinating operating system.

That, of course, means that you would need to re-partition your hard drive. You may or not not be confident to do that and re-partitioning could itself lead to breakage if you are unlucky, so there's plenty for you to think about.

In the meantime, here is the release schedule for Natty:

[https://wiki.ubuntu.com/NattyReleaseSchedule](https://wiki.ubuntu.com/NattyReleaseSchedule)

I'm running Natty on one of my laptops just now, but that is only because I wanted to be ready for when ordinary users such as myself can be useful. The fun really starts in December.

I won't post any download links partly because you need to think on all this, and partly because there is no ISO for Natty yet. If you really, really, really want to try Natty in December, people will inevitably be posting links so they should be easy to find. In the meantime, even though we may not have achieved anything tangible in this thread, I hope you've learnt a thing or three, which is perhaps more important, and I for one have enjoyed participating.

Good luck!

---

### Post by amjjawad on 2010-10-29
I like your last post a lot, Coffeecat :)

---

### Post by Jetso on 2010-10-29
> **coffeecat said:**
>  You **should not** rely on your testing pre-release installation of Ubuntu for day-to-day work.  
Good luck!

Makes perfect sense.

> The fun really starts in December.

I'm out of room on my hard drive, and I need an external, so I'll install it on that, in december!

---

