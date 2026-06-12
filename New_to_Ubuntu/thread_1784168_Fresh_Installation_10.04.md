---
title: "Fresh Installation 10.04"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by rs321 on 2011-06-16
Howdy,

I have a corrupted version of XP on my hard drive and a few days ago I installed Ubuntu for the first time and messed that up all by myself.  What I plan to do tomorrow is have he HD formatted and start from scratch but before I start plugging-in all sorts of stuff from Ubuntu I'd like to find out the general consensus of what would be best.  For example, in my unbridled zeal to get going I installed several music players and several DVD recorders and several of almost everything else to the point that now none of them function.  Does anybody have a particular favorite app for each little goodie, or are there some that don't work quite so well as others?  I suppose that's like asking if anybody just dropped this $100 bill but it's worth a shot.

I'll be installing 10.04 LTS and have a choice between 32 and 64 bit versions.  My computer will certainly handle 64 bits but is there any reason anyone can think of why I should stick to the slower version?

Thanks in advance,

-Randy

---

### Post by r-senior on 2011-06-16
How did you install these applications?

The reason I ask is that one of the most common reasons that people get into trouble coming from Windows to a Linux distribution is continuing the approach of "download and run installer". If you use the package management features of a Linux distribution (so that would be Software Centre, Synaptic et al on Ubuntu), you won't go far wrong. IME applications can be installed and deinstalled much more freely on a Linux distribution as long as you use the package management features provided.

OK, you might leave a few configuration files in your home directory but it's not going to do a great deal of harm. Otherwise applications do get uninstalled properly and don't leave a performance-draining legacy behind.

There's more on 64-bit vs 32-bit here:

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by wildmanne39 on 2011-06-16
> **rs321 said:**
> Howdy,

I have a corrupted version of XP on my hard drive and a few days ago I installed Ubuntu for the first time and messed that up all by myself.  What I plan to do tomorrow is have he HD formatted and start from scratch but before I start plugging-in all sorts of stuff from Ubuntu I'd like to find out the general consensus of what would be best.  For example, in my unbridled zeal to get going I installed several music players and several DVD recorders and several of almost everything else to the point that now none of them function.  Does anybody have a particular favorite app for each little goodie, or are there some that don't work quite so well as others?  I suppose that's like asking if anybody just dropped this $100 bill but it's worth a shot.

I'll be installing 10.04 LTS and have a choice between 32 and 64 bit versions.  My computer will certainly handle 64 bits but is there any reason anyone can think of why I should stick to the slower version?

Thanks in advance,
-Randy
Hi, first I have been using 64 bit for 4 years with no problems.
2. I use vlc to watch dvd's it works great for me.
3. I use brasero or k9 copy to burn dvd's ans cd's and I get them all all set up to work by going to this link and follow the instructions all the way down the page.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by candtalan on 2011-06-16
Welcome!
I think that starting out, the 32 bit version will give fewer questions, and unless you really need more than (4GB?) the 32 bit ram size in operation it is not worth it in my opinion. I would keep it simple, at least just now.

It is not clear from what you say if you have retained XP on the hard drive?

Also, did you install Ubuntu into Windows (wubi) or did you use a normal method, which creates partitions for Ubuntu?

Generally you will not need to 'format' before a fresh install but it will be most important for you to know which install option to use, and the reasons why.

Ubuntu comes with a set of apps by default. If you want to try more, be sure to use the Ubuntu Software Centre in Ubuntu, don't just download from various internet places, yet anyway.

The first thing I do after install is to get updates. Then I install Ubuntu restricted extras. Then, well, it is up to you.

A small comment - 10.04 is the original image, without updates. It is useful to use the 10.04.2 image, which includes many updates and probably some more drivers.

---

### Post by rs321 on 2011-06-16
Folks,

Thanks so much for your prompt replies.  I'm running an AMD dual core processor on a matched Gigabyte motherboard.  I expect I'll install XP first because it becomes confused so easily, then bring Ubuntu in and let it sort out the details.  On the first install I didn't find the installation package until I got a whole bunch of other stuff plugged in so this time I'll do what Ubuntu (and you) suggest and then see what else I want to add, but I'll get the system up and running and be comfortable with it before I get too creative on my own.

I'll reinstall XP just for the familiarity of it but once I get rolling with Ubuntu I shall be immensely pleased to kiss XP and MS goodbye.

(BTW, one of my neighbors is an elderly gentleman who was born and raised in Nigeria and is quite familiar with the philosophy of Ubuntu.  I approached him about it for clarification of pronunciation (just as it is written, with all the vowels sounding the same and no stress on any syllable) and it took me half an hour before I could break away from his devotion to the philosophy.  At least I know I pronounce it correctly.)

Thanks again,

-Randy

---

### Post by rs321 on 2011-06-16
Candtalan,

Pardon me, please, but I didn't ignore your questions intentionally.

I'll go with the 64 bit install then have XP to use during the learning curve, with XP installed first.  I'll then install Ubuntu separately and let it set the partition because I'm not familiar with the process and can always (so I've read) either enlarge it or add another partition as necessary.  I'll find the updates first and then the 10.04.2 image asap.

Thanks again,

-Randy

---

### Post by crispy_420 on 2011-06-16
The 4GB limit issue is not the same as it is in Windows. In Linux using the PAE kernel supports 64GB of RAM on a 32-bit OS ([https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)).

---

### Post by candtalan on 2011-06-17
> **rs321 said:**
> Candtalan,
Pardon me, please, but I didn't ignore your questions intentionally
No problem at all. I am glad if you find  comments useful.
>  I'll go with the 64 bit install then have XP to use during the learning curve, with XP installed first OK, as you hinted, I think xp will want to be offered a partition which is already formatted before install. If I am correct here, then if you wish you can use the Ubuntu live CD which includes 'gparted' partition editor and using this you can delete existing partitions, make a new one and format it to NTFS.
>  I'll then install Ubuntu separately and let it set the partition because I'm not familiar with the process 
After XP, then, re start with the Ubuntu CD in the drive, boot from it, and choose install side by side. It will automatically resize sensibly and create its own partitions.
>  and can always (so I've read) either enlarge it or add another partition as necessary.  I'll find the updates first and then the 10.04.2 image asap.
Thanks again,
-Randy
Ubuntu 10.04.2 is the install CD image (choose)
[www.ubuntu.com/download/ubuntu/download](www.ubuntu.com/download/ubuntu/download)
and after it is installed, then subsequent the Ubuntu updates will be available via the Ubuntu Update Manager.

---

