---
title: "Modem and Wireless Problems w/Feisty"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by RxRated on 2007-07-31
I have a Toshiba laptop dual booting xp and feisty.  The computer had no networking issues with edgy.  After upgrading to feisty, I have had 2 problems.  I have a realtek wireless mini pci card that feisty didn't recognize.  I learned on the forum that the drivers were blocked in feisty and updated the file.  Now, when attempting to connect to wireless, the connection stalls.  I then  
have to select "connect to other wireless networks" in network manager, and put in a fake ssid.
After searching for 10 seconds it stops searching and returns to no network found.  Then if I choose my network from the list, it connects and works properly.  I have to repeat this procedure every time I start Feisty.

When at work, I use a modem.  I always used KPPP and the modem is a smartlink.  Again, I had no problems with Edgy.  Now when I try to dial, I get a NO CARRIER error.  The modem is found when I run a query on it.  If I run the command $ sudo /etc/init.d/sl-modem-daemon restart 
then re-run KPPP the modem dials and works fine.  

Is there a "fix" for this, or even a way to run the modem command automatically when Feisty boots?  Could both problems may be related to network manager???

Thanks for any help in advance

---

### Post by Pogo_VA on 2007-08-01
I'm having somewhat similar problems with a SmartLink winmodem on my HP laptop; in fact, my thanks because your mention about doing the sl-daemon restart got me past the NO CARRIER message I was running into.

I ran across the following thread when doing a search with Scroogle:

[http://ubuntuforums.org/showthread.php?t=190728](http://ubuntuforums.org/showthread.php?t=190728)

It's a bit beyond me for now, but I will work with it later and hope that it might be something you could use.

Unfortunately, I'm now running into exactly the failure to dial out after ATDT that's mentioned in thread, but that may be fixed now with a better directed approach to installation or the newest driver (I hope).

Good luck.

--------------------------------------------------
We have met the enemy and he is us - Pogo

---

