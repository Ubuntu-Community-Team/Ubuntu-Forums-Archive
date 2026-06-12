---
title: "convert wubi to full install"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by gkraju on 2009-07-05
hi i have installed ubuntu 9.04 in Xp 
i going to format my Xp.
I dont want ubuntu to be removed what can i do to save my ubuntu installation? 

thanks....

---

### Post by ivanvajar on 2009-07-05
Just make copies of your files and do fresh installation. Since Ubuntu is installed inside Windows, you can't save it as it is when removing XP.

---

### Post by jmszr on 2009-07-05
gkraju.

These links might be of help: [http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/](http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/) and: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by Cringer on 2009-07-05
> **jmszr said:**
> gkraju.

This link might be of help: [http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/](http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/) . also this: [http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/](http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/) and this: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

I actually had those open when I came into this thread, as I have been working towards doing this since yesterday. I actually haven't found a 4th page that has similar info, which was the one I found yesterday to get me started down this road.

---

### Post by theozzlives on 2009-07-05
I'd say, backup your entire /home (hidden files and all), do a fresh install, and restore it. Example:
```
sudo tar cvpzf /path/to/backup/backup.tgz /home
```

Restore:
```
sudo tar xvpfz /path/to/file/backup.tgz -C /home
```

EDIT: Your /home is what's important. I'd also like to add, create a seperate /home partition. You'll only have to do this once, but keep reguluar backups "just in case".

---

### Post by jmszr on 2009-07-05
Cringer,

Did you try looking through your Firefox History for yesterday's thread/link? Assuming that you use Firefox,of course.

---

### Post by Cringer on 2009-07-06
> **jmszr said:**
> Cringer,

Did you try looking through your Firefox History for yesterday's thread/link? Assuming that you use Firefox,of course.

 No, but it was pretty much exactly the same as the links above.  In reference to the original post, I just finished (within the last hour actually) moving my Wubi Ubuntu install over to it's own partition. I have Ubuntu 9.04 64bit version. I used LVPM, from the links provided by jmszr above. I took my time doing this though, maybe if you don't care about keeping Windows then you could rush it a little more. Here is my story though I just posted on a different board.... (I left out step by step super-details, because those are in the links provided above, I simply followed those exactly, bit maybe someone get some details I always like to know, like length of time for some steps and what Vista did when I tried to go into it the first time.)    > Yes! N3RD success!  I just finished moving my Wubi Ubuntu installation over to it's own partition, with no frickin' problems at all. Took all day, actually 24 hours since I started last night but it wasn't non-stop work. Started last night with trying to get a Ubuntu Live CD going, and had trouble with and actual CD working. I had to go to a USB flash memory stick as my boot device. Got that working, then went over to Vista to start some clean up. Deleted some stuff, then started to defrag and went to sleep a bit later.   
 Woke up this morning and defrag was still going (two year old laptop, 240 GB HD, never been defragged). I stopped the defrag and downloaded a program to defrag instead of using the Vista app for it, since it was supposed to be faster. It probably was faster, but it still took another 5 hours until it was done defragging. Finished up some work I was doing and then rebooted using my USB stick to boot into. I then went to shrink my Vista partition, from roughly 224 GB down to 124 GB, that would leave me 4 GB extra in Vista besides what is there (that will increase a decent amount once I uninstall Wubi). This worried me, because I took a huge chance. I only had my Palm Pre to use to back up stuff, plus I was impatient. I backed up a few gigs of stuff onto my Pre incase things went wrong making the partitions, as I read is a very real possibility. gParted (partitioning app) let me know shrinking the Vista partition would take a while so I laid down for a nap.    
  Three hours later or so I woke up, and Vista's space was shrunk. I made two new partitions out of the open space, a swap partition of 2 GB, and my main Ubuntu partion with the rest, roughly 94GB. I may add a 3rd partition later on to use for my /home directory, but one giant step at a time for me right now. Once that was done I was supposed to reboot into my Wubi Ubuntu install, but I wanted to see if I killed Vista first. It scared me by stopping the boot to do a chkdisk run, but once that finished after about 20 minutes it rebooted and I was able to get into windows just fine. **phew**  Went back into Wubi Ubuntu install and downloaded a program called LVPM, which is made to move the Wubi install to the partition. This is huge for me since I didn't want to have to do EVERYTHING over again, especially downloading roughly 20,000 emails if my separate Thunderbird backup didn't work. So I started that, and it took about an hour to finish, I ate some dinner while waiting.     
 It finished, and then when I rebooted I had to change some GRUB setting so it pointed towards the new partition Ubuntu and not the Wubi install. That was quick and easy as it turned out and I have everything up and running. I am ******* loving this! Dual boot laptop with Vista and Ubuntu.   
 One note, my half plus day in Vista after a good amount of time in Ubuntu, I actually felt cramped in Vista. I couldn't switch to a new desktop, and it drove me nuts. That alone is a big enough reason to switch to Ubuntu.

---

### Post by Cringer on 2009-07-06
> **jmszr said:**
> Cringer,

Did you try looking through your Firefox History for yesterday's thread/link? Assuming that you use Firefox,of course.

 Actually I found it, I just had to be in Ubuntu because I had it saved as a bookmark and earlier I was in Vista.  [http://www.saltycrane.com/blog/2008/08/notes-moving-ubuntu-wubi-standard-ext3-partition-using-lvpm/](http://www.saltycrane.com/blog/2008/08/notes-moving-ubuntu-wubi-standard-ext3-partition-using-lvpm/)  This is the one I had written out and pretty much followed, though like I said the others are pretty much the same as well.

---

### Post by gkraju on 2009-07-06
> **jmszr said:**
> gkraju.

This link might be of help: [http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/](http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/) . also this: [http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/](http://infoqueue.wordpress.com/2009/01/04/wubi-installation-to-regular-installation/) and this: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

thanks for replies
it worked

---

