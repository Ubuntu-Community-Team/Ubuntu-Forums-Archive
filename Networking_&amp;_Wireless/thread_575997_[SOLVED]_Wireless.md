---
title: "[SOLVED] Wireless"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2007-10-14
I am having a lot of trouble getting my wireless network card to work.  I have a PC with a wireless network pci that I installed.  Linux seems to know it is there.  It shows up in the network panel and I have run a few commands in the terminal all of which report that the card is there.  Why can't I connect to the network with it?

---

### Post by scrooge_74 on 2007-10-14
Main question: which type of card you have, without that info nobody can help

---

### Post by f37u5g0d on 2007-10-14
I have a linksys card (make: broadcom).  Linux reports that my driver is "BCM4306" .

---

### Post by scrooge_74 on 2007-10-15
Now we can help

Try this links so you can check on yours, I think the first link should be the one for you

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)
[http://ubuntuforums.org/showthread.php?t=482555](http://ubuntuforums.org/showthread.php?t=482555)
[http://ubuntuforums.org/showthread.php?p=3045507#post3045507](http://ubuntuforums.org/showthread.php?p=3045507#post3045507)

---

### Post by f37u5g0d on 2007-10-17
So I was trying to install the firmware for my wireless card with the guide you found for me in that first link (thanks by the way).  I got to step 3 (install the bcm43xx-fwcutter) and I ran into a problem.  I entered the following code into the terminal "  sudo apt-get install bcm43xx-fwcutter " it went smoothly until the end when it tried to download something from a website.  

" Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:30:58 ERROR 404: Not Found. "

I guess that website hasn't been updated in a long time.  What should I do?  (I know my wired internet is working btw).

I through that address into my browser and it is "Nick McMahon" 's personal website.  There is no contact information.

---

### Post by scrooge_74 on 2007-10-17
I discover a few days ago about that, it seems the website went over his quota for data transfer.

That package is trying to download a driver call wl_apsta.o and bcmwl5.sys you can get them from [here]("http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.1.tar.gz") also.  They go here /lib/firmware

You can find more info on the Debian forum about the native driver

[http://forums.debian.net/viewtopic.php?t=7949&highlight=broadcom](http://forums.debian.net/viewtopic.php?t=7949&highlight=broadcom)

---

### Post by f37u5g0d on 2007-10-17
That link is dead.  (the one that says "here").

---

### Post by jbaerbock on 2007-10-18
If you have a broadcom may have to install the windows driver using ndiswrapper. Then blacklist the alternate driver that ubuntu attempts to use in its place.

---

### Post by scrooge_74 on 2007-10-18
> **f37u5g0d said:**
> That link is dead.  (the one that says "here").

Sorry it was working a few days ago, you could try searching for the individual files, the sys files is a windows file so you should be able to find it in your windows drivers disk.

I did not use ndiswrapper this time around, I just went with the linux driver, but then again each machine is different

---

### Post by f37u5g0d on 2007-10-19
I have the windows driver (BCMWL5.SYS).  That was on the windows side of my hard drive.  I searched around the internet a little for the other driver but I couldn't find it.  Any ideas for good websites to check?  I am also updating my system today (to ubuntu 7.10) maybe that will fix the problem.  Thanks btw for all your help.

---

### Post by jbaerbock on 2007-10-19
Yeah 7.10 works with wireless. The card is active, although it isn't wanting to connect at the moment lol.

---

### Post by f37u5g0d on 2007-10-23
Yeah, ubuntu def. reckognizes it's their but it's not connecting for me either.  Does anybody know how to fix it?  I tired a lot of the stuff in the previous postings but none of it worked.

---

### Post by f37u5g0d on 2008-02-27
I have took some time away from this project but I am eager to tackle it now.  Ubuntu knows I have a card and I am using the ndiswrapper.  I can attempt to connect to networks.  I choose connect to other wireless network on the network applet and it attempts to connect but it never makes any progress (i.e. 0%).  It evetually gives up.  How can I scan the area for available wireless networks?

---

### Post by f37u5g0d on 2008-02-27
I am an idiot and when I followed all of the how to's and so on but I used the .sys windows driver instead of the .inf.  All I had to do to get wireless working in ubuntu is follow the wireless troubleshooter in the documentation of the ubuntu website.  Wireless is now up and running for me! :) :) :) (P.S. linux + compiz fusion = better than mac os and windows _combined_.)

---

