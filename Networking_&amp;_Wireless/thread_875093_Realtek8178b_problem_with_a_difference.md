---
title: "Realtek8178b problem with a difference"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by wessie on 2008-07-30
Hi all,

I've spent at least 40-50 man hours trying to sort out my wireless woes with hardy with no luck.

I have a toshiba l300 with an onboard realtek chip. When i received the laptop it was pre-installed with vista. Just to make sure everything worked i used it for 2 days and everything incl. the wireless worked fine.

Now i've installed ubuntu and all the upgrades available and still can't connect to my wireless router.

Now the difference I've noticed between my problem and the common problem on this site is that others have a PID of 8197 or 8189 when they do a lsusb. However this is my output when i do a lsusb

```
wes@wes-laptop:~$ lsusb
Bus 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 04fc:00d3 Sunplus Technology Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
``` 

I've tried installing ndiswrapper along with the modified driver (the 2.6.24 patch), i've tried updating the win98 driver as suggested multiple times on this site......still i have no luck. 

So now i'm asking the resident linux geniuses to please help a very green linux user to sort this mess out. I'm ready to run any command and provide any info. Please help.

---

