---
title: "Acer Aspire One, Vista - How to load Ubuntu"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by John Bo on 2009-10-07
Hi
 
I bought an Aspire One AO751h with Vista 3 weeks ago. It's as slow as thick treacle. Over 30 Windows updates (in 3 weeks). It hangs and it gets confused...  I thought it was time to explore Ubuntu and Linux.
 
I want to create a partition on my 250Gig drive and dual boot Ubuntu/Vista. (I may need a Microsoft product for some of my many legacy windows programs that use various UART and USB links)
 
I can't load UBUNTU Netbook Remix onto my USB stick.
 
1. I am a slightly above average computer user, but I don't know Vista (I avoided it on my other PCs because of bad press). I have used and cursed Windows since V2.3, long before 95 and 3.1, good time for a change.
 
2. I have googled and read for 2 days. Very little on Vista and I am confused by the stuff on XP. Great YouTube videos on Ubuntu up and running but that just makes me even more frustrated!!!
 
Please I beg, can someone direct me to a simple, step by step proceedure for getting Ubuntu - dual boot onto my Aspire One.
 
 
Regards

---

### Post by Merk42 on 2009-10-07
Why the heck did that netbook come with Vista?

What problems were you having for getting Ubuntu Netbook Remix on your USB?

You should be able to follow the instructions [here](https://wiki.ubuntu.com/UNR).

Two things to note.[list]
[*]Just because you have a netbook, you do not need to use the netbook remix, UNR is about changing the interface to maximize screen real estate, you could very well use a normal installation of Ubuntu
[*]The next version 9.10 Karmic Koala will be out by the end of the month, you may want to wait for that[/list]

---

### Post by Temposs on 2009-10-07
Those instructions assume you're already using Ubuntu.

Try these instructions instead:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Scroll down to the instructions to UNetbootin. Follow the instructions for that first.

Once you create the USB installer on your USB drive, you have to set your BIOS to boot from the USB drive before the hard drive. If you can do that, then the installer will boot.

---

### Post by Kapitän Rotbart on 2009-10-07
Firstly, back everything up.

Secondly, if you still want a windows partition, it would probably be best to reinstall windows (this is the easy way). Again, back everything up. Give windows vista maybe 50 GB on that 250 GB disc (Vista needs at least 40 GB as a primary partition, you can get it down to taking 35 GB after you remove a bunch of things, but still it takes a lot of space for the OS alone). Vista is pretty good for creating backup discs. Alternately, get the drivers, and install winXP on it (a 10 GB partition would already be plenty, and you can get stripped down XP's like TinyXP). Now, if you don't want to reinstall Vista or install XP, then you still have (less desirable or more difficult) options. You could get Ubuntu to try to resize the Vista NTFS partition (something I haven't succeeded at yet, despite trying on multiple occasions) or installing Ubuntu via Wubi (easy to install, it installs itself as a windows application so it's easy to uninstall, however it's not as fast, can't really hibernate/suspend, and it complicates things for the bootloader). Hence I strongly recommend reinstalling windows.

Thirdly, you could wait for Ubuntu 9.10 Karmic, but don't wait for it, get Ubuntu 9.04 now (I started using Ubuntu back in version 7.04 just weeks before 7.10 came out, I knew I had to switch, I wasn't going to test some beta OS and I learned a few tricks that were necessary to get 7.04 to work whereas in version 7.10, it was out of the box). This is also the easy part. You already reinstalled Vista (or installed XP) on a smaller partition. Seeing as you're stuck learning about partitioning your hard drive, explore your options! Exploring is my recommendation to any n00b that has to partition. You may want a backup partition or simply a partition where you stash misc files that you don't want to lose when you install the latest Ubuntu every 6 months (mount it to /media/whatever), you may want to create a partition just for your /home directory (saves you from reconfiguring your prefs for each app you use every time you install some Ubuntu). An other thing about Ubuntu...there are distros Ubuntu-based (tweaked Ubuntu, let's say) that make everything work out of the box on the Aspire One. This includes eeebuntu (for the eee pc and the one) and Linux4One (an Italian-made distro also available in English or any language for the Aspire One). Also it's up to you whether you use the netbook remix, though on the Aspire One I'd recommend it!

Fancy that! Now you have a dual boot! If you think you don't really need windows or you think you would just need it for one application or two, see if it works in Wine. You may not have to dual boot.

---

### Post by mapes12 on 2009-10-08
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by John Bo on 2009-10-08
Thanks guys
 
UNetbootin solved my problem. Once the USB stick was formatted, the rest was painless.
 
I had tried all the other options discussed and several others. I had even learned how to get that Russian, DOS based command prompt USB formatter to run - but that appears to be where my problem was.
 
I had tried to downlosd UNetbootin before but it requires a US state, business type and valid US phone number - from a South African. (Typical STUPID data validation!!! Is this absolutely validated, absolute garbage ever used).
 
Thanks for the tip on Wine. Previous searches show that it works with my MCU programmer but not with my oscilloscope software.
 
I suppose this makes me part of the Linux community - Oops, I've crossed over, I've become a computer nerd...
 
Regards
John

---

### Post by LewRockwell on 2009-10-08
[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

