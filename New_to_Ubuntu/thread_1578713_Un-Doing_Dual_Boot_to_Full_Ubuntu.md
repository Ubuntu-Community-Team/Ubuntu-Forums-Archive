---
title: "Un-Doing Dual Boot to Full Ubuntu"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by jbocean on 2010-09-20
I wrote an earlier thread on increasing Ubuntu partition. 

Instead of trying to adjust partitions (sounds scary), I am considering doing a complete re-install of Ubuntu 10.04 and to just overwrite the whole hard drive 
(wiping out Win-XP). 
I have already backed up the files I wish to save.

My Computer:

* Dell Inspiron 4550: 2gig RAM, 38gig HD

* Linksys wireless receiver 300N-USB

 **At the end of the day, the most important thing is having a wireless internet connection that 'just works' w/out hassle, and the extra hard drive space**.

In theory it sounds OK, but since I have never done this before, I want to know ...

a) Is an 'overwrite' kind of reinstall even recommended? I mean is there a high probability of success?
b) I will use a hard-wired internet connection during the actual install - then move the computer to another room after the install and any updates/tweaks to set up the wireless connection.
c) Will I have to completely re-install my wireless receiver? - I still have the CD it came with.
d) What major pitfalls do I need to know about?


Thanks for helping

---

### Post by perspectoff on 2010-09-20
38 Gb isn't a very big hard drive, these days. I went to Best Buy and they had big (internal) hard drives for, like, $30.

Are you sure you don't want to just buy a new one and keep both Windows and Ubuntu?

I'm not a big Windows fan, but I still run across a program now and then (for work) that runs only in Windows and doesn't run well in Wine.  I still like Windows XP, and still run it every once in a great while.

You might want to consider keeping it around for a while longer. 

If your computer supports 2 hard drives (and even old ones usually do) you could even install Ubuntu on the new hard drive, leaving Windows untouched on the old one. I did that on my kid's computer, so she wouldn't squawk about me touching Windows, and leaving it "the way she liked it".

Yeah, there are risks and frustrations with any new OS. Heck Windows Vista didn't work for many users for over a year. There are some graphics bugs with Ubuntu Lucid for a large number of computers. I'm a pretty knowledgeable Ubuntu user but it still took me 3 months to get 2 of my older computers to work with Lucid.

Fortunately, I never, ever overwrite anything. I install a new OS in parallel to an old one, and only when the new one is working 100% do I retire the old one (and usually just leave it sitting there as a backup for a year or so). You never know what important files were scattered on that old OS that you had forgotten about, but again might need one day. (That happened to me with taxes one year, when I was audited and I needed TurboTax files from 7 years earlier which I thought I would never need again.)

---

### Post by wilee-nilee on 2010-09-20
> **jbocean said:**
> I wrote an earlier thread on increasing Ubuntu partition. 

Instead of trying to adjust partitions (sounds scary), I am considering doing a complete re-install of Ubuntu 10.04 and to just overwrite the whole hard drive 
(wiping out Win-XP). 
I have already backed up the files I wish to save.

My Computer:

* Dell Inspiron 4550: 2gig RAM, 38gig HD

* Linksys wireless receiver 300N-USB

 **At the end of the day, the most important thing is having a wireless internet connection that 'just works' w/out hassle, and the extra hard drive space**.

In theory it sounds OK, but since I have never done this before, I want to know ...

a) Is an 'overwrite' kind of reinstall even recommended? I mean is there a high probability of success?
b) I will use a hard-wired internet connection during the actual install - then move the computer to another room after the install and any updates/tweaks to set up the wireless connection.
c) Will I have to completely re-install my wireless receiver? - I still have the CD it came with.
d) What major pitfalls do I need to know about?


Thanks for helping

If your wireless is working with the live cd then you should be set. A overwrite is one method if it was me I would just wipe the whole drive with gparted, in the Ubuntu Live cd. Then just let it install to the free space. 

Some though like to set up separate home partitions and other specialties so others will comment I'm sure.

The one concern may be the graphics driver so just run the live cd and run this command in the terminal to get this info in the thread for others.
```
lspci | grep VGA
``` 
You could also post. 
```
lspci
```

The second command shows more the first just the graphic setup.

**Edit: Looking at your original thread and the download of the partition table I see you have a Linux install. Is the wireless working there?, Are the graphics okay already, and what distros are they if they work.**

---

### Post by perspectoff on 2010-09-20
PS I hear a lot of people whining about their wireless in these forums, and there are a few hiccoughs, but in my experience they are easily solved.

I have never had a wireless problem persist for very long or not be able to find a quick solution. I have 5 laptops, all with different wireless.

I wouldn't let wireless be that much of a worry.

All my computers are able to run Lucid, now, in a stable fashion, but I have done a bit of tweaking and fiddling. Two advanced servers had to be reverted to Karmic because of some advanced server incompatibilities, but they should not be an issue for a new user.

---

### Post by v1ad on 2010-09-20
i swapped over to 10.10 today and so far i have no issues, and like perspectoff said wireless issues are pretty easy to fix. i swapped my laptop to full ubuntu, and i am actually more than happy with my 7 second boot time (post bios SSD). and do i need windows for anything? nope.

---

### Post by lfforman on 2010-09-20
I recently did with my notebook and my daughter's computer what you are considering to do. my experience was the following

I installed as dual boot and played around with configurations and everything to see exactly what i want to do and how to make things run properly (flash, ubuntu-extras, etc)

As i was satified i back-up my files, run the LiveCD and completely wiped my hd during this new installation.

Installed all the extra software and configurations I needed and updated the version
if you are newbie i would recomend you to use a package called ubuntu tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) it can make some things more easy.

I think it is important for you to test and use as a dual boot for some days so u can be sure about all you want to configure and see how it works.

I am very happy with my notebook, and my daughter is very happy with herd old slow windwos machine running fast.

---

### Post by lbrty on 2010-09-20
Does your current system work 100% (wireless, video, etc) with Ubuntu? You can also try running Ubuntu off a live CD or USB to test all your hardware on the system that you are thinking of installing Ubuntu on. Once in the live enviroment, goto System>Administration>System Testing and take it step-by-step. If all the hardware peforms as expected on the System Testing and wireless internet (etc) all work promptly then make sure you have your data backup (as you stated) and do a fresh install. There should not be any problems during the installation and if there is use another computer to login to these forums to describe the problem.

---

### Post by jbocean on 2010-09-21
Wow - 
Thanks for such swift and thorough responses!
I'll address some of the specific points.

+  We have another computer w/ Win-7 so I feel like I can sacrifice this older machine totally for Ubuntu (my dream).

+ I installed Lucid sometime in early May 2010 and have had a couple of months to configure and play around w/ it (it is so much faster and stable than Win-XP). 

+  When I did the Lucid install I went to a site called OMG!Ubuntu! and their 4/29/10 post "10 things to do after installing Ubuntu 10.04 Lucid Lynx". I followed several of their suggestions including UbuntuTweak.

+  In the next couple of days, I'll put in the Live-CD and see if I can get the wireless working in the Live environment. Wireless is working fine now w/this computer in dual boot Win-XP & Lucid. The graphics drivers appear to work well also.

Thanks!

---

### Post by mastablasta on 2010-09-21
> **jbocean said:**
>  
+ In the next couple of days, I'll put in the Live-CD and see if I can get the wireless working in the Live environment. Wireless is working fine now w/this computer in dual boot Win-XP & Lucid. The graphics drivers appear to work well also.
 

 
if it works in dual boot mode then you don't need to test it in Live CD. As basically oyu already have it installed, but you have it next to another OS (Windows).
 
also refering to oyur first post it would be better to have computer plugged in to internet via cable while oyu are resolving any issues regarding graphics or wireless driver. i mean you can't download wireless driver (if necessary) if your cable is out and your wireless not working yet.

---

### Post by corrytonapple on 2010-09-21
Welcome to the fourms!:smile:
> **jbocean said:**
> 
 **At the end of the day, the most important thing is having a wireless  internet connection that 'just works' w/out hassle, and the extra hard  drive space**.

So right now you do not have a working internet connection? If not, lets get that problem solved first.
> **jbocean said:**
> 
 a) Is an 'overwrite' kind of reinstall even recommended? I mean is there a high probability of success?

Very High, in fact, it is the way I would do it.
> **jbocean said:**
> 
b) I will use a hard-wired internet connection during the actual install  - then move the computer to another room after the install and any  updates/tweaks to set up the wireless connection.

That should be fine. I would do that too. It is what I did.
> **jbocean said:**
> 
c) Will I have to completely re-install my wireless receiver? - I still have the CD it came with.

If it works now no further action needs to be taken.
> **jbocean said:**
> 
d) What major pitfalls do I need to know about?

There  are none. Besides software, but there is a open source version for  everything. If it works for you now than it will be fine later. Tell us  if you want to wipe, reformat, and reinstall Ubuntu. Will be glad to  help.

---

### Post by jbocean on 2010-09-29
Me again - 

I have arranged time on Friday to convert my old Dell Inspiron 4550 totally over to Ubuntu (and over-writing Win XP).

_Question 1_:
Will the re-install I do on Friday automatically update me to 10.04.1 ?

_Question 2_:
Since 10.10 is just around the corner; can I re-install 10.04 (keeping the LTS) and then get some of the features of 10.10 which I like?

* New Software Center
* Updated Nautilus
* New Sound Menu
* New Ambiance theme

Thanks!

---

### Post by Elfy on 2010-09-29
welcome back :)

1 - you will only have 10.04.1 if you downloaded the iso after 10.04.1 was released, if not then you will have 10.04 untill you update.

2 - it might be that some of things in 10.10 will become available if someone makes them available - they won't though become available through the default repositories.

Why not grab a copy of the maverick RC on friday and see if it works for you and use that instead if it works for you.

---

