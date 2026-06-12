---
title: "Questions about Ubuntu"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by mystvearn on 2011-01-07
Hi,

I have tried ubuntu like 10 mins at a time as a final resort when repairing laptops where the owner's does not have their OS dvd's but have never used it as my main OS. On the base it looks a lot like an apple OS and I can find my way around quite easily. I now have an old Dell inspiron laptop with Vista basic on board (2 gb ram, 5400 rpm hd, 80 gb HD, Intel Centrino duo T1500) which I don't know what to do about. I wanted to trade in this laptop at PC world UK for cash towards a new laptop (when my wife wanted her laptop upgraded), but it seems that no UK retailer are making offers for cashback at the moment. So practically I'm stuck with an old laptop which I don't use since my main pc is a W7-64bit desktop. My questions are:

1. Does anyone know a good website/online guide to get me speed up with the Ubuntu and Linux OS? Also a site which teaches execution commands in what seems like the same command prompt (DOS) present in windows

2. Is it be possible to install windows software directly on Ubuntu? There are some specific windows software which need. I am sick of vista basic, (or maybe the slow 5400 rpm drive). I did a google search, saw it was possible, tried it myself and failed. It seems that the execution commands are different from windows even though it seems that both have a DOS like layout. 

3. I'm thinking of changing the 5400 rpm 80 gb hd for a SSD drive. Does Ubuntu have TRIM support feature which is present and natively supported by W7?

---

### Post by trinitydan on 2011-01-07
1. Most of your questions will have been answered in the forums previously, so the trick is learning how to search for what you need.  I have better luck personally searching directly from google then trying to use the search on this forum.

2. In a nutshell, no, Windows software does not run well in Ubuntu (although you can run some programs in [Wine]("https://help.ubuntu.com/community/Wine")).  For the most part I would suggest you try to learn to use open source software alternatives to accomplish your tasks whenever possible and/or dual boot to keep your Windows functions you need.  Also it is really more of a Unix like file system which is more like what you would find on a Mac.

3. Don't know.

Welcome to Ubuntu Forums!

---

### Post by A_M_S on 2011-01-07
Welcome to the forums.:)
1
For some videos try [this]("http://ubuntuclips.org/collections_2.htm")

To nice collection of tutorials [this]("http://www.psychocats.net/ubuntu/index")

For a intro manual [this]("http://ubuntu-manual.org/")

For bash try:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/intro_10.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/intro_10.html)
[http://www.gnu.org/software/bash/manual/bashref.h](http://www.gnu.org/software/bash/manual/bashref.h)
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)
2
You can install a virtual machine like [virtual box]("https://help.ubuntu.com/community/VirtualBox") or install [wine]("https://help.ubuntu.com/community/Wine")

Hope that helps

---

### Post by hansolo4949 on 2011-01-07
answers to your questions:

1. you should look around Ubuntu forums. Many of your questions will be answered here.

2.it is possible to do it, via wine, but some programs might not like ti on wine, or might not be compatible with it.

3. I don't know, but my guess is that you might be able to download a package for trim support, but you should investigate that before you sink a lot of money into an SSD. 

 Welcome to Ubuntu!


 hansolo4949

---

### Post by cogier on 2011-01-07
With regard to question 1/. As trinitydan says use Google, search for BASH commands. The Linux Terminal is much more powerful than DOS.

Question 2/. If you want to run Windows software use Windows. If you want to experiment with the Linux look for the many and varied alternatives available. Enjoy the challenge of exploring the alternatives.

Question 3/. No idea. But I use a SSD on my Dell M1330 with 10.10 and it takes 15 seconds to boot to a USABLE desktop.

Enjoy open source software, try to think outside of the MS Windows box.

---

### Post by aytech on 2011-01-07
Hi, 
Little input from my side:

1. Specific to Ubuntu: [Ubuntuguide]("http://ubuntuguide.org/wiki/Main_Page")
2. No, you can not run Windows software natively in Linux. Terminal in ubuntu is like extended DOS thing in Win, but syntax of commands is different, although there're similarities
3. Whats the advantage of this?

---

### Post by zach33 on 2011-01-07
Question 3: Right now, I don't think the current release has TRIM support but I think they are working on it for later releases.

---

### Post by mystvearn on 2011-01-08
Thanks all for the replies.

2. When I go to conferences, they require windows to install their software so I can't just ditch windows. 

I just figured out that Vista does not support TRIM and I'm looking to offload this computer as upgrading to SSD is not really worthwhile on this old system. 

I have not yet given up on this old system. Since its an old Dell inspiron 1420, I can open the processor area, and ram area, I might thinker around with it. See if I can find a mobile centrino duo and extra ram online. If all works, and hopefully SSD will be supported by linux, there is little sense for me to look for an upgrade. Right now I'm doing a clean install, cause after all vista upgrade,s it takes 34gb of hd space, which just does not seem right...

---

### Post by 3rdalbum on 2011-01-08
> **mystvearn said:**
> On the base it looks a lot like an apple OS and I can find my way around quite easily....


...Also a site which teaches execution commands in what seems like the same command prompt (DOS) present in windows...

...different from windows even though it seems that both have a DOS like layout.

Ubuntu is really nothing like the Mac OS, nor anything like Windows. You probably associate the command-line with MS-DOS; but this isn't anything like MS-DOS (correction: MS-DOS is nothing like Unix/Linux. MS-DOS is a rip-off of CP/M, which was still released after Unix).

That's just something to note. Superficially, Ubuntu and OS X both have the close button in the top-left corner. Superficially, Ubuntu and Windows programs have their menus underneath the title bar. In actual operation and "underneath", no Linux distro is really anything like OS X or Windows. It'll be much easier for you to grasp Ubuntu if you know that you're a newbie.

---

### Post by Frogs Hair on 2011-01-08
Links I found useful. 

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

[http://linuxcommand.org/](http://linuxcommand.org/)

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by waynefoutz on 2011-01-08
I've been using Ubuntu for 5 years now, and I know less than 5 commands when I'm in the terminal. I very rarely use it, and as Ubuntu has gotten more mature, the need to launch a terminal windows has decreased dramatically. Back in the early days it was common, not so much anymore. I wouldn't let the lack of command line expertise scare you away from Ubuntu, the truth is you will probably rarely use it anyway.

---

### Post by Phillip Spencer on 2011-01-08
> **mystvearn said:**
> 
2. When I go to conferences, they require windows to install their software so I can't just ditch windows. 

I am in a similar position with a client where I could only get remote access to their system via Windows.  It is the only reason I keep it on my current laptop.  The answer is to set it up to dual-boot. Make sure you install Ubuntu second though as Windows assumes it will be the only OS!  

As a word of warning, watch out for physical partition limits (max four) and install Ubuntu on an extended partition if appropriate.  Search the forums for guidance on this as it is much easier to do right first time round than fix a partition problem caused by haste.  I found out the painful way deleting a Windows recovery partition I thought I did not need and then found the PC would not boot at all.

BTW, For the past couple of years I have used Ubuntu on five different PCs / laptops. Apart from fixing problems like the partitioning I have hardly had to use terminal commands.

Good luck,
Phillip

---

