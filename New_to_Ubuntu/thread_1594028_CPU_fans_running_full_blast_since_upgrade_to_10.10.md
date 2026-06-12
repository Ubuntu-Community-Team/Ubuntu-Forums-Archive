---
title: "CPU fans running full blast since upgrade to 10.10"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by mattismyname on 2010-10-11
Ever since I upgraded to 10.10, my CPU fans are running full blast (and making a lot of noise).  Anybody else seen this or know how to fix it?

---

### Post by bailli on 2010-10-12
I have a experienced a more noisy fan after upgrade to Kubuntu 10.10, too.

And I also have the impression that sometimes Firefox (or the whole system?) is slowed down.

---

### Post by peace.gangsta on 2010-10-12
Fans won't run full blast for no reason at all. Just take a look at the System Monitor for cpu consumption. Look for some malfunctioning program which is consuming up your cpu overheating it, hence causing the fans to run in full blast.

---

### Post by bailli on 2010-10-12
My fan isn't running full speed - it's just a bit more active since 10.10.
I already looked for possible cpu intensive processes but couldn't come up with anything significant (kwin might use a bit more cpu - but that could be just my imagination trying to find a culprit ;) )

A reason could be a different fan control policy - I am running kubuntu on a Samsung R560 notebook.

BTW.: is it possible to get rid of akonadi ?

---

### Post by mattismyname on 2010-10-12
@peace.gangsta I watch top but nothing is taking a significant amount of CPU
 @bailli how do you change the fan control policy?

---

### Post by tobid on 2010-10-13
i have just upgrade from 10.04 to 10.10 and experienced the same problem. the fans of my notebook (dell studio xp 1555) are running constantly at full speed, temperatures are within normal range (40C to 48C) and cpu cores are most of the time idle. it seems like this has something to do with ubuntu 10.10. ... damn i shouldn't have upgraded!

[UPDATE] mea culpa: its the open source drivers for my ati graphic adapter. i changed to the closed source ones and now the notebook is as quite as before.

---

### Post by spillage2 on 2010-10-13
mines been running flat out with 10.04. so this evening i decided to poke around my case. 

removed the heatsink and gave it all a good clean slapped on some new compound and now i cant hear the thing running.

cant believe thats all it took after spending a good few hours looking for a fix on the net.

---

### Post by GoosFraaba on 2010-10-14
I also had success by installing the proprietary graphics driver for my ATI card. I was trying to get by without installing it, but it fixed the fan issue.

---

### Post by mattismyname on 2010-10-17
Yep...proprietary drivers fixed it for me also.

---

### Post by 2un@ on 2010-11-03
Thank-you Thank-you Thank-you
This was driving me insane with fan constantly cycling on for no apparent reason
System/administration/additional drivers had prop driver that stopped it
HP DV6 laptop with ATI 4650 GPU

---

