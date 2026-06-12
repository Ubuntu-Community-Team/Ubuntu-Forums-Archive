---
title: "ATI Card in Karmic"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by jnmjr on 2010-04-08
Hey All....I've swithched my graphics card from NViadia AGP to an ATI Radeon 9200 Pro AGP (I've an older system) due to being unable to completely free my Ubuntu OS from random freezes, over the last month they haven't being too bad, but for the last 3 days it's back to being unbearable.... I want to give this ATI card a chance but I haven't found drivers in Synaptic, if any one uses this card or similar could you post on what drivers you use and your experience , good or bad, or any info you may want to share...THX

---

### Post by Mark Phelps on 2010-04-08
That old an ATI card does not have any ATI restricted drivers that work with current versions of Ubuntu.  ATI dropped Linux support for that card, and lots of others, over a year ago.

If you download drivers from ATI or force driver installs using EnvyNG, you will only trash your display and have to remove them.

When you boot Ubuntu, it will install the default open-source ATI drivers -- which are the only drivers available now for your card.

---

### Post by tom.swartz07 on 2010-04-08
+1 with the guy above me.


I have a 3 year old computer, with an ATI Radeon X1270 and there are absolutely zero drivers and no support for Linux. Majority of the features for the card are lost on Windows 7 too. 


For the time being, just stick with the default drivers from the kernel. In the future, dont buy anything from ATI. haha.


It sucks, I know, but unfortunately, thats just how it is I guess...

---

### Post by 3rdalbum on 2010-04-08
If the freezes are getting worse, then I think you've got bad RAM. Hey, I was quick to blame my Nvidia card... but when I ran a memory benchmark in Phoronix Test Suite and the computer crashed, that's when I took out two of my RAM sticks and the system rarely crashed again.

ATI's older cards don't have proprietary drivers anymore; you'd be stuck with the open-source driver which is fairly limited.

So, if I were you, I'd run Memtest from the GRUB menu. Run it overnight. If the computer has crashed by the time you get up in the morning, or if it reports any errors, then find out what pair of RAM sticks is faulty and bin them. If you only have one pair, then that makes it easy.

---

### Post by jnmjr on 2010-04-08
> **tom.swartz07 said:**
> +1 with the guy above me.


I have a 3 year old computer, with an ATI Radeon X1270 and there are absolutely zero drivers and no support for Linux. Majority of the features for the card are lost on Windows 7 too. 


For the time being, just stick with the default drivers from the kernel. In the future, dont buy anything from ATI. haha.


It sucks, I know, but unfortunately, thats just how it is I guess...


Thanks both for your input, fortunately I didn't go out and buy this card it's a leftover from another system I parted out, it's very disappointing that nothing can be done, I don't play games or any of that but the way this runs with the default drivers leaves much to be desired, I've been struggling with the Nvidia situation almost since I began using Ubuntu back in Dec/09, it has become a very frustrating issue to say the least, though I don't particularly relish the thought of buying another video card, I'm willing to put out the cash if I can resolve the issue, PCI, AGP does not make a difference since I have room for either, as long as it's inexpensive and has no driver issues, I've looked in some of the websites and seen a few older Nvideas  below $40 shipped, the one I own now is a GeForce 6200a, and I guess qualifies as an older model, which I have not being able to run quite successfully, again I ask for suggestions or personal experiences which can help me with this situation......THX

---

### Post by jnmjr on 2010-04-08
> **3rdalbum said:**
> If the freezes are getting worse, then I think you've got bad RAM. Hey, I was quick to blame my Nvidia card... but when I ran a memory benchmark in Phoronix Test Suite and the computer crashed, that's when I took out two of my RAM sticks and the system rarely crashed again.

ATI's older cards don't have proprietary drivers anymore; you'd be stuck with the open-source driver which is fairly limited.

So, if I were you, I'd run Memtest from the GRUB menu. Run it overnight. If the computer has crashed by the time you get up in the morning, or if it reports any errors, then find out what pair of RAM sticks is faulty and bin them. If you only have one pair, then that makes it easy.

Thank you for your response, I would consider it a possibility if I would have the same problem in Windows, but it runs flawlessly there, I would think bad memory would not prejudice one OS over the other.

---

### Post by clhsharky on 2010-04-08
HI jnmjr

How do you know its a radeon driver problem as they are more stable than fglrx drivers for most users. Have you looked in the Logs 'System/Administration/Log File Viewer'at messages or debug? I believe its more likely to be a app, firefox,flashplayer,or something like that.
ATI still supports your chip 'R200' in the radeon driver.


Sharky

---

### Post by cascade9 on 2010-04-08
> **jnmjr said:**
> Thank you for your response, I would consider it a possibility if I would have the same problem in Windows, but it runs flawlessly there, I would think bad memory would not prejudice one OS over the other.

Probably not, but stranger things have happened. 

Aside from other random weirdness, if you are running windows on one drive, and linux on a different drive, it could be caused by errors on the drive with linux on it, or the cable.

---

### Post by jnmjr on 2010-04-08
> **clhsharky said:**
> HI jnmjr

How do you know its a radeon driver problem as they are more stable than fglrx drivers for most users. Have you looked in the Logs 'System/Administration/Log File Viewer'at messages or debug? I believe its more likely to be a app, firefox,flashplayer,or something like that.
ATI still supports your chip 'R200' in the radeon driver.


Sharky

You misunderstand, it runs Ok with the default Ubuntu drivers, but it's very slow, according to the above posters there's no support, so I'd rather use something that has some sort of support, as far as logs and apps, I've been fighting this for the better part of 3-4 months, I haven't been able to pinpoint it so far, I make some changes as per other research and suggestions and sometimes I can get it to work (Nvidia) for a few days then whatever happens and I'm almost back to square one. I know the new OS is coming out soon and I'm hoping an upgrade may resolve this issue. THX

---

### Post by clhsharky on 2010-04-08
HI jnmjr


Go here and read for your self

 Linux Graphics / X.Org Drivers
[http://www.phoronix.com/forums/forumdisplay.php?f=46](http://www.phoronix.com/forums/forumdisplay.php?f=46)

Bridgman is a ATI/dev open source manager and see who is more knowledgeable. Other devs hang out there also.

Also
[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

You can see there still working on you chip.

I apologize if I wasn't any help on you problem.

Sharky

---

### Post by jnmjr on 2010-04-08
> **cascade9 said:**
> Probably not, but stranger things have happened. 

Aside from other random weirdness, if you are running windows on one drive, and linux on a different drive, it could be caused by errors on the drive with linux on it, or the cable.

That same thought occurred to me a while back, I took the Linux drive out and had it checked by a PC shop it checked OK, I also changed the cable, I even had the motherboard looked at by a friend who's a PC and electronics wiz, funny like you said, he also said Linux acts weird (he likes win), I don't give up easily  and I like Linux, there're hundreds of thousands if not millions who use Linux with little trouble, sooner or later we'll get to the bottom of this, in the meantime I'll continue to use both OS's as necessary........THX

---

### Post by jnmjr on 2010-04-08
> **clhsharky said:**
> HI jnmjr


Go here and read for your self

 Linux Graphics / X.Org Drivers
[http://www.phoronix.com/forums/forumdisplay.php?f=46](http://www.phoronix.com/forums/forumdisplay.php?f=46)

Bridgman is a ATI/dev open source manager and see who is more knowledgeable. Other devs hang out there also.

Also
[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

You can see there still working on you chip.

I apologize if I wasn't any help on you problem.

Sharky

No need to apologize, you have pointed me in a new direction with these ATI  drivers, and I thank you for it, I will be reading up on this as soon as I free some time up.

---

### Post by Mark Phelps on 2010-04-08
>  ...I know the new OS is coming out soon and I'm hoping an upgrade may resolve this issue. 

While there are improvements in the open-source ATI drivers already being worked into 10.04, I would not be surprised if these are for the newer cards only. 

Until the drivers are finalized and the release notes made available, we won't know for sure which ATI chipsets will actually see improvements.

---

### Post by jnmjr on 2010-04-08
> **Mark Phelps said:**
> While there are improvements in the open-source ATI drivers already being worked into 10.04, I would not be surprised if these are for the newer cards only. 

Until the drivers are finalized and the release notes made available, we won't know for sure which ATI chipsets will actually see improvements.

After doing some research as suggested by Sharky, I think I'm going to agree with your post Mark, though I'm far from techno-savy the impression I got is that the ATI open source drivers are not up to snuff yet, mind you lots of stuff went over my head but that's the feeling I got, I'm going to wait for 10.04 upgrade before I do anything else, this ATI card is working so far without any freezes, though lethargic in Ubuntu it works well enough in XP so I'll deal with it in the meantime, I'll also try the GForce with the new upgrade, see what happens..... I want to thank all of you again for your suggestions and support.....THX

---

