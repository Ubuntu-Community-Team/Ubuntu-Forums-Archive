---
title: "Ubuntu 10.10 - Full install with updates + downloads"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by ebun2 on 2011-04-12
Hi there,
I am an absolute non tech savvy newbie and just beginning to enjoy Ubuntu. I have installed Ubuntu 10.10 on my PC simultaneous to its current OS (Windows7) so I am presently on dual boot option.

After reviewing some forums I have personalised the Ubuntu desktop with some downloads such as themes, apps like Docky etc. In addition I have almost completed the updates (which auto prompted) via "Updates Manager" (this I did with much difficulty using my HSPA connection which was very time consuming) :-k

Now I am planning to do a full installation (that is to get rid of Windows7) and make Ubuntu my default and only OS. My question is .... Is there any way to copy/back up what I have already installed/updated so that I do not have to go download/upload the same stuff back again after the new installation? 

Appreciate your concerns and advise, thanks all in advance ):P

---

### Post by sanguinoso on 2011-04-12
There should be some in /var/cache/apt/archives/. However, unless you set your system to cache all the downloaded files, all the installed packages won't be in there. However, it could save you some download time with the packages that are.

---

### Post by cbowman57 on 2011-04-12
My  recommendation, shrink your Win 7 partition down to about 20Gb and you can still make Ubuntu your primary OS.

Sometimes it's handy to have Windows if you're trying to eliminate linux as the culprit if you run into a problem.

YMMV

---

### Post by Miljet on 2011-04-12
This is a personal preference. When I decide to finally get rid of Windows several years ago, I kept the partition and reformatted it as EXT4. Then when a new version of Ubuntu came out, I installed it in the old Windows partition. That way I can fully check out the new Ubuntu version while still keeping the old version in case of problems.
The next time a new version comes out, I install it where the oldest Ubuntu  was.

---

### Post by Mark Phelps on 2011-04-12
IF you decide to keep Win7 and shrink it, be sure to use the Win7 Disk Management utility to do that.  Do NOT use GParted or any other Linux utility to do that.  However, do not be surprised if Disk Management doesn't let you shrink it much.

---

### Post by Ghost_Mazal on 2011-04-13
Look into remastersys. It's the best for this type of thing. It makes a re-installable .iso that you can burn and install with. And all the apps and updates that was in your system is there.

I've used it a few times now and find it is the best for re-install with everything already there.

Obviously you need to make sure that you backup your /home and other important data first to put that back after the install.

---

### Post by el_koraco on 2011-04-13
How did you install it, on the hard drive or using the Wubi installer (installing it inside Windows)?

---

### Post by kn0w-b1nary on 2011-04-13
Remastersys works, but you can just reformat the windows partition with gparted and just use that partition for storage.

---

### Post by ebun2 on 2011-04-22
Thanks everyone for the valuable feedback, appreciated ! cheers ;)

---

