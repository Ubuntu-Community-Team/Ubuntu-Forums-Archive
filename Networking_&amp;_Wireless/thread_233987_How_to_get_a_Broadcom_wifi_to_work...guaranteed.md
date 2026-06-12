---
title: "How to get a Broadcom wifi to work...guaranteed"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by csann on 2006-08-10
I have found out exactly how to get Wifi working if it has one of those miseable Broadcom chips in it.    R E P L A C E    I T!

That's right. Replace the sucker. :D I just received 2 brand new Intel 8200GB miniPCI cards. I installed on my my wifes Dell Inspiron 8200. She runs Windows. Booted it up with the new card, installed a driver. And it worked.

Did the same with my Dell Inspiron 8600 under Windows. Worked prefectly. Both laptops reported a considerably better signal strength with the new cards.

Then took out the Winders drive and put the Ubuntu hard drive in the Inspiron 8600. Booted. Turned on the Wifi. And it worked. Didn't even have to install anything. Very cool. Adios Windows.

The only problem is that I don't have any way to see the signal strength. Something seems to be screwed up there but it is probably related to all the screwing around I had to do to try to get the evil Broadcom working.

Anyone want to buy a Broadcom card? Cheap.

Clark

PS...the cards cost something like $12 each on eBay with another $10 shipping.  What a deal!

---

### Post by csann on 2006-08-10
By the way, the card is operation at 54 mbps.  This just keeps getting better and better.

Now to complete the minor task of getting the card to show up in my notification area.

Life is good with Ubuntu and wifi....

Clark

---

### Post by bensexson on 2006-08-10
Unfortunately some laptop vendors (HP).  Add a BIOS blacklist and only allow you to use the miniPCI adapter provided with your laptop.  I considered this a while back and found out my laptop has this "feature".  I am using my bcm4306 with ndiswrapper just fine though.

---

### Post by csann on 2006-08-10
Just how evil does a company have to be to prevent you from installing what you want.  That is reason enough for me to never buy an HP.  

I think I've read somewhere that there are mods out there to overcome the blacklist though.  

Glad to hear your working ok with ndis though!

---

