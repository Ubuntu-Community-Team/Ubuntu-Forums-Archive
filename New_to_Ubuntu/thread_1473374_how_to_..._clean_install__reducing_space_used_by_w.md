---
title: "how to ... clean install / reducing space used by windows?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Karen Forrest on 2010-05-05
I would be grateful for instructions aimed at idiot level!
My laptop (and only computer) is a Packard Bell Easynote  BU45-0-002. It came with windows vista (no disc, but a recovery partition), which got slower and slower until last year, I got my friend to put ubuntu 8.10 on it. I was already using all open source software, except a couple of programmes for my palm, and my data was on a separate partition. I don't intend to go back and only load windows about once every two weeks -  to use a friend's printer, to sync a couple of things on the palm or if I want to use the webcam, which I never managed to get ubuntu to recognise.
But now I am getting daily kernal panic, and anyway, it's time for a fresh install I think. 
First - I have no idea how to do this. It's not helped by the fact that I'm in Africa on a slow connection. I have been able to get a copy of 9.10 on a disc, but downloading 10.4 isn't going to be possible. 
Second - I'd really like to reduce the amount of space taken up by windows. The 80Gb hard drive is divided as follows: Windows and its programmes 46GB (8GB free) - I'm not sure what is taking up so much space. Data 24GB (4GB free). Recovery partition 8GB (4GB free). 
Any suggestions would be appreciated! 
Thanks,
Karen

---

### Post by mörgæs on 2010-05-05
If you install 9.10, expect a lot of downloading as well. You will need to download hundreds of bugfixes (which is good, as 9.10 is finally getting stable). 

I guess you can better tell than I what takes the 46 GB in Windows. Do you have a lot of film and music? What is in 'data'?

---

### Post by madjr on 2010-05-05
well first try cleaning up a bit in windows, check each folder size in "users"

you'll be amaze all the "crap" or duplicates it can have

if you get like 15+ GB free, then you can install ubuntu pretty easy 

just follow this vid:
[http://youtube.com/watch?v=Z0tNpt5RZYI](http://youtube.com/watch?v=Z0tNpt5RZYI)

just hit next everything lol

you will then have:

windows
newer ubuntu 9.10
older ubuntu 8.10 (which you can delete later or keep for a while till you're all setup and move your files)

ps. partitioning is also really easy if you want to do it in the future. check this guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html) (bit more detailed)

just check it out and you'll be a pro

only thing you need to remember is that **windows = NTFS** ; so thats the only thing you need caution with

---

### Post by NightwishFan on 2010-05-05
Right click on 'My Computer' and hit manage. You will notice a disk management tab. Go to there and shrink/move your Windows drives so that you have free space at the end. If it does not let you get much free space you need to defragment first.

After this, when installing Ubuntu choose the 'use largest continuous free space' option. That will automatically partition and dualboot Ubuntu with Windows.

If possible I advise you perhaps find a way to get 10.04. Since it is a LTS, you will not have to upgrade for another three or more years.

---

### Post by Karen Forrest on 2010-05-05
Thank you - that already helped. 
I had planned to wait until I was on a decent connection again and then install 10.4, but the kernal panic I'm getting now has precipitated the need to work with what I can get access to.

The Users folders were only 400MB total. 
Data contains documents, music, photos mainly. Anything big like video I keep on an external hard drive.
The windows partition only has programmes. But after using disc clean up - I now have 20GB free - mainly due to getting rid of old restore points. What's left appears to be windows - which is using 18GB - and 4GB of programmes.

I'll defragment when the thunderstorm goes by and then put 9.10 on the space on the windows partition. I like the idea of still being able to use 8.10 until I get everything on the new version running properly.

Karen

---

### Post by timjohn7 on 2010-05-05
Karen
Where in Africa are you?  There is plenty of support at various universities and Linux User Groups.  We could certainly help with getting latest version CDs to you.

Have you asked Shipit to send CDs (it's free) though it takes a while?

I strongly recommend installing 10.04 for the reasons stated above, but it will also provide you with a really impressive version to use for many years.

PS  You do know about the various Palm Sync options in Ubuntu, don't you?

Cheers from a fellow-African.

---

### Post by Karen Forrest on 2010-05-06
Thanks for the help.
I'm at a small college outside Nairobi. I haven't given up on getting 10.4 - my current plan is to smile sweetly at our IT officer to try to persuade him to download it overnight. It's not that the internet here isn't able to cope, just that it is unreliable and very dependent on who else happens to be using it. And its not available in our accommodation and as the power is very unreliable, so that you need to be around to shut down if it goes off for longer than the battery lasts, I can't do it myself at night. And oddly the post is rubbish just now too - something that's not usually a problem here - so getting the CD sent probably isn't the best solution.
But then I should remember that when I return to my usual home in a West African village, I'll be on a dial up connection which doesn't work more often than it does, so I should stop complaining about what is really an excellent service here! 

As for the discs - after defragmenting and cleaning the disc again, the free 20GB on the windows partition reduced to 13GB - don't know why. But I then checked out disc management and discovered 2 partitions which weren't there before I gave the computer to my friend for him to install ubuntu last year. They don't have names and according to windows they are empty. Will they be where ubuntu lives? Or can I delete them and use them to make the other partitions bigger? When I'm using Ubuntu they're not recognised at all.
Karen

---

### Post by madjr on 2010-05-06
> **Karen Forrest said:**
> 

As for the discs - after defragmenting and cleaning the disc again, the free 20GB on the windows partition reduced to 13GB - don't know why. But I then checked out disc management and discovered 2 partitions which weren't there before I gave the computer to my friend for him to install ubuntu last year. They don't have names and according to windows they are empty. Will they be where ubuntu lives? Or can I delete them and use them to make the other partitions bigger? When I'm using Ubuntu they're not recognised at all.
Karen

well if the partitions are NTFS or FAT32 they're windows partitions

if they are ext3 or ext4, then that's ubuntu

using gparted in ubuntu you can figure it out better because windows is very primitive

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Karen Forrest on 2010-05-10
Thanks for everyone's help.
I spent a good bit of the last two days putting 10.4 on my computer and then repartitioning the windows section. And everything's working well! 
Karen

---

