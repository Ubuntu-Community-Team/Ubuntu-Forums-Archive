---
title: "Karmic install - stuck at 'prepare partitions'"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by stevek123 on 2010-04-06
I'm sorry to post this one. I did a search and found several folks with similar posts. I just didnt 'get' the answer. 

Situ: New 'hand me down' comp = 3.8Ghz dual core AMD 64 w/ 2MB ram & 150GB sata HD. 
Experience: I've run ubuntu on another comp since Gutsy - upgraded to Hardy & have been hanging there since. The guy who gave me the comp helped me set it up, so this is my first true solo install. 

I wanted to setup a dual boot with winXP to access a cpl of apps but xp doesnt carry sata drivers. Dumped the dual boot idea. Good bye M$.

I went to install Karmic from an iso disc. Karmic booted up well and ran everything so I went to install. I got a blank screen at 'prepare partitions'. 
OK... I went back to CD boot sys and looked in gparted. It had an 1GB boot partition, 8GB linux swap partition, & a 130GB section with an older linux/ubuntu OS on it. I formatted the 130 section into a 50GB ext3 and a 90GB ext3. Install borked at same place. ... so I went and used disc utility to make the 50GB partition bootable. Install borked at same place. 

NOW... from searching prev posts it appears that Install will search for unformatted space. Great. All I need to do is delete the partition(s). 
???  What I want is one partition for OS, one for swap, & one for Home. 

I'm not sure what to do next. Do I delete ALL the partitions (boot, swap, OS, home)? or just the OS section? or the OS & Home sections? or the OS, Home & Swap section?  Do I just delete/unformat the entire drive and let Karmic Install get me there?  ... and then... what sizes are recommended for the swap & OS partitions?
... and then... will install let me designate a separate partition for the Home folder or do I have to go back in later after the install and make that change?

---

### Post by LewRockwellFAN on 2010-04-06
Take my ideas with NaCl. I'm no expert. BUT I've had similar experiences. This may sound dumb but try carefully cleaning the CD even if it looks clean. 90% isopropyl alcohol like at Walmart. Wet that sucker good and carefully wipe with a clean washrag in a RADIAL direction (i.e., from the center out or from the rim in) until it is dry. (Or you can use a CD cleaning gadget if you like) Blow out the CD reader with some canned gas. As for deleting partitions, etc., if you have no data on there you want, I can't see any reason not to delete all parttions and start over from scratch.

With 2 GB of RAM I wouldn't bother with a swap (people will dispute that. I think they are wrong). I have 2 GB of RAM and I keep my whole Karmic 9.1, 32 bit installation in a 15 GB /. That is one partition mounted as root (/). It I were going to keep my data in home the way so many linux people do, of course make it bigger by whathever amount of space I thought I needed for data. Or I would use a seperate home partition. I keep my data on an FAT 32 tha anything can read. This simplifies making images of my system.

The installer will let you designate a partition as home during the partitioning phase of the installation. I'm pretty sure you CAN go back and do (or redo) this later if you change your mind about what you want although I have not done it. Certainly easier to do it during installation.

---

