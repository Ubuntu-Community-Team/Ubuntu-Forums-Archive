---
title: "upgrade to 9.10, will my drivers be affected?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by fwin on 2009-10-21
Hi,

I heard that the new version of ubuntu is coming out, and I definitely want to install it but, will this uninstall/undo all the drivers/fixes that i have?. I don't want to start looking for new drivers/fixes for version 9.10, I had a really hard time finding a way to make work my wifi and specially my nvidia card with 9.04. 

thanks in advance for your help

---

### Post by kellemes on 2009-10-21
It will upgrade drivers installed on your system. So if all goes well you won't have any trouble..

Obviously you should realize upgrading your system always brings risks. So always backup stuff and assume trouble.

---

### Post by andymorton on 2009-10-21
Mine have been affected when I upgraded to the 9.10 beta but only in a positive way. When I was using 9.04 any wi-fi connection I used would cut out every ten minutes or so. This has never happened with Karmic.  

andy
:)

---

### Post by QIII on 2009-10-21
At best, you can get only anecdotal responses from everyone who has been down the path with their own particular hardware/driver combinations.

There is always risk, as stated above, and I will reiterate the recommendation to DO BACKUPS.

---

### Post by Mark Phelps on 2009-10-21
> **fwin said:**
> ... and especially my nvidia card with 9.04. 

Yeah, I know this is somewhat different, but lots of folks got burned updating to 9.04 from 8.10 because they had ATI drivers installed -- and those aren't supported in 9.04.

Don't know about the case with Nvidia drivers, but it might be worth your while to boot into a 9.10 LiveCD and see if you can then install restricted NVidia drivers OK.  If you can, you should have no problems during the upgrade.

---

### Post by agberg on 2009-10-21
When I upgraded on my HP laptop the sound would not work. I switched back to 8.10 and it works fine.

---

### Post by fwin on 2009-10-21
I guess I will try the 9.10 live cd first.

 Thank you all for your ideas.

---

### Post by waspbr on 2009-10-21
> **agberg said:**
> When I upgraded on my HP laptop the sound would not work. I switched back to 8.10 and it works fine.

I have the same issue with my ho laptop. it not exactly a driver problem, more like an alsa problem. 

this command may help

```
sudo alsactl restore
```

it mya restore your sound setting, note that I said may. In my case the command worked sporadically. Hope you have submitted a bug report tho, the more ppl submit the better

---

### Post by Sef on 2009-10-21
> I guess I will try the 9.10 live cd first.


That is the best thing to do if you are unsure about a new version of Ubuntu.

---

### Post by QIII on 2009-10-21
> **Mark Phelps said:**
> Yeah, I know this is somewhat different, but lots of folks got burned updating to 9.04 from 8.10 because they had ATI drivers installed -- and those aren't supported in 9.04.

Some of the ones that ATI had consigned to the trash heap of "legacy" were not supported by ATI any more.  2D was still supported with the open source driers.  I have a Jaunty machine happily running an ATI card with full 3D acceleration.

---

