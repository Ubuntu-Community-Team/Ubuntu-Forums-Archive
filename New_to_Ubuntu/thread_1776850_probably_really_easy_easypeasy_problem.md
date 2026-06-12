---
title: "?? probably really easy easypeasy problem"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by RabidGoat on 2011-06-06
I'm running easypeasy updated fully on a asus eee pc 901 intel w/ intel atom processor. just upped the ram from 1 gig to 2 gigs but everything drags somewhat most of the time while the system monitor says both cores (if it even has two) are at or near 100%. thats not a huge issue as this is a netbook and i'm not expecting a mini deep blue here. but the main reason i'm posting is because i believe i messed up my partition. I keep getting this error message when running computer janitor.

Failed to run computer-janitor-gtk as user root.

Unable to copy the user's Xauthorization file.

I read up that this could be because of an error i made while partioning my drive. I left 4 gigs for the root directory, 12 for my home folder, and 4 for my swap thinking it would be enough but it filled up quickly with updates and a few programs. when I downloaded my last program (amarok) i had multiple warnings for low disk space, but it never completely filled up. i was trying to delete files but i didn't know which were system critical and I didn't want to break my ubuntu even more. anyways when I tried to run Gparted I got the same message about the xauthorization file again. I really don't want to re install and reformat again as this will be my third time... so any advice you unix wizards can bestow on a noob?

thanks in advance.

---

### Post by wildmanne39 on 2011-06-07
> **RabidGoat said:**
> I'm running easypeasy updated fully on a asus eee pc 901 intel w/ intel atom processor. just upped the ram from 1 gig to 2 gigs but everything drags somewhat most of the time while the system monitor says both cores (if it even has two) are at or near 100%. thats not a huge issue as this is a netbook and i'm not expecting a mini deep blue here. but the main reason i'm posting is because i believe i messed up my partition. I keep getting this error message when running computer janitor.

Failed to run computer-janitor-gtk as user root.

Unable to copy the user's Xauthorization file.

I read up that this could be because of an error i made while partioning my drive. I left 4 gigs for the root directory, 12 for my home folder, and 4 for my swap thinking it would be enough but it filled up quickly with updates and a few programs. when I downloaded my last program (amarok) i had multiple warnings for low disk space, but it never completely filled up. i was trying to delete files but i didn't know which were system critical and I didn't want to break my ubuntu even more. anyways when I tried to run Gparted I got the same message about the xauthorization file again. I really don't want to re install and reformat again as this will be my third time... so any advice you unix wizards can bestow on a noob?

thanks in advance.
Hi, I have 40 gigs for my root partition because a few years ago I went with what was recommend like 4 I think and I had to reinstall ubuntu to give all my partitions more space. You need 2 for swap but the other partitions are very small your home partition is where most things are stored you need it to be large if you plan on putting music,movies or installing very many programs. Aslo I would not use computer janitor, I have used it before and it will tell you things are not needed but sometimes they are, and that caused me a problem.

---

### Post by Paqman on 2011-06-07
How full are your partitions? Emptying your trash should free up some space in /home, to free some up in your root your can do the following:
```

sudo apt-get autoremove
sudo apt-get clean

```

This will get rid of any unneeded packages and then dump the package manager's cache. Should free up a little bit of space quickly. After that the thing to do would be uninstall old kernels. You can do this in Synaptic, filter for installed packaged starting with "linux-image" and completely uninstall all except the latest one.

---

### Post by Bucky Ball on 2011-06-07
> **Paqman said:**
> ... filter for installed packaged starting with "linux-image" and completely uninstall all except the latest one.

And linux-headers.

---

### Post by RabidGoat on 2011-06-07
Thanks for the info but now I'm faced with another problem. After I shut down last night and tried to start up this morning, I am unable to log in. I get an error saying that gnome power manger configuration defaults installed incorrectly and I am frozen at the log in screen. I can't even see my mouse right now... This happened before and I just reinstalled to solve it but like I said earlier I really don't want to do that again. If I use my live disk to backup my files I can't access my drive. I was always a linux advocate with limited knowledge but this is killing my faith here. Is there a safe mode option to fix this?

Edit* tried rebooting and not frozen anymore, but I get the same error when trying all options such as failsafe gnome and the like.

---

### Post by RabidGoat on 2011-06-07
To answer about my drives. I have a 20 gig (4 and a 16 seperately) ssd. My 4 gig has 0 bytes free and the 12 has about 8. Don't know what to delete from the root to make room and I can't run those options as I am on a live disk and I don't think it will allow me to access my original install. I can backup my files now, but once I do I'm not sure how to partition my drive to avoid this again as my ssd is tiny in the first place. Should I just give the larger ssd 10 or so gigs and work with a fragmented filesystem after that and rely on an external + thumbdrives?

---

### Post by RabidGoat on 2011-06-07
To answer about my drives. I have a 20 gig (4 and a 16 seperately) ssd. My 4 gig has 0 bytes free and the 12 has about 8. Don't know what to delete from the root to make room and I can't run those options as I am on a live disk and I don't think it will allow me to access my original install. I can backup my files now, but once I do I'm not sure how to partition my drive to avoid this again as my ssd is tiny in the first place. Should I just give the larger ssd 10 or so gigs and work with a fragmented filesystem after that and rely on an external + thumbdrives?

Also the root is ext3 and home is ext4, no idea what that means functionally, or if it even helps.

---

### Post by snowpine on 2011-06-07
I highly recommend opening the System Monitor and figuring out *what* is using up all your CPU cycles. Without this information it is difficult/impossible for us to help you troubleshoot. And of course, if your root / partition is full (it appears to be) you'll have all kinds of problems.

You can get support for Easy Peasy here:

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

Here is a good forums specific to the EEE 901:

[http://forum.eeeuser.com/viewforum.php?id=53](http://forum.eeeuser.com/viewforum.php?id=53)

My understanding of the 901 (never used it personally) is that the 4gb SSD is fast and the 16gb is very slow. Therefore for best performance you should install completely to the 4gb and use the 16gb only for storage of personal files and documents.

Personally I would recommend a fresh reinstall of the current Xubuntu or Lubuntu release; these are two lightweight (under 4gb) versions of Ubuntu that are popular and well supported here. I have never used EasyPeasy, it is not supported on ubuntuforums.org, and it looks like their last release was over a year ago.

---

### Post by RabidGoat on 2011-06-07
thanks, that does help. I was getting somewhat tired of easypeasy with it not actually having a desktop but it was manageable. I assumed it was a ubuntu product as the name is everywhere inside. But if I were to go with one of those, how large should I make my swap space? I heard it should be 2x size of ram. also, will there be enough space in the root directory for additional programs? Or can I install them to the home/other partitions if it gets close to full? Again, thanks for pointing me in the right direction, I really just want a quick lightweight platform that has a good foundation / support base. Maybe once I'm more familiar I will try dsl or something but I'm very noobish with the penguin right now.

---

### Post by JKyleOKC on 2011-06-07
With 2 GB of RAM, I would make the swap partition about 2.1 GB if I intended to use Suspend or Hibernate. I have 3 GB of RAM on this machine and gave it a 4-GB swap partition, which has never been used at all. If you don't plan to suspend or hibernate, 1 GB ought to be plenty -- and probably, like mine, will never be used.

I would put it on the larger SSD, too, to leave as much space as possible for installation and updates to system programs on the smaller one.

Welcome aboard!

---

### Post by dFlyer on 2011-06-07
> **RabidGoat said:**
> thanks, that does help. I was getting somewhat tired of easypeasy with it not actually having a desktop but it was manageable. I assumed it was a ubuntu product as the name is everywhere inside. But if I were to go with one of those, how large should I make my swap space? I heard it should be 2x size of ram. also, will there be enough space in the root directory for additional programs? Or can I install them to the home/other partitions if it gets close to full? Again, thanks for pointing me in the right direction, I really just want a quick lightweight platform that has a good foundation / support base. Maybe once I'm more familiar I will try dsl or something but I'm very noobish with the penguin right now.

Size of your swap really depends on how you use your computer these days. Most modern computers have gigs of ram, usually 2 or more. I find that a swap equal to my ram or 1 1/2 time so if I have 2 gig of ram my swap is 3 gig. Again it's mainly a personal choice. One thing I did notice is you're running a 20 gig linux system. I would recommend that you that you use / partition only and not have a separate home folder, this will give you a little more playing around room, between your root and home folders.

---

### Post by snowpine on 2011-06-07
> **RabidGoat said:**
> thanks, that does help. I was getting somewhat tired of easypeasy with it not actually having a desktop but it was manageable. I assumed it was a ubuntu product as the name is everywhere inside. But if I were to go with one of those, how large should I make my swap space? I heard it should be 2x size of ram. also, will there be enough space in the root directory for additional programs? Or can I install them to the home/other partitions if it gets close to full? Again, thanks for pointing me in the right direction, I really just want a quick lightweight platform that has a good foundation / support base. Maybe once I'm more familiar I will try dsl or something but I'm very noobish with the penguin right now.

I recommend:

4gb / (root) partition on the fast drive
data partition on the slow drive
no swap
no separate /home partition

You are correct that 4gb is not very much space; you'll need to start with a lightweight install (such as Xubuntu or Lubuntu, or even a [minimal install]("http://www.psychocats.net/ubuntu/minimal")) and be very careful what you add.

Did you check out the 901-specific subforum at eeeuser.com (link above)? 

ps DSL is a dead distro and will not have good support for your EEE.

---

### Post by RabidGoat on 2011-06-07
Thanks for the info. Will do about the swap space. Any idea how large the installation is for either of those releases? I am downloading lubuntu now with unetbootin to make a usblivedrive but I can't seem to run the unetbootin executable file... Maybe I should just quit computering altogether lol. But I guess I can always use my dads super slow XP machine. And thanks for the warm and informative welcome. All hurdles aside I still feel linux is more rewarding than windows. I just have a literal metric ton of questions. But I will follow the #1 rule of message boards and search first. 

Anyways thanks guise.

---

