---
title: "frustrated"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by thinker on 2006-09-08
Ok... so, I'm still a bit of a noob to linux; booted for my first time on unbuntu about a week ago, and have spent that week trying to figure out my wireless connection... I have read just about all the wikis and troubleshooting guides, not to mention most of what is on the forum.  Still, no avail, though I think I have been able to more accurately diagnose my problem. I apologize if it seems like the questions about this issue are endless... I am just very frustrated:) and wanted to get as clear an answer as possible.  Thanks in advance for dealing with me:)

I am running a Dell Inspiron 1150 laptop, with a Dell wireless 1350 mini-pci adapter (as it tells me) In linux, opening the networking gui, the wireless is displayed (as eth01, I have disabled the others) yet I still have to activate it myself everytime... Running the ifconfig in the terminal, it gives me an inet addr, but running iwconfig, it says the access point is invalid.  Which leads me to a scary question...

I do not have a router; I connect (barely) to an unsecured signal from one of the nearby university buildings... works fine on windows XP, but does linux need a router? It would seem as if there is some link missing; i.e. an IP address of a router or other connection device...

So, I guess my two main questions are; can I still connect to the signal without a router?  And, if so, what is missing?  It seems as if linux recognizes my device; I have done all the ndiswrapper and getting the bcm43xx drivers and everything I could find in other posts/the ubuntu help page, to no avail.  Am I missing something really stupid?  Is there some install or activate step I haven't done?  Or is this something that will need a more complex script to get around the issue?

Again, thanks so much for your help.  I find all of this so interesting (with the exception of things not working:)) and your feeback would be much appreciated.  

-thinker

---

### Post by cdgrocott on 2006-09-10
I was having the same problem with my wireless card using the bcm43xx drivers. jhuff seems to have found a way around it though for Belkin devices: [http://ubuntuforums.org/showthread.php?t=187004]("http://ubuntuforums.org/showthread.php?t=187004")

I think it's a case of the bcm43xx drivers not playing nice, blacklisting them and finding a windows version of your driver seems to be the way forward.

Hope that helps.

---

### Post by bmasephol on 2006-09-10
I have the same wireless card (Dell 1350) I'm using with my laptop (!Dell).  

I've used ubuntu straight out of the box and it detects the wireless card and it seems to work except I could only ever get it to connect to access points that had WEP enabled... I couldn't get it to connect to access points that had no security.  Tried forums, tried tinkering, but in the end never got it figured out.  Gave up on linux for a while... but I just got a hold of a Zonet Cardbus wireless card and just for fun I booted into ubuntu instead of winxp and shoved the card in and within 2 minutes I was connected to the wireless access point that I couldn't get connected to with the Dell card.

I think I'll just wait for an update or something and for the time being carry the Zonet card with me... I think I caught it on a rebate and it ended up  costing me like 15 bucks max.

---

