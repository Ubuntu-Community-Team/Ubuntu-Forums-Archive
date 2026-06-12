---
title: "I'm new to Ubuntu so I have some questions."
date: 2011-04-29
forum: New to Ubuntu
---

### Post by NARWH4L on 2011-04-29
Introduction:
 
About a year ago (or maybe sooner), I download Ubuntu 10.X (I can't remember the name). I liked it, but at the time I didn't know how to or what HD partitioning was, so I was left with a Ubuntu system that couldn't do anything because there was no space for operation except for the OS itself. (I was dual-booting with Windows).
 
I did all that on my old laptop with 700MB of RAM.
 
Today:
 
I wanted to get the newest release of Ubuntu (11.4) on my Desktop Computer, which has 500MB of RAM. I installed it on my computer with Wubi, the windows installer, and the performance was terrible. It took up to 30 seconds to load FireFox, and over 10 just to load the settings. I don't think this is right. 
 
I know that Ubuntu 10.X worked fined on my 700MB Laptop, but it was extremely laggy on my Desktop. 
 
My question is:
 
If I install it on my destop via CD or USB drive, would the performance be better or do I need a higher RAM amount?
 
Thanks.
 
(I know I sound like a total Newbie, but I want to get into Ubuntu as a replacement to Windows XP.)

---

### Post by NARWH4L on 2011-04-29
:confused: Anybody have any ideas/suggestions?

---

### Post by NARWH4L on 2011-04-29
-------

---

### Post by damnupdates on 2011-04-29
i think a upgrade in ram is needed. i have not been on >500m for 6 years. dont even know if programs except windows xp work properly with that amount of ram.
thankfully ram is cheap. can get 4 gb for $50

---

### Post by overdrank on 2011-04-29
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by K_45 on 2011-04-29
Try Lubuntu, a Debian netinst, or an Ubuntu minimal install. If you choose the last 2 options, try XFCE4. XFCE4 is only slightly fatter than LXDE.

---

### Post by cymbaline42 on 2011-04-29
You will need to upgrade your RAM for smoother performance on Ubuntu Natty.  

If you are looking for a lightweight version of Linux to run with your current RAM, try Puppy Linux.

---

### Post by kalos on 2011-04-29
If you install it as a replacement to Windows, it should be faster. (Or even as a separate partition -- so long as you have enough space for a big [swap partition]("https://help.ubuntu.com/community/SwapFaq").)

[Ubuntu wiki mentions]("https://wiki.ubuntu.com/WubiGuide") that "Poor disk performance [with Wubi] is usually due to a fragmented drive or to a low amount of memory (frequent swapping)." (And it has a fix: defragmenting your ntfs drive).

Phoronix has a [Wubi performance article]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1") for Ubuntu 10.10. Wubi doesn't fare well.

So if you're okay with losing that Windows install and everything on it, just go for it with Ubuntu! You're meeting the [recommended requirements]("https://help.ubuntu.com/10.10/installation-guide/i386/minimum-hardware-reqts.html") for RAM, so it shouldn't be too terrible.


However, I'd agree with K_45, that you should look into xfce. You can also try [Xubuntu]("http://www.xubuntu.org/").

---

### Post by alayoyo on 2011-04-29
Yes, I found Lubuntu to work much better on my ancient laptop than anything else i tried.

---

### Post by I2k4 on 2011-04-30
I've been running Lubuntu 10.10 on "persistent" Live USB after experiments with other 10.10 versions. Another vote for Lubuntu as the slickest lightweight version though you need to learn some Linux basics as there is less user-coaching than in the mainstream versions. Tried the new 11.04 the same way, and found it much slower (also not wild about Unity interface and don't need all that preloaded software.)  

My main tip from a few months of running Live USB on a weak machine is, where possible, to set software preferences for caches and swap files (as in FireFox about:config, or GIMP Preferences) to the hard drive instead of accessing the USB or RAM. Also found the various "pipelining" tweaks for FireFox (google "about:config tweaks") still apply to speed up version 4. 

Finally, forget about updates during the testing phase, and when deleting or adding software with the Synaptic manager, do them one or two applications at a time since the slow USB can't handle too much going on at once.  With so many versions out there, Persistent Live USB is a blessing for no-risk trial and error.

---

### Post by lukeanders70 on 2011-04-30
I would probably go for the RAM upgrade because even if you could get Ubuntu 11.04 working smoothly you wouldn't be able to run most programs such as games, powerpoints, videos ect. However, if you really don't want to upgrade I would suggest downloading an earlier version of Ubuntu especially if it is made for netbooks (there is a chance that you could use the RAM from your laptop to upgrade your desktop but, its unlikely and you would no longer have a laptop

---

### Post by JayKay3OOO on 2011-04-30
I took this RAM readings from my laptop with 2GB ram on Xubuntu and my PC with 4GB RAM (32bit + PAE) for your help in their recorded states.

Xubuntu 11.04 uses 440MB RAM with ubuntu software centre, terminal (installing an application) and task manager open

Ubuntu 11.04 uses 940MB RAM with 2 chromium tabs & last FM plugin, archive manager and terminal open with apache 2 server installed.

(These are still less than win 7 that idles at 600 - 700MB)

Chromium is a resource hog (like all the top browsers) so midori or rekonq might use less.

I think with 1GB ram Ubuntu 11.04 would be ok with a 1GB swap partition or try something like Joli Cloud, i've run that fine on a dell laptop with 512MB ram. It has an old version of Ubuntu as a base - well, the 2GHZ processor can't do 1080p youtube streaming ;)

Puppy linux is great for old systems too. The iso is only 160MB and most apps work with it. I've heard great things about damn small linux too.

---

### Post by K_45 on 2011-04-30
> **JayKay3OOO said:**
> I took this RAM readings from my laptop with 2GB ram on Xubuntu and my PC with 4GB RAM (32bit + PAE) for your help in their recorded states.

Xubuntu 11.04 uses 440MB RAM with ubuntu software centre, terminal (installing an application) and task manager open

Ubuntu 11.04 uses 940MB RAM with 2 chromium tabs & last FM plugin, archive manager and terminal open with apache 2 server installed.

(These are still less than win 7 that idles at 600 - 700MB)

Chromium is a resource hog (like all the top browsers) so midori or rekonq might use less.

I think with 1GB ram Ubuntu 11.04 would be ok with a 1GB swap partition or try something like Joli Cloud, i've run that fine on a dell laptop with 512MB ram. It has an old version of Ubuntu as a base - well, the 2GHZ processor can't do 1080p youtube streaming ;)

Puppy linux is great for old systems too. The iso is only 160MB and most apps work with it. I've heard great things about damn small linux too.

 XFCE4 here uses 170MB with a terminal open. If you want lightweight Xubuntu is definitely not it.

---

