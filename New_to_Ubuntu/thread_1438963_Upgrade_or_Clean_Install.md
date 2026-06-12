---
title: "Upgrade or Clean Install?"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by KdotJ on 2010-03-25
Hey people,
What's the differences (if any) between upgrading from within ubuntu and from performing a clean install from a CD? Apart from keeping your files and programs? I've never upgraded before so I wouldn't know what gets kept and what doesn't. My question really is, if I was to upgrade via inside ubuntu, would it be a full upgrade with everything new? 

Sorry if this a n00b question lol

---

### Post by cogier on 2010-03-25
From which version to which version?

For example upgrading from 9.04 to 9.10 will not install the ext4 file system but a fresh install will.

I think the best way is a fresh install if possible.

---

### Post by clhsharky on 2010-03-25
HI

I have done a upgrade and clean install on every release since 7.04. A clean install has always been better, and faster in the long run. Having to diagnose, fix problems and clean out config files left behind that some times don't work right. Upgrade and fixes can teach you about your system, if your interested.

Going from 9.04 to 9.10 you will loose out on Grub2 and ext4 file sys. although they can be installed or converted. So no to everything new.

Sharky

---

### Post by KdotJ on 2010-03-25
Hey thanks for the replies guys,

Im talking about upgradin got 10.04 Lucid, when it becomes a stable release. I think im going to go with a clean install, purley because everything will be fresh. Its just a bit of a pain getting it all back to how you want it, but worth it in the long run i guess....

---

### Post by Zzl1xndd on 2010-03-25
I recommend a clean install as well (with any OS). Also you may wish to set a separate home partition when installing. Then you can do a clean install each time and not mess with any of your files. That being said you should always have a back up in case something goes wrong.

---

### Post by KdotJ on 2010-03-25
Yeah I always make sure to back up. In the past (during my Windoze days) I always performed a clean install. The seperate home partition sounds like a good idea though.

o/t @ tweakedenigma**: **I like your quote in your sig :p

---

### Post by cobb_cruiser on 2010-04-05
> **tweakedenigma said:**
> I recommend a clean install as well (with any OS). Also you may wish to set a separate home partition when installing. Then you can do a clean install each time and not mess with any of your files. That being said you should always have a back up in case something goes wrong.

k - I'm a n00b...  about the separate home partition recommendation:  can I create it with my existing data files when I install Lucid (I currently have Karmic Koala)?  If so, how.  If not, I guess I need to save everything on a disk and reload?  Or are there any other options?  Thanks!

---

### Post by da burger on 2010-04-05
This page shows you how to add a separate /home partition to a current install without losing files.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
I believe on a clean install there is an option to make one.

---

### Post by Paqman on 2010-04-05
If you're using standard Ubuntu packages from the repos then there's no reason why an upgrade shouldn't go smoothly. I've done quite a few now, and these days they just work.

During the upgrade process any 3rd-party repos (eg: Google repo, PPAs, etc) will get disabled, so you'll need to look into updating those once you've finished the upgrade. Also if you've been compiling your own software then your system could well b0rk, which is one of the main reasons why compiling your own software should be avoided.

---

### Post by warfacegod on 2010-04-05
> **KdotJ said:**
> Hey thanks for the replies guys,

Im talking about upgradin got 10.04 Lucid, when it becomes a stable release. I think im going to go with a clean install, purley because everything will be fresh. Its just a bit of a pain getting it all back to how you want it, but worth it in the long run i guess....

If you would like to keep your settings, you can. Open your /home folder and hit Ctrl+H. All of the .filename folders are your settings. Copy them somewhere safe. Then when you done your install, copy them into your new home folder. If anything starts misbehaving afterwards, just delete them.

---

### Post by Paqman on 2010-04-05
> **warfacegod said:**
>  Then when you done your install, copy them into your new home folder.

The main thing that go wrong with this is file ownership. Unless you set up your accounts exactly identical on the new system, it won't work. You can fix this by forcing ownership of all the files in your home:
```
sudo chown -R username /home/username
```

---

### Post by warfacegod on 2010-04-05
Yeah, forgot about that. My fault.

3 stars for catching my mistake!:KS:KS:KS

---

### Post by Paqman on 2010-04-05
> **warfacegod said:**
> Yeah, forgot about that. My fault.

3 stars for catching my mistake!:KS:KS:KS

No worries, a lot of people forget about that one because they've only ever got one user on their machine, so it's never an issue for them. They've always got the same uid every time they reinstall.

---

