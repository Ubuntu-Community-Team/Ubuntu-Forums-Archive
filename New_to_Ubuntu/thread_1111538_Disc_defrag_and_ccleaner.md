---
title: "Disc defrag and ccleaner"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by bessy on 2009-03-30
Hi, having just come from m.s i am used to de-fraging and using ccleaner to keep my computer in tip top condition. Having looked through ubuntu i cannot find anything that does the same. Do i need to do this with ubuntu? Also i went on you tube but it said i need flashplayer but was unsure if i should download it or there's an equivalent for linux? 

many thanks.

---

### Post by philinux on 2009-03-30
> **bessy said:**
> Hi, having just come from m.s i am used to de-fraging and using ccleaner to keep my computer in tip top condition. Having looked through ubuntu i cannot find anything that does the same. Do i need to do this with ubuntu? Also i went on you tube but it said i need flashplayer but was unsure if i should download it or there's an equivalent for linux? 

many thanks.


First bit not needed.

Second bit, have you installed 32 or 64 bit ubuntu and which version of ubuntu?

---

### Post by bessy on 2009-03-30
32 bit. 

Thanks

---

### Post by doctorbighands on 2009-03-30
No need to defrag in Linux. Cool, huh? :)

You can download flash player from [here]("http://get.adobe.com/flashplayer/"). Just follow the instructions for installation on that page. You should find it to be pretty easy.

Alternatively, you could install the flashplugin-nonfree package using Synaptic (System > Administration > Synaptic).

---

### Post by Therion on 2009-03-30
You'll want/need something to handle Flash, Java and a few other things.  To get this stuff, open a Terminal (Applications/Accessories) and copy and paste the following: ```
sudo apt-get install ubuntu-restricted-extras
```Enter your password when prompted, follow the prompts and you're off and running.

Forget about defragmenting your hard drive, that's no longer required if Ubuntu is your sole OS.

For routine clean up procedures, I suggest you use Quick Start:  [http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop-p2](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop-p2)

Be SURE you read and follow the install instructions.

---

### Post by kanikilu on 2009-03-30
You don't need to defrag. As for ccleaner, I don't know of an equivalent application. Since it does several different things, it's hard to make specific suggestions, but if you're just looking to do basic periodic maintenance, check out this article:

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

For Flash, you can either install the player from Adobe using these instructions:

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Or you can install the package from the repositories:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by philinux on 2009-03-30
Best thing to suggest is this.

system>admin>synaptic package manager.

Click on any line then type ubuntu-restricted

right click and select install

Then click the apply button in the menus.

---

### Post by bessy on 2009-03-30
Yes ubuntu is my only os. Got to say i am loving it and have found it very easy to use. Plus the help on here is 2nd to none and everyone gives good clear advice.  

Thanks again.

---

### Post by Lunx on 2009-03-30
> **bessy said:**
> Hi, having just come from m.s i am used to de-fraging and using ccleaner to keep my computer in tip top condition. Having looked through ubuntu i cannot find anything that does the same. Do i need to do this with ubuntu? Also i went on you tube but it said i need flashplayer but was unsure if i should download it or there's an equivalent for linux? 

many thanks.

No need to defrag as Ubuntu uses different file system to FAT and NTFS (defrag is one of the most oversold system utilities around to a degree, even NTFS doesn't gain great benefits from using it as far as I'm aware). There's a program called BleachBit which does similar to ccleaner ( based on what I've heard, no actual experience with it). There are equivalents to the official Adobe flash plugin, but my experience has been that many sites won't work unless you are using version 10, so you may well have to install that (You can get it from within Synaptic by searching flash-nonfree, but it will download it from Adobe and you are then subject to their terms and conditions)

---

### Post by presence1960 on 2009-03-30
> **bessy said:**
> Hi, having just come from m.s i am used to de-fraging and using ccleaner to keep my computer in tip top condition. Having looked through ubuntu i cannot find anything that does the same. Do i need to do this with ubuntu? Also i went on you tube but it said i need flashplayer but was unsure if i should download it or there's an equivalent for linux? 

many thanks.

You will very, very rarely ever have to defrag, That (defrag) is the exception rather than the rule. CC Cleaner will not run on a linux file system so you can keep that if you use windows still. That function is really unnecessary in Linux

Read this about ext3 filesystem regarding fragmentation: [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

For flash you can run this in terminal ```
sudo apt-get install flashplugin-nonfree
```

Or if you are using 64bit Ubuntu check this out:
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Good Luck!

---

