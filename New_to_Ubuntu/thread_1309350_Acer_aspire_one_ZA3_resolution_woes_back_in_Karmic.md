---
title: "Acer aspire one ZA3 resolution woes back in Karmic"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by CheeseEatingBulldog on 2009-11-01
I have just reinstalled my girlfriends acer aspire one (ZA3) and like in jaunty it cant give me the larger resolution 1366x768. In jaunty I solved this by adding the [https://launchpad.net/~ubuntu-mobile/+archive/ppa]("https://launchpad.net/~ubuntu-mobile/+archive/ppa") mobile teams repo and adding some packages.

However it appears that they only have a jaunty repo, which I tried but that just removes bucketloads of packages.

Can anyone point me in the right direction as to how to fix the resolution issue.

Thanks

(previous thread which helped me solve it in jaunty is [here]("http://ubuntuforums.org/showthread.php?t=1180151")

---

### Post by LewRockwell on 2009-11-01
turn compiz off and reboot a couple of times

we know it sounds silly but yesterday we noted several problems/trouble-calls being "cured" just by rebooting several times

some reports have indicated that wireless card issues are hit-and-miss and we see this personally on the tech bench(this behavior was also evident in previous versions of ubuntu)

.

---

### Post by CheeseEatingBulldog on 2009-11-01
Compiz isnt on to start with. And wont turn on. I dont see rebooting as a valid solution, as what do you suggest, to use the laptop I have to reboot untill I get the right resolution?

I cannot change the resolution from 1024x768 to anything.

Any ideas?

edit: I just rebooted 3 times and no change. Still cant choose a different resolution.

---

### Post by CheeseEatingBulldog on 2009-11-02
Last night I rebooted about 15 times to see if anything would change, but no. Is there anyone who knows howto add the ppa of the mobile team as a karmic repo, without it removing a bucketload of packages?

---

### Post by CheeseEatingBulldog on 2009-11-07
Anyone have an update on this yet?

---

### Post by whitefort on 2009-11-07
Sorry I can't help - just offer you the 'moral support' of knowing you're not the only one with this problem.  This has been driving me crazy too.

If I find a solution, I'll report back to this thread and share it.

---

### Post by CheeseEatingBulldog on 2009-11-07
Thanks. I think it is somewhere in the driver, the intel one is installed, yet a vesa driver is running as seen here by compiz-check:

```
Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
 Driver in use:         vesa
 Rendering method:      AIGLX


```

So how does one configure the display these days. Editing Xorg.conf is out as it no longer is there. The display option gives only one choice so where is an override for the system?

Surely "Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)" is nothing more than an intel chip, so why is the driver not active? Hardware drivers give no propriatry options either btw.

---

### Post by CheeseEatingBulldog on 2009-11-07
Right, fixed it ...found [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/426791]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/426791") this bug, which lead me to [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") that fix. Easy peasy. 

Download the the packages, of which I think 3 .deb files. Install them and follow the guide. There is no xorg.conf, but I put mine (created) in the usual /etc/X11/ directory. Reboot and wonderful resolution!

EDIT: I tried [http://ubuntuforums.org/showthread.php?t=1014534&page=76]("http://ubuntuforums.org/showthread.php?t=1014534&page=76") the xorg.conf at the bottom of the page, as another thread suggested it might add 3d and compiz. It didn't as it gave me a distorted disply, but then compiz didn't work for me in jaunty either.

---

### Post by LewRockwell on 2009-11-07
[http://www.linuxjournal.com/content/how-kick-your-friends-face-gma500](http://www.linuxjournal.com/content/how-kick-your-friends-face-gma500)

[http://www.linuxjournal.com/content/more-poulsbo-gma500-intel-and-community](http://www.linuxjournal.com/content/more-poulsbo-gma500-intel-and-community)

this should be fixed in the 9.10 release so that it "just works" out of the box


sad that millions of downloads and bittorrents will all need to be redone

.

---

### Post by Galaaladdiin on 2009-11-08
I'm a beginner on Ubuntu and I can't have your solution work on my ZA3 because I don't have the ubuntu-mobile.list in the first place! I guess it's because you have the ubuntu-mobile installed whereas I have the full version. True? Should I install first the mobile version or is there another way? Thanks!

---

### Post by CheeseEatingBulldog on 2009-11-08
> **Galaaladdiin said:**
> I'm a beginner on Ubuntu and I can't have your solution work on my ZA3 because I don't have the ubuntu-mobile.list in the first place! I guess it's because you have the ubuntu-mobile installed whereas I have the full version. True? Should I install first the mobile version or is there another way? Thanks!

It doesnt work like that. You start, as I did with a clean install of karmic, then download the packages I stated, double click the .deb files one by one and install them. 

Then open a terminal and 'sudo' all the commands one by one stated in the link, this will add the mobile repositories. Once you have done that, sudo apt-get update to update your repository list. 

Continue with the guide and it will tell you to place a file named xorg.conf (which you just create) (sudo gedit /etc/X11/xorg.conf) paste xorg example in file, save and close.

Reboot and you are done.

---

### Post by whitefort on 2009-11-08
> **CheeseEatingBulldog said:**
> Right, fixed it ....

Glad it worked for you!

Not for me, sadly... :-(

I'm pretty sure I followed the instructions to the letter, but the final result was a total inability to start X.

I've been tinkering all morning trying to fix it, but I'm just about to give up and re-install.

Since I'm re-installing anyway, I think I might just go back to Jaunty, and keep my fingers crossed that this is fixed when 10.4 appears.

---

