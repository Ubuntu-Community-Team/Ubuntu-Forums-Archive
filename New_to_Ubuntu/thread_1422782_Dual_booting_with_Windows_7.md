---
title: "Dual booting with Windows 7"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by gnometorule on 2010-03-05
I will soon buy a new laptop that will have Windows 7 preinstalled. I intend to dual-boot with Ubuntu (currently doing the same with XP on an old laptop). To not regret any purchase, any feedback welcome:

(1) Any laptops (by company, or by model within a company's offering) that are known to be either incompatible, or just make it a pain to get Ubuntu as a 2nd OS?

(2) Any tutorials for this particular install, or for special issues, if any, to expect when going through this? I assume there be must be a prior post (didn't pop up when 'search'ing here), so link to prior fine of course. Wouldn't such a link be a good sticky?

(3) Any sub-components (e.g., ethernet/wireless cards) that are known to either not work or work poorly with Ubuntu? Don't want to find out after the fact.

Thanks much.

---

### Post by OrangeCrate on 2010-03-05
I dual boot Ubuntu with Windows 7...

A good set of instructions to follow is here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

(Be careful with advice. Some here have been suggesting install instructions that were appropriate with XP, but not appropriate with Vista/Win7.)

Edit:

Forgot to comment on this...

> (3) Any sub-components (e.g., ethernet/wireless cards) that are known to either not work or work poorly with Ubuntu? Don't want to find out after the fact.

Run the Live CD prior to installing, to see if your hardware, etc. is compatible.

---

### Post by gnometorule on 2010-03-05
Tyvm for the thread - will read shortly. 

Just to clarify '(3)': I'm not particularly married to any maker of laptops or any model, so I'd like to known in advance if there are (in particular) ethernet / wireless cards that I should avoid. I'll then just not buy a laptop that is manufactured with them. So i can't run the live cd as you suggest as I don't have that new laptop yet. This is purchase advice mostly not to be bummed out after buying. Goal is to buy a laptop that will make installing Ubuntu as 2nd OS as smooth as possible.

---

### Post by sandyd on 2010-03-05
> **gnometorule said:**
> Tyvm for the thread - will read shortly. 

Just to clarify '(3)': I'm not particularly married to any maker of laptops or any model, so I'd like to known in advance if there are (in particular) ethernet / wireless cards that I should avoid. I'll then just not buy a laptop that is manufactured with them. So i can't run the live cd as you suggest as I don't have that new laptop yet. This is purchase advice mostly not to be bummed out after buying. Goal is to buy a laptop that will make installing Ubuntu as 2nd OS as smooth as possible.
any card with the broadcom chipset 4311-, 4312-, 4313-, 4321-, 4322- will work fine due to bcmwl (which works awesomely on the listed cards)
avoid some atheros chipsets, some of them require madwifi and ndiswrapper

---

### Post by uRock on 2010-03-05
Dual booting on my wife's 8 month old HP laptop painlessly. The only problem you may run in to that will cause you to need a repair disk is shrinking the NTFS partition.

---

### Post by sandyd on 2010-03-05
> **iRock said:**
> Dual booting on my wife's 8 month old HP laptop painlessly. The only problem you may run in to that will cause you to need a repair disk is shrinking the NTFS partition.
shrink it w/ the win7 partitioner and you shouldnt have any problems.;)
the fact that resizing the windows 7 partition with ubuntu will cause windows to complain should be added to a sticky.

---

### Post by uRock on 2010-03-05
> **carlee said:**
> shrink it w/ the win7 partitioner and you shouldnt have any problems.;)
the fact that resizing the windows 7 partition with ubuntu will cause windows to complain should be added to a sticky.

No matter what I did, it would only offer 8 gigs of free space. But, that was with Vista on that machine. I deleted Vasta, then using a GParted LiveCD I cut the NTFS in half, then made the EXT and Swap partitions. After that I clean installed Windows 7 Pro and Ubuntu on it.

Very true on the sticky part, but nobody reads the stickies.(or at least quite a few people I have seen posting.)

---

### Post by Robertjm on 2010-03-05
I'm using an older HP to dual boot so I can't really comment on new machines. What I will suggest is that you consider setting up a separate NTSF partition which you use as a shared data partition which is accessible from both Ubuntu and Windows. I did that, and it's pretty cool in case I need a document and I'm in the other O.S., or I want to have the same bookmarks and profile no matter which O.S. I'm in.

Once you get your system, if they're using a restore partition, make sure you back that partition up somewhere in case you ever need to restore your laptop to factory specs. Vendors might freak out a little if you have to send it back and they find you've done things to the restoration partition.

Good luck!!

Robert

---

### Post by seymur on 2010-03-05
I have 1.5 years old Toshiba, dual booting with Windows 7. Had no problems with drivers. I have one shared NTFS partition, and 2 other partitions for each OS.
Like guys said before, try live cd beforehand.

---

### Post by gnometorule on 2010-03-06
Thanks much everyone! I will dig into this more when I will actually buy the new system, but it will be good to know about components that work out of the box and some that don't, and to be able to fall back on the replies and links here. I did a quick google and add this link going over what several suggested - setting up a (shared) NFTS partition:

[https://help.ubuntu.com/community/Partitioning%20issues](https://help.ubuntu.com/community/Partitioning%20issues)

At the bottom are more links; those to psychocats are usually good for beginners. 

I'll close this now, but I think it could help if someone writes 'dual boot Windows 7/Ubuntu' as a sticky.

---

