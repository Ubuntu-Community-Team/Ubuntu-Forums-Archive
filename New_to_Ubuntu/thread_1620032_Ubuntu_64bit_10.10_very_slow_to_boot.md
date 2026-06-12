---
title: "Ubuntu 64bit 10.10 very slow to boot"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by dagarshali on 2010-11-12
Hi,
I recently upgraded to 10.10 from 10.04 and I have windows 7 installed via dual boot. When I select ubuntu from the boot screen, I seen a black screen with a cursor blinking at the top left for many seconds, which is then followed by the purple screen. It will take some more time before I can get the log in screen. Once I enter the information, it take a number of seconds to get the desktop. Any ideas as to what to look for?

I have attached the bootchart for your reference.

Regards,
Vishwa

---

### Post by bryangwilliam on 2010-11-12
What do you mean by "many seconds"? My installation exhibits similar behavior but I would definitely not call it slow, especially in comparison to my Windows 7 boot time.

---

### Post by dagarshali on 2010-11-12
I mean the 10.04 boot chart would say about 25 secs. This one shows about 40 seconds. That is what made me say that it is very slow.

Vishwa

---

### Post by poyraza on 2010-12-11
I have the same issue with Ubuntu 32bit 10.10
I have Acer 1810T with Celeron.

First, Ubuntu was not booting at all. Then, I omitted and changed a line at Grub (namely deleted the search line, and changed the linux line by targeting the linux drive).  Since then, Ubuntu has been starting up but now, it starts up exactly in 3 minutes. 

Can you please suggest me how I can solve this?

Cheers!

---

### Post by raydeen on 2010-12-19
Same issue here with the 32 bit version. I had 9.04 on my Eeepc and upgraded to 10.10 when 9.04 support ran out. Much slower boot time. I'm suspecting a difference between Grub and Grub2? I'm running it off an 8 gig SDHC card. 9.04 was a screamer on the card. 10.10, not so much. A minor annoyance but speeding up the boot would be nice if it's possible.

---

### Post by Jack Brown on 2011-01-25
probably not grub2... grub2 on a 10.04 (32bit) boots up ubuntu quickly....

that's why 10.10 x64 booting up so slow is puzzling. (it's supposed to be fast)

(had to go into ubuntu recovery mode and use the recover grub option when ubuntu wont even boot after recent update)


possible reasons/solutions could be older hardware / higher system requirements (in this case would need to install another edition / distro)?

some tuneup changes? (if you know how, starting with startup programs..) 

wait for more updates?

---

### Post by poodoopealeoaph on 2011-01-25
Since you had 10.04 in a dual boot situation and upgraded, it may have messed up your grub installer or it could have done a number of things to your system (ie. partition rearrangement, losing certain core files, uncompatable or old drivers.).

I would recommend to try to wipe the partition that you have ubuntu on and try to install with 10.10. Any upgrade I've tried has usually had problems. So, try the straight up install and see if it works better.

By the way, I use ubuntu 10.10 64bit on my laptop and it boots from the time I push the button to being at the desktop in about 15 seconds. I'd also like to add that my system isn't that spectacular, 2.19 ghz dual core with 4 gb ram...

---

### Post by bandoba on 2011-04-05
Yet another user confirming similar problems on ACER T180. I am running Ubuntu 10.10 and still observe very slow boot.

---

