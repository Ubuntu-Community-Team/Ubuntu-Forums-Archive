---
title: "Switching Over  to Linux"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by cfree220 on 2009-02-01
Ok, so Windows just stepped on my  last nerve, and I'm not even going to try to  fix it this time. Instead, I'm replacing it with Hardy Heron (I've read/experienced that Intrepid doesn't work as well on my computer out of the box). Before I actually go ahead and format my hard drives, I have some questions about preparing to move over.

First is this: I usually keep my files on a separate partition from the OS. I also prefer the default Vista folder hierarchy (for user files) to the Ubuntu one (I'm just more familiar with it, and have learned how to organize my files using that method). Is there a way for me to move my home folders over to a second partition?

Second is the preparation of the HDD. Should this be done with the GParted LiveCD and, if so, what is an appropriate size for the OS partition? How should the partitions be formatted? And will having this computer on a Windows network affect formatting (I know that when I set up a Samba server on an old desktop, the tutorial said that the second HDD should be NTFS....)?

In case there are any considerations I'm forgetting or unaware of, I'm installing 64 bit Hardy on a Dell XPS M1530 with an Intel Core2Duo T8300 processor.

---

### Post by kestrel1 on 2009-02-01
I would suggest setting your hard drive up like this:
All are seperate partitions.
OS = /
home = /home
swap = swap

---

### Post by SunnyRabbiera on 2009-02-01
Well for the first question you can just set a home partition, but keep in mind a hard drive even the most modern ones handle only handle up to 4 partitions.
You have to factor in your vista main partition, your vista home partition, your main ubuntu partition, your ubuntu home partition and then swap.
By that you got 5 partitions, if I were you I would just forget about a separate home partition until you are done your dual boot setup.
I also suggest taking time to get used to the ubuntu filesystem, its actually easier then you think.

Your second question you really dont need the gparted live CD to set things up for you as Ubuntu uses gparted by default and it can be accessed if you use the manual setting.
I also would not worry about your windows network, Vista uses NTFS by default so no worries with SAMBA

---

### Post by kestrel1 on 2009-02-01
> **SunnyRabbiera said:**
> Well for the first question you can just set a home partition, but keep in mind a hard drive even the most modern ones handle only handle up to 4 partitions.


Not strictly true. Hard drives can only handle up to four Primary partitions, but you can have as many Logical partitions as you like inside of an Extended section of the drive. So you could have Three Primary & one Extended with more Logical partitions inside of it.

---

### Post by cfree220 on 2009-02-01
I don't think I'm going to set up dual boot... Microsuck refuses to give me any tech support since I bought my version of Ultimate through an educational retailer. My school doesn't offer tech support for Linux, but then again, you guys here on the eforum have been more helpful than they have been in troubleshooting problems, so I don't really see any loss there either.

Kestrel, when you say:
> I would suggest setting your hard drive up like this:
All are seperate partitions.
OS = /
home = /home
swap = swap
Is that something I have the option to do in the installer? I've installed Ubuntu before on my internal, but never saw that option.... IS that in the manual partition tool? If so, how large should the swap be? I have 4GB installed memory.

Thanks!

---

### Post by SunnyRabbiera on 2009-02-01
> **kestrel1 said:**
> Not strictly true. Hard drives can only handle up to four Primary partitions, but you can have as many Logical partitions as you like inside of an Extended section of the drive. So you could have Three Primary & one Extended with more Logical partitions inside of it.

Yeh but I personally advise against doing something like that for a newcommer.
Partitioning is very tricky, mess it up and loose data.

> **cfree220 said:**
> I don't think I'm going to set up dual boot... Microsuck refuses to give me any tech support since I bought my version of Ultimate through an educational retailer. My school doesn't offer tech support for Linux, but then again, you guys here on the eforum have been more helpful than they have been in troubleshooting problems, so I don't really see any loss there either.

Kestrel, when you say:

Is that something I have the option to do in the installer? I've installed Ubuntu before on my internal, but never saw that option.... IS that in the manual partition tool? If so, how large should the swap be? I have 4GB installed memory.

Thanks!

Well still I suggest backing things up if you can, if you are not dual booting it makes this simple.
After you back up your data you could use the manual configuration tool on the ubuntu disk to start playing around.
Here are some suggestions on how to set up:
Example:
If you have say a 70GB hard drive like I do, I would partition at least 10GB for the root partition so you have room to install apps, then use about 68GB for home and about 2GB for swap.
Because your memory is high I would not spend too much space on swap, 2GB should suit you fine

---

### Post by kestrel1 on 2009-02-01
Yes if you choose custom when you get the the partition section when installing or you could run gparted from the live CD to set it up first.
I wouldn't make the swap any larger than 1gb as you have plenty of RAM

---

### Post by cfree220 on 2009-02-01
On the topic of swapo.... Is it possible to increase the size of the swap later if need be? I have a 320GB internal. Right now, and likely well into the future, I have about 90 gigs still free, so if I can't increase the swap later, might it be worth it to just go ahead and do that now?

---

### Post by SunnyRabbiera on 2009-02-01
> **cfree220 said:**
> On the topic of swapo.... Is it possible to increase the size of the swap later if need be? I have a 320GB internal. Right now, and likely well into the future, I have about 90 gigs still free, so if I can't increase the swap later, might it be worth it to just go ahead and do that now?

If you increase the size of swap just back things up.
But trust me for your system 1 or 2GB of swap is more then enough.
Swap acts like extra memory, its mainly used for suspending to ram and such.
Your regular memory is quite large so swap is not that needed truth be told...
But having even a small swap partition does come in handy :D

---

### Post by jimmy the saint on 2009-02-01
> 
Yes if you choose custom when you get the the partition section when installing or you could run gparted from the live CD to set it up first.
I wouldn't make the swap any larger than 1gb as you have plenty of RAM 

That is true, unless you want to hibernate (very useful if you are a student going from class to class).  If you want to hibernate, make your swap RAM*120% or so.  You need to be able to dump the entire contents of your RAM to your swap partition in order to save the state.

Setting up your own partitioning scheme is fairly easy in the installer, but I would definitely recommend a backup of your data partition regardless of how you plan to install.  Any disk altering operation can be risky.

If you want a seperate /home partition (which may be a little more than you need to do in your very first installation) you would select "manually edit partition table" in the installer when it asks you where to install and create the partitions you want.  I would recommend one of around 15Gigs that you choose to mount as / and one of that is the rest of your drive mounted as /home.

---

### Post by cfree220 on 2009-02-01
Ok, just one last question. Hibernating the computer doesn't use the swap partition, does it? If not, then I'll just go ahead and use one or two gigs for swap.

---

### Post by jimmy the saint on 2009-02-01
> If you increase the size of swap just back things up.
But trust me for your system 1 or 2GB of swap is more then enough.
Swap acts like extra memory, its mainly used for suspending to ram and such.
Your regular memory is quite large so swap is not that needed truth be told...
But having even a small swap partition does come in handy

It is important to understand the difference between suspend and hibernate here.  
Suspend simple maintains enough power to keep the RAM from losing power, and therefore its state.  Nothing should be transfered from RAM to disk in this case, but if you are on a laptop, your battery will continue to drain at the rate neccessary to keep the RAM going.  If your batter dies, so does your session.

Hibernate, on the other hand, copies the contents of RAM to disk (swap) and restores it to RAM the next time the machine starts.  No power is used and the information is not lost.  This requires enough swap space to hold all of the information if RAM, so it is recommended to have more swap than ram to be safe if you want to hibernate.

Edit: Hibernate is slower than suspend, but eliminates the power concern.  Hibernate is faster.  Both can be buggy on various hardware (especially with nvidia) but can usually be made to work with given a little attention and TLC

---

### Post by cfree220 on 2009-02-01
ah, ok. Looks like the last post was a second too late. Alright, since I do plan on hibernating, I'll go with the larger swap.

Also, I'm not worried about file loss. Everthing is backed up on an external hard drive and on my server, so it would be really hard to lose everything.

---

### Post by SunnyRabbiera on 2009-02-01
> **cfree220 said:**
> Ok, just one last question. Hibernating the computer doesn't use the swap partition, does it? If not, then I'll just go ahead and use one or two gigs for swap.

Yes suspend/hibernate both go to swap.
But seeing your specs just 1GB of swap should suffice, you could probably hibernate your comp a week before it starts to count in :D

---

### Post by jimmy the saint on 2009-02-01
Here is a good explanation of suspend/hibernate and how they differ.
[http://www.linux.com/articles/54610](http://www.linux.com/articles/54610)

---

### Post by SunnyRabbiera on 2009-02-01
> **jimmy the saint said:**
> Here is a good explanation of suspend/hibernate and how they differ.
[http://www.linux.com/articles/54610](http://www.linux.com/articles/54610)

Well I knew that part, he only brought up hibernate after I suggested using swap for suspend.

---

### Post by jimmy the saint on 2009-02-01
> Yes suspend/hibernate both go to swap.
But seeing your specs just 1GB of swap should suffice, you could probably hibernate your comp a week before it starts to count in

The reaon I included the link is because I wanted to clear up the confusion about suspend vs hibernate.  suspend does NOT send information to swap.  that is a key difference and the reason swap in not important to suspend.  I made the mistake of not adding sufficient swap my first time around and spent days trying to figure out why I couldn't get it to work.  It turned out it was because I was confusing suspend/hibernate!  I'm just trying to prevent the OP from reliving my experience!

---

### Post by SunnyRabbiera on 2009-02-01
> **jimmy the saint said:**
> The reaon I included the link is because I wanted to clear up the confusion about suspend vs hibernate.  suspend does NOT send information to swap.  that is a key difference and the reason swap in not important to suspend.

Well in my case when I activate suspend I do see a slight spike in swap though...
I know its not hibernate as when I activate suspend, my computer says its in suspend.
Unless there is an odd config file on my end that has goofed it up.

---

### Post by cfree220 on 2009-02-01
Ok, so I went to do the installation. I'm not worried about losing my user files, in fact I count on it, since I'll want patitions of different sizes from the existing and in different places.

Just wondering what sort of formatting options I should be using... Can I use NTFS for my /home partition?

---

