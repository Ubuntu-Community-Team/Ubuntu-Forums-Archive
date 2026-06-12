---
title: "Ubuntu with pentium III processor"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by rajapandian on 2009-08-19
I am using pentium III processor with 256RAM.Can i use the latest version of ubuntu 9.04...please do help out:confused:

---

### Post by SoftwareExplorer on 2009-08-19
It should work, but you may have to use the alternate installer. Check out [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by zarthon on 2009-08-19
> **rajapandian said:**
> I am using pentium III processor with 256RAM.Can i use the latest version of ubuntu 9.04...please do help out:confused:
You can try Ubuntu off of a live CD. Boot it up and let us know if it works.  

Honestly though as much as I really like Ubuntu there are Distros for specialized situations. One is older hardware and low RAM. 

I would use [AntiX]("http://antix.mepis.org/index.php/Main_Page"). It is also derived from Debian (indirectly through MEMPIS) but it is specialized for older hardware. The default window manager is the main thing that saves RAM and overhead. It is not as user friendly but is fine for web browsing.

Ubuntu also has some remixes that may be good for low RAM.

Try and salvage RAM for your old box if it is not maxed.

---

### Post by SoftwareExplorer on 2009-08-19
By the way, welcome to the ubuntu forums.

---

### Post by bodhi.zazen on 2009-08-19
You can use it, but you are low on RAM and it will be slow.

Boot the Alternate CD and make a swap partition 512 Mb in size, then try booting the desktop CD.

IMO you are best off with either Xubuntu, Crunchbang, or a light weight distro such as Puppy linux.

---

### Post by azebuski on 2009-08-19
One of my spare computers is an old Compaq Deskpro PIII 450mhz with 258MB RAM and a 6gig HD.  It runs Hardy Heron just fine but it is pretty slow.

---

### Post by Ji Ruo on 2009-08-20
I have a laptop with 800MHz Celeron and 256MB ram which is running Ubuntu 9.04. It runs fine (considering the age of the hardware) as long as you aren't trying to do more than a couple of things at once. I used the live CD to install.

When you install, use ext4 for the filesystem (instead of the default, ext3) by choosing to partition the hard drive manually. It will give you a noticeable performance improvement with old hardware. I used 768MB for the swap partition.

---

### Post by binbash on 2009-08-20
You can run Crunchbang fine with that box (= ubuntu with openbox)

---

### Post by alexlafreniere on 2009-08-20
Try Xubuntu or CrunchBang, both will give you a lot more breathing room performance wise. And they both use Debian's apt package system , which is a huge plus for me.

---

### Post by nomnomnom on 2009-08-20
Upgrade your RAM to as much as your motherboard can take. It makes a BIG difference!

---

### Post by Bartender on 2009-08-20
+1 on nomnom's suggestion.

Stuffing the MB with as much RAM as possible will not only let you install from a LiveCD, but the PC will be much more responsive once the OS is installed.

I've got a 1GHz PIII.  Tried installing with just over 256 RAM and the thing sat there for half an hour with the HDD light flickering but no visible progress.  Bailed out of installation and stacked the RAM slots full, getting it up to 700+ MB RAM.  Tried again and installation went much faster.

If you don't want to add RAM, try the alternate install CD, and think about using Xubuntu or some other "lighter" OS.

---

### Post by cascade9 on 2009-08-20
> **nomnomnom said:**
> Upgrade your RAM to as much as your motherboard can take. It makes a BIG difference!
Yep, it will. Not as much as you could hope for..and watch out, most p3s are running intel 810/815 chipsets, and almost all of them have a 512MB ram limit.  

[http://en.wikipedia.org/wiki/List_of_Intel_chipsets](http://en.wikipedia.org/wiki/List_of_Intel_chipsets)

To the OP- I cant speak for 9.04 ubuntu, but I've run 9.04 xubuntu on a p3-800/192MB and a p3-866 with 256MB and 384MB. On the p3-800, its a bit slow and unresponsive, but not that bad. The p3-866 384MB is much much better :)

---

### Post by LewRockwell on 2009-08-20
yes, we would max out the ram and see how it does with some of the lighter distros

we use Puppy Linux on some of ours

.

---

### Post by egalvan on 2009-08-20
> **LewRockwell said:**
> yes, we would **max out the ram **and see how it does with some of the lighter distros

we **use Puppy Linux** on some of ours

.

+1 for both suggestions.

And adding one more....

research what the max CPU will go on your board...
search eBay for something faster...
P-III are usually dirt-cheap.
Local Mom&Pop computer repair shops are a good source for both RAM and CPU.

I upgraded a 766MHz HP to 1000MHz.
Made a good difference....
but not as good as the upgrade from 256M to 512M RAM.

---

