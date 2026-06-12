---
title: "setting up a file server"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by xolot1 on 2006-08-06
question: how would i set up an efficient, stable, useful file server to be used by my ubuntu laptop?

background: i got a laptop for college - 60gig i think, and 25 are being used by windows, then a number of other smaller partitions for ubuntu.  i was looking to get another larger harddrive for storing music, video, tv, etc. i picked up a 60gig internal IDE at a yardsale ($15) and an old computer at another for $5.  150mhz 64ram 6gig HD. by combining the two, i figure i can save the $30 or so id need for an enclosure for the IDE HD.

at the most basic level, i could just run ubuntu on the older computer 24/7 with the 60gig shared. what is a more efficient solution? i know very little about networking, etc but am interested in learning.

---

### Post by greenstar on 2006-08-07
That's a pretty meager box, and minimal RAM. If you do make it happen, I don't think it will be with Ubuntu. Maybe with [Puppy]("http://puppyos.com/") or [Damn Small]("http://www.damnsmalllinux.org/").

Keep us posted on your results, I'm interested to see how this turns out. I'll help where I can. 

Greenstar

---

### Post by sitedesign on 2006-08-07
That box will work, make sure you download the server version.

You will not have any graphical environment so you might like to install webmin ([www.webmin.com](www.webmin.com)) They have .deb package of it now which works fine.

That should get you rolling.

---

### Post by darrenm on 2006-08-07
That spec should be fine with no X running.

As said use the server install CD and run ```
sudo apt-get install samba samba-common
``` then edit the /etc/samba/smb.conf to your liking. 

Really easy, Samba rules and your boxes CPU wont even get touched :)

---

### Post by xolot1 on 2006-08-07
thank you. sounds like this should work out pretty well.

now i have to figure out how to flash the bios so it will recognize a 60gig HD, not an 8. thanks again for the replies.

---

