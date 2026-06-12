---
title: "Install advice for new computer user with new computer !!!"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-02
**HERE IS MY SITUATION: **
 
**I have a new desktop being delivered to me next tuesday... no os... one 320 gb hdd... q9300 processor... 9600gt video... i am a computer novice at best but willing to learn... i have a burnt copy of xp pro disc including the key...**
 
**HERE IS MY OBJECTIVE:**
 
**I would like to partition the hdd into 2 partitions of roughly 160gb each... i would like to install 9.04 (disc bought on ebay) and have 1/2 the hdd reserved for windows xp pro in case i need it... **
 
**HERE ARE MY QUESTIONS:**
 
**1. How do i go about partitioning the hdd on a brand new computer??? from the bios???**
 
**2. is there a partition that would be more beneficial to install 9.04 to or does it matter???**
 
**3. is there an advantage to installing xp pro first or does it matter???**
 
**4. should i try to buy a windows 7 rc disc because it might be more user friendly and bypass the xp pro???**
 
**5. should i even be trying to do this with my limited know how???**
 
**6. can anyone explain this in novice talk step by step for me???**
 
**THANKS in advance for any input...**

---

### Post by arochester on 2009-07-02
Look at [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by frunns on 2009-07-02
1. Nah, just boot from the Ubuntu disc, and then you get to partition it during the installation. (I'm sure there are some tutorials out there that can help you if you need it, and you should hopefully be able to use internet while installing so it shouldn't be a problem if you got the patience)

2. Partition type? Or first or second partition on the disc? I'm supposing the latter. I would probably put XP on the first and Ubuntu on the second if I was going to play some games on XP (you can get slightly better performance that way).

3. XP has a... Not so intutive way of partitioning, but then again your need is simple, and if you install it first it won't mess up your Grub when you install it (installing Ubuntu and then installing XP will cause XP to boot every time you start your computer, instead of a menu where you can choose between the two, but that's fairly easily fixable, just takes some googling)

4. Well, you don't really need to buy the RC, as it's free. I'd recommend trying it out if you're interested, I don't like Vista but W7 seems kinda good.

5. Heck yeah! You gotta learn in one way or the other! :)

6. Well, that's kinda what I've done. What do you want to know more specifically? And give the bold text a rest, use it for emphasis.

---

### Post by tvtech on 2009-07-02
1.  partitioning can be handled by any new os install disk, windows mac osx ubuntu.  I recommend you use ubuntu.  You are going to want to make at least 3 partitions.  40-60 gig for ubuntu  40-60 gig for windows a partition that is slightly larger than your amount of ram for swap and the final partition as a storage drive that you'll format ntfs. Use the partition editor in ubuntu to do this. 

2. don't install this as a dual boot system it's a big hastle!!!!!!

3. install ubuntu as the main OS, you've got some pretty serious hardware so just run windows in a VM  unless your insistent on running heavy duty 3d games. 

4. if your insistent on running heavy duty 3d games go download [gparted]("http://www.gparted.org") live cd and use it to do your initial partitions

5. if you've isstalled ubuntu 9.04 to the primary drive get it all up and running enable your hardware drivers and update the system.  Install [Virtual Box]("http://www.virtualbox.org")
make sure it's the newest one vbox 3.0 
if you need help it comes with an excellent user manual

build yourself a VM and call it windows install windows into the VM

6. if your going this route you don't need the extra partition for windows. 

7. the newest vbox has experimental support for direct 3d via direct x9 and 10  so you should be able to install and run 3d games in the Vbox.  

8. this means you never have to reboot to access a windows feature!!!!!! YAY

9. YES YOU SHOULD BE DOING THIS ESPECIALLY SINCE YOUR A NOVICE!! how do you think you become a GURU?  by not trying things?  

if your insistent on running a dual boot do it this way.

1.  boot up your system with the windows install disk and use the built in partition manager.  set up the 4 partitions like I said.  

2. update windows and make the world a happy place.  

3. put the ubuntu disk in and use the manual mode when it asks you about which partition it wants.  set " / " =  room directory ubuntu to install to the unused 40-60 gig partition.  and set the swap as the small partition that is slightly larger than your computers ram.

4. don't forget to mount the other drives/ windows partition and data drive as well.  you'll want to type in the mount point for these two drives DO NOT FORMAT THEM, windows should have done this already.  mount them in the /media/DATA   and /media/WInDOz

5.  I seriously don't recommend dual boot it's a hastle and will only make you angry.  

install Ubuntu as the primary os and just do 3 partitions ubuntu 40-60 gig swap just larger than your total ram.  and a third partition.  for data.   Then install windows in a VM. with virtual box.  you'll be MUCH happier!!!

hope this helps!


**WINDOWS 7 is NOT NOT NOT more user friendly if you already know xp!**

---

### Post by Elfy on 2009-07-02
Hi - 

you can use the partition editor on the livecd to deal with the partitioning.

Once you have booted it is in the System Admin menu.

Create a partition to install windows in - it will go at the beginning of the drive - easier to deal with that for windows. Linux will install wherever you want in my experience - windows not so.

When you start the buntu install - use the free space - it should create the necessary partitions there for you. If you have isasues then - post back - you can get online from the livecd.

I won't go into installing windows for the moment other than to say it is slightly easier to have it installed first - but it is not very hard to deal with if you don't.

---

### Post by firewall_03 on 2009-07-02
make sure your new computer uses EIDE for the hard drive or you will not be able to install Windows XP, but you can still install Ubuntu

---

### Post by frunns on 2009-07-02
> **tvtech said:**
> **WINDOWS 7 is NOT NOT NOT more user friendly if you already know xp!**

Of course you think something new is less user friendly when you put it like that. I mean, by that logic you shouldn't try PS, because you already know how to use Paint. And considering the computer, if he really want's Windows he should go for something newer than XP. Seriously. And comparing W7 to Vista, he'd be (IMO) better off with W7.

---

### Post by NOTAGEEK on 2009-07-02
What i meant by win 7 being more user friendly does not have to do with my exposure to XP...  I think i read somewhere (?) that win 7 is more user friendly when it comes to partitioning and recognizing UBUNTU as a 2nd OS...  Am i on the right track there ???

---

### Post by austinpsycho on 2009-07-02
> **NOTAGEEK said:**
> **HERE IS MY SITUATION: **
 
**I have a new desktop being delivered to me next tuesday... no os... one 320 gb hdd... q9300 processor... 9600gt video... i am a computer novice at best but willing to learn... i have a burnt copy of xp pro disc including the key...**
 
**HERE IS MY OBJECTIVE:**
 
**I would like to partition the hdd into 2 partitions of roughly 160gb each... i would like to install 9.04 (disc bought on ebay) and have 1/2 the hdd reserved for windows xp pro in case i need it... **
 
**HERE ARE MY QUESTIONS:**
 
**1. How do i go about partitioning the hdd on a brand new computer??? from the bios???**
 
**2. is there a partition that would be more beneficial to install 9.04 to or does it matter???**
 
**3. is there an advantage to installing xp pro first or does it matter???**
 
**4. should i try to buy a windows 7 rc disc because it might be more user friendly and bypass the xp pro???**
 
**5. should i even be trying to do this with my limited know how???**
 
**6. can anyone explain this in novice talk step by step for me???**
 
**THANKS in advance for any input...** 
In my opinion, just skip all the expensive windows stuff and go for it! If you find you don't like it and still want windows, the later versions of windows (I would in fact recommend windows 7 to people, its basically a faster and more usable version of vista) actually can handle dual booting without much effort; (so can linux so it doesn't matter which order you install them though hardcore linux users will tell you otherwise;))

---

### Post by austinpsycho on 2009-07-02
> **tvtech said:**
> 


**WINDOWS 7 is NOT NOT NOT more user friendly if you already know xp!**

Yeah, ima agree with others on this thread; I did the windows 7 beta test (it ended which incidentally is why i now use ubuntu) and i was very happy with it as a windows xp user. It is slightly different than xp, not very different from vista (user-friendlyness wise) but he *is* on the right track when he says that it will handle the dual boot better

on a side note, whichever operating system you install last will be handleing the boot

---

### Post by NOTAGEEK on 2009-07-02
THANK YOU to all that replied to my post...
 
I am reading all input...
 
All your posts have helped...
 
NOTAGEEK

---

