---
title: "Skype US wish help to install XP and Keep Ubuntu 8.10"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Peterfc on 2009-04-03
Hi All

I have tried all the help from this Forum to get Skype to work and have never had it working like it should. I have upgraded when updates are sent. Release Upgrade is ticked so I am up to date on all updates sent. 

I wish to install XP so I can use Skype. 

Option 1:- Install XP on the same drive as my Ubuntu.
Option 2:- Install onto a second drive.

Skype will work with XP I still have my XP disc could i install as option 1 and fick between Ubuntu and XP for calls.

Thanks for reading this Thread.....

Dell Dimension 2400 200GB h/drive 1GB ram DVD RW.

---

### Post by Tobi-fp on 2009-04-03
You should always try looking for help on the internet before posting here, there are so many guides on the internet... Just google it.. : dual boot xp

For a very quick walk through:
Install gparted:

~ apt-get install gparted

run gparted and resize your current partition, so that you have at least 10 gb free for the windows installation (You will not be able to access your linux folders from xp but you will be able to access your xp folders from linux, if you dont install extra drivers for ext2/3, just keep this in mind)

Anyways, now you can just plug your windows xp cd in, run the install and when it prompts you for witch partition you want to use, just remember how big you made the disk and choose it..

Nothing more to it

---

### Post by Tobi-fp on 2009-04-03
anyways, can you try to run skype in a terminal session, maybe i can help you with your skype issue

---

### Post by LowSky on 2009-04-03
> **Tobi-fp said:**
> anyways, can you try to run skype in a terminal session, maybe i can help you with your skype issue

Could you fill us in on how you installed skype, what are the issue is exactly.

installing windows after an ubuntu install is always messy and if there is a way around doing this the hard way, I'm all for it.

---

### Post by gandaran on 2009-04-03
> **Peterfc said:**
> Hi All

I have tried all the help from this Forum to get Skype to work and have never had it working like it should. I have upgraded when updates are sent. Release Upgrade is ticked so I am up to date on all updates sent. 

I wish to install XP so I can use Skype. 

Option 1:- Install XP on the same drive as my Ubuntu.
Option 2:- Install onto a second drive.

Skype will work with XP I still have my XP disc could i install as option 1 and fick between Ubuntu and XP for calls.

Thanks for reading this Thread.....

Dell Dimension 2400 200GB h/drive 1GB ram DVD RW.

what are your skype issues with ubuntu? skype should work just as well in ubuntu as in windows, one recommendation through is to install skype-static version from [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository, skype-static integrates and works better in the gnome environment, this is the version to install if using ubuntu.

---

### Post by mlentink on 2009-04-03
> **Peterfc said:**
> 

Skype will work with XP I still have my XP disc could i install as option 1 and fick between Ubuntu and XP for calls.


The only way that would work is if you installed XP within a virtual machine such as Virtualbox.

In a dual-boot configuration you would have to reboot each time you wanted to switch OS's

---

### Post by sneeks on 2009-04-03
what are the issues you have had with skype,as i found it normally work fine once you have set up the sound config.

---

