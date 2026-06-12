---
title: "Advice Needed"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by rkanth on 2011-07-07
I'm using Karmic for a while and am very happy with it. But I understand it's not supported any longer and I need to upgrade.I want to know:

1. What are the pros and cons of using an unsupported version? I'm a tech-novice and spent long hours on various fora to get my computer to this condition where I'm very happy to use it. I don't even remember the sites and people (God bless you all) that I took help from if I were to do it again. Will I be able to use Karmic indefinitely, if I want to?

2. Is there a way I can get to 11.04 without changing my settings and losing any of my files, or going through meticulous back-ups?

3.Is it possible to create another partition on my HD where I can install 11.04 and use it as dual boot(9.10 and 11.04) and slowly find my way around to configure Natty like my present system and then migrate?
Thanks,
RK

---

### Post by cbanakis on 2011-07-07
Having a supported version is good, because if you try to use new hardware, or software, it will be more likely to work.
And there are security updates for supported versions, that address vulnerabilities in your computer.
Also, any known bugs/glitches are usually fixed.

You should be able to upgrade without losing anything.  (Theoretically)

All that being said..

If it aint broke, don't fix it.

If everything works fine, your happy with everything, and don't plan on upgrading anything in your computer, why mess with it.

Just because Karmic is no longer supported, does not mean there is a time bomb in your computer.
You may not get the security updates, but with Linux, the odds are always in your favor.
I wouldn't worry anyway.

---

### Post by nzjethro on 2011-07-07
> **rkanth said:**
> I'm using Karmic for a while and am very happy with it. But I understand it's not supported any longer and I need to upgrade.

Hi RK, I've recently been going through a similar decision whether or not to "downgrade" from 10.10 (soon to be unsupported) to 10.04 LTS (supported until 2013), so I hope I can help out.

> 1. What are the pros and cons of using an unsupported version? I'm a tech-novice and spent long hours on various fora to get my computer to this condition where I'm very happy to use it. I don't even remember the sites and people (God bless you all) that I took help from if I were to do it again. Will I be able to use Karmic indefinitely, if I want to?

[Here]("http://ubuntuforums.org/showthread.php?t=1782547") is a link to my thread, which outlines the pros and cons of upgrading. In general, while theoretically you can use any release even after EOL, it is not recommended, as updates for important security bugs will not be released, meaning your system may become vulnerable. If you are interested, I decided against reverting to 10.04 LTS, as I'm happy with the way my system works, and I'll cross the bridge of EOL when I come to it.

> 2. Is there a way I can get to 11.04 without changing my settings and losing any of my files, or going through meticulous back-ups?

You could update through the Update Manager, which will remove the need for such things. However, a clean install of 11.04 is probably faster, and will have less issues, so it may be worth it to back up and do a clean install. Even if you go through the Update Manager, I advise you to **have a full and tested back up of any files you wouldn't want to lose,** as I've read too often on these fora of people losing data in upgrading.

> 
3.Is it possible to create another partition on my HD where I can install 11.04 and use it as dual boot(9.10 and 11.04) and slowly find my way around to configure Natty like my present system and then migrate?


Yes, this is probably recommended. 11.04 is a pretty major change (Unity rather than Gnome), so it is probably worth your while testing it out to see whether or not a) you like it, and b) if it will run flawlessly on your system. You could do a small dual boot install, or else run 11.04 on a persistent Live CD for a week or so, to see whether you like it or not, before committing to replacing Karmic.

Another 2 cents, if you try 11.04 and don't like it, consider giving 10.04 LTS (Lucid Lynx) a shot. It's supported until 2013 (same time as 11.04), and it will be a lot more familiar to you roming from Karmic. Also, it is a lot more mature, and less buggy than Natty, so it should be a consideration for you.

**EDIT:** You may also like to read [this thread]("http://ubuntuforums.org/showthread.php?p=11016000#post11016000") about a user's experience transitioning from Karmic to Natty, to know what to expect.

---

### Post by rkanth on 2011-07-07
Thanks, nzjethro and cbanakis. You were helpful. I think I'll go the dualboot way. The problem I face with my linux don-know-how is not so much with files (most of them I save on to a different partition after my last tech tragedy) but with making the settings and programs work to my satisfaction and remembering the way I made them do so.
Thanks for assuring me that there won't be a time-bomb, cbanakis. Indeed I was worried that some programs may stop behaving over time.

I have another doubt;please don't laugh:
Suppose I go the Lucid way as nzjethro seconded, dual-boot, and during installation if something goes wrong, will it affect the new partition or also the one with karmic on it? What are the chances of screwing up the entire hard disk during partition?

Also, Is it possible to live with a live cd/usb and not install anything on the HD and still expect good performance from ubuntu? Where will the programs and daily security patches get installed if I run Ubuntu from a USB stick?

Thanks
RK

---

### Post by cbanakis on 2011-07-07
You can boot off a flash drive just as you would a CD.

When the install menu comes up, just select "Try Ubuntu" instead of "install"
And your hard drive will remain un-touched, (Unless you touch it, while in a live session.)
But I'm sure your not gonna boot up off a flash drive, then go around formatting partitions.

But as far as I know, you cant really use it as a permanent solution.

I think its just so you can poke around, and check everything out.
I'm pretty sure you can't save any settings, or files in that mode.

It is usually kind-of slow, and I don't think it gets updates of any kind.

You might be able to install 11.04 onto an external HD.

Then just change the boot order in your BIOS every time you want to switch OS's
But dual booting might be more practical.

I have never done it though, so I don't know if there are any risks.  I don't think there would be any problems though, since Ubuntu is designed to dual boot.

---

### Post by rkanth on 2011-07-07
Okay, I can do with more help :)

1. I'm going to install 10.04 LTS on a seperare partion on my hard disk. I'm going to create a new partion on my 500gig HD with about 350 g freespace. Can ubuntu handle this without screwing up the data? How risky is it?

2. After installing 10.04, I want it to work just like my 9.10 instal which is great. Is there a tool that can copy all my settings, preferences and downloaded repositories and any other configurations that I need? If it makes a list of all that I have on my present system, that's enough. I'll re-download them for 10.04.

Thanks in advance.
RK

---

### Post by rkanth on 2011-07-07
bump

---

### Post by rkanth on 2011-07-07
bumping...

---

### Post by Mark Phelps on 2011-07-07
First of all, while I understand your concerns, please do NOT bump every few hours.  The rule around here is no more than once every day (24 hours).  Bumping more often is considered rude -- and will not get you answers sooner.

As to retaining settings, customizations, files (etc), what most folks will tell you is that ALL of that stuff is under /home (and some in hidden directories and files). The implication of that is that if you copy off /home (including the hidden stuff) and then restore it after an update, ALL your custom stuff will be restored.

While that is generally true, it is NOT true in cases where you have (1) moved stuff outside of the /home filesystem branch, (2) installed apps from source,  (3) otherwise, made customizations outside of /home (example, hand-built a custom boot script file).

So, unfortunately, there is really no simple way to save and restore ALL the customizations you might have done.

I've made LOTS of custom changes to my Ubuntu installs and have gone to the trouble of (1) writing a document that describes all the different types, and (2) saving off the customizations in a data directory on another partition.

Thus, when a new Ubuntu version comes along, I do the following:
1) Create a new partition on an existing volume for that new version
2) Install the new version to the new partition
3) Mount the shared volume with the customization document
4) Go through the document and re-apply each of the customizations that still apply to the new Ubuntu version.

And yes, this is a LOT of work -- but since it's only needed twice a year, to me, it's worth it.

---

### Post by JKyleOKC on 2011-07-07
> **rkanth said:**
> Okay, I can do with more help :)

1. I'm going to install 10.04 LTS on a seperare partion on my hard disk. I'm going to create a new partion on my 500gig HD with about 350 g freespace. Can ubuntu handle this without screwing up the data? How risky is it?

2. After installing 10.04, I want it to work just like my 9.10 instal which is great. Is there a tool that can copy all my settings, preferences and downloaded repositories and any other configurations that I need? If it makes a list of all that I have on my present system, that's enough. I'll re-download them for 10.04.

Thanks in advance.
RK
Any time that you make changes to the partition tables, there's at least a slight risk of something going wrong and apparently losing everything. I say "apparently" because it's possible to back up the partition table itself, and subsequently restoring it, which usually brings back all the data. However even then there's risk involved. The real question is "How much risk is there?"

I've made changes without any ill effects, and so have many other folk here. If you actually have that 350 GB as "unallocated space" your risk would be very small. If it's simply unused space but already allocated to a partition, you would have to shrink that partition, and the risk would increase. In that case, you should back the entire drive up to an external HD using Clonezilla, just in case something goes wrong during the shrink process.

Your new install won't work EXACTLY like your existing one, because a number of programs have changed. The new install won't have any of your custom tweaks applied, either. However you will probably have an easier time of customizing it that you did originally, because you've been there before and won't have to do so much trial and error stuff.

You might be able to copy all the hidden files from your old version's home directory into the new one, but that might cause more problems than it solved. It would do no good at all for files stored in other system directories, though.

I came to Ubuntu at version 7.04, upgraded that to 8.04 without too horribly much trouble, and then moved to 10.04. The first upgrade took me several months of fine-tuning to get back the way I wanted; the second took only a couple of weeks (although I did misconfigure a few things that took me more than a year to get put right). Your mileage may vary, of course.

The changes at 11.04 seem to be extremely major, and the indications are that 11.10 will be even more drastically different so many of your existing tweaks may not apply. I stick with the LTS (Long Term Support) releases to avoid such hassles every six months...

---

### Post by candtalan on 2011-07-07
You try to avoid 'meticulous'backups. I understand, but it can be very easy, and very worthwhile. One question is what method to use, you might want to consider and discuss this. Personally I find a live CD (clonezilla live) is pretty easy in putting a whole drive, or a whole partition, into images onto an external USB drive. However, clonezilla is a bit scary to start with because it mostly comes up with lines of text, without any GUI. Some sort of external backup is worthwhile though. A simple copy out of your /home/username folder would be a very good start.
Good luck.

---

### Post by nzjethro on 2011-07-07
> **rkanth said:**
> Thanks, nzjethro and cbanakis. You were helpful.
No worries.

> 
Suppose I go the Lucid way as nzjethro seconded, dual-boot, and during installation if something goes wrong, will it affect the new partition or also the one with karmic on it? What are the chances of screwing up the entire hard disk during partition?


No, as long as you partition your HDD properly, you should'nt run into any errors. There are a lot of partitioning How-To's out there, and as always, post to the fora if you need help. And also, make sure you have a tested backup; while nothing should go wrong, things do go wrong, so it's nice to know that even if you cook something, you haven't lost anything.

> 
Also, Is it possible to live with a live cd/usb and not install anything on the HD and still expect good performance from ubuntu? Where will the programs and daily security patches get installed if I run Ubuntu from a USB stick?

There are two choices with a Live USB stick, persistent or non persistent. Persistent will save any changes you make to the OS to the USB. If you install programmes, download security updates, make system changes etc, these will be saved to the USB, and accessed each time you boot from the Live USB.
If you go non-persistent, no changes will be saved - each time you boot to Live USB it will be like you've just created a new Live USB, and no changes will be saved. I'd recommend creating a persistent USB (there will be a checkbox when you use Unetbootin).

---

### Post by rkanth on 2011-07-07
Thank you all. And sorry for the anxious bumping.

---

