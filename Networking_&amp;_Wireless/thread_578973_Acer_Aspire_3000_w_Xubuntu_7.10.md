---
title: "Acer Aspire 3000 w/ Xubuntu 7.10"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2007-10-17
I have an Acer Aspire 3000 series laptop and I want to install Xubuntu 7.10 on it.

I am currently using the live CD right now before I partition my HD and make way for a second OS on it.  This version seems to recognize my network card as it shows up in the network interfaces list(in the network manager).

Now my problem seems to be with wireless security.  I can get a wireless network to show up, and if I try to connect to it, then after mabye 60 seconds or so I get a box that tells me the network requires a key.  It is a WEP key(64 bit Hex) and if I enter the key in(100% correct) then after clicking 'Login to Network', the process simply repeats.  I wait maybe another 2 minutes, then am prompted for the key again.  There is never an actual connection made.

I would like to install Xubuntu, but not if I can't connect to my networks.  Without an internet connection the laptop is essentially useless to me, as pretty much everything I do requires an internet connection.


Any ideas?  Is there something wrong with WEP(64 bit Hex) with Xubuntu? Or is it some compatibility issue with my network card(for Acer Aspire 3000)?  But the card is automatically detected and installed...

---

### Post by Sup3rkirby on 2007-10-18
Ok, so no help I see.  I've noticed a lot of that lately....

Question: If I were to use gparted on my Acer Aspire 3000 to create a new partition that is, say 10 Gb, what are the chances something would go wrong?  With gparted on the Ubuntu Fiesty CD I got some error that resulted in a blank HD(sucks without a backup).

Does NTFS raise my chances?

Is there a suggestion for the best partitioning program I could use on my NTFS partition(52.something Gb)?  I don't want to screw up my laptop here.  I do have a backup, but it is from about 2 months ago(a lot of changes have been made since then).  I can't make a backup until tomorrow, but I really do enjoy Linux and would like to enjoy it asap.

---

### Post by jdzitro on 2007-10-18
I like using the gparted boot disk to customize my hd. It runs a lot faster and overall easier than doing it from within the OS. It's a little more time but it does things right (when you know what you are doing). There shouldn't be any problems creating a new partition so long as disk space allows.

NTFS and ext3 are not pals. My external (where I keep everything important) is in FAT32 so that I can read/write it from both winblows and buntu.

IMHO, [get gparted on a cd]("http://gparted.sourceforge.net/livecd.php") and perform your partitioning tasks that way.

[Super GRUB Disk]("http://supergrub.forjamari.linex.org/?section=download") is also a great tool to have if your MBR goes to **** from changing things incorrectly.

---

