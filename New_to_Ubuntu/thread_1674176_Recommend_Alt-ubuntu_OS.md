---
title: "Recommend Alt-ubuntu OS?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by pgibson on 2011-01-23
I give up.  I'm tired of spending my weekends futzing with k/x/Ubuntu. 8.10 was the only edition that ever "just worked" on my old dell laptop.  I've loved the ubuntu --- heck, I even gave money to Canonical this past December, just because I believe in what they're doing --- but whatever the cause, it's clunked again.  Never mind how, I'm not going to try and fix it anymore.  I'll check back at 11.04 and see if it likes my equipment again.

So I'll do what I did when I got weary of Hardy couldn't run my wireless, I'll switch distros.  PCLOS was the one I settled on personally, back then.  I've got a separate /home ... anything I should do to those files if I install another distro on my / partition?  What if that other distro is a different "flavor" of linux than deb?  

What are some other user-friendly distros that probably will be able to interface with whatever stuff ubuntu puts in my /home partition?  Alternatively, what are the real risks of going back to 8.10?  Is that even possible?

---

### Post by NightwishFan on 2011-01-23
The issues you are having are more likely than not something to do with the vast collection of upstream projects and would not change no matter what distro you use. Why not base your system on 10.04 and try to fix your problems with it, and then you do not have to switch until after 2012 (if that happens).

---

### Post by pgibson on 2011-01-23
My bad, but I already have ubuntu 10.04 and xubuntu 10.10 installed on the two machines I use wirelessly, I simply haven't updated my usercp here at the forums.

Trying other distro live cds will give me a pretty quick diagnostic tool --- if the problem is upstream, then other distros will also fail to work ... then I'll probably do as you suggest and dig into this more deeply.  

How straightforward it will be to keep my /home partition for a new distro.  So many settings are there for various bits of software, will that cause problems  or be helpful?  I did this with keeping some continuity during upgrades of ubuntu, but switching distros is clearly a more profound change. 

Mandriva has been downloaded, pclos is on the way, puppy 5 too (just cause :)) and then I'm gonna get opensuse gnome.  Any other userfriendly distros you (or anyone reading this) might be able to suggest?

---

### Post by Paqman on 2011-01-23
> **pgibson said:**
> 
How straightforward it will be to keep my /home partition for a new distro.  So many settings are there for various bits of software, will that cause problems  or be helpful?  I did this with keeping some continuity during upgrades of ubuntu, but switching distros is clearly a more profound change. 


Well, it would probably work fine, but it's difficult to predict. Switching to a KDE distro like PCLOS or Mandriva means that very few of the settings will get used anyway (unless you've had Kubuntu installed at some point).

Personally, I would just create a new account with fresh settings on the new distro and copy any data files you wanted to keep from  the old user's home directory to the new one.

---

### Post by cipherboy_loc on 2011-01-23
> 
How straightforward it will be to keep my /home partition for a new  distro.  So many settings are there for various bits of software, will  that cause problems  or be helpful?  I did this with keeping some  continuity during upgrades of ubuntu, but switching distros is clearly a  more profound change. 


If it is a partition, as you say it is, then in theory it is very simple:

Install the new OS with only a /, nuking your old /. Set up a user account with the same name as the old user, and then modify FSTAB to mount your /home partition on boot. If you need more help, post back.



Cipherboy

---

### Post by Paqman on 2011-01-23
> **cipherboy_loc said:**
> 
Install the new OS with only a /, nuking your old /. Set up a user account with the same name as the old user, and then modify FSTAB to mount your /home partition on boot.

One problem you might run into is permissions. Users aren't actually identified by name, but rather by UID. Ubuntu gives the first user UID 1000, but not all distros do (some start at 500).

If you got permissions errors when you tried to log in you'd need to get to a root shell and run:
```
chown username:username /home/username
```

IIRC most distros should add your home partition to fstab automatically if you specify /home to be mounted there during installation. I've not come across one that doesn't, anyway.

---

### Post by pgibson on 2011-01-23
Thanks all.  I'm writing using Mandriva 2010 Live CD, and things have been muy smooth, even on this forum.  I've got to burn several more CDs, and play a bit.

Paqman, you make a good point: copy the data files and start over.  Most of my "important" things are in documents/videos/music etc.  Maybe I've borked some setting somewhere (how easy for me) and everything's pointing in different directions at once.  

Otherwise, I'll be back in the next day or so, I'm sure, about setting up things up.

Thanks all,
:)

---

