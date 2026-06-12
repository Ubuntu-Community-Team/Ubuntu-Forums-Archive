---
title: "Ubuntu 10.04"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by b3ard on 2010-05-26
hello to all, 
 
I got a aspire one (acer) and I just install 10.04. Right away I immediately noticed lag with just about everything ( desktop navigation, apps, internet browsing, etc). I have used this notebook with a few of the previous distros and have not had this problem. Does anyone else notice the lag with 10.04???? or have any insight????
 
My desktop effects are set to none, so I have no extra goodies runnin.

---

### Post by warfacegod on 2010-05-26
My first guess would be that you need to activate your video cards driver.

Go to: System> Admin.> Hardware Drivers> Activate the "recommended" driver.

You may need to do an update first.

---

### Post by KdotJ on 2010-05-26
I too have an acer aspire and ubuntun 10.04 runs perfectly. Is it ATI graphics? Because since 10.04 I no longer needed to use the closed drivers to get everything to work as it should. It all worked straight out of the box

---

### Post by 3rdalbum on 2010-05-26
> **warfacegod said:**
> My first guess would be that you need to activate your video cards driver.

Go to: System> Admin.> Hardware Drivers> Activate the "recommended" driver.

You may need to do an update first.

No, the Aspire One is a netbook and has Intel graphics.

Unexplained slowness is usually due to a background program using up a lot of CPU time (or less commonly, I/O time). You can use System Monitor to examine the total CPU load. If it's higher than a couple of percent and your computer is not really doing anything, then go to the Processes tab and click on the CPU column to sort the list by CPU use.

Find whatever program in the list that is causing the high CPU use, and kill it. Right-click it, and go to End Process.

---

### Post by b3ard on 2010-05-27
Hey thanks for the replies,, all of you. Unfortunately, I had to get some work done immediately and had no other choice except to do a fresh install of 9.10. However, I will upgrade back to 10.04 tonight (with faith) and will check out the CPU usage. I will post my results as soon as I upgrade.

---

### Post by Yanno on 2010-05-27
actually Lucid is much faster...it that a problem with the kernel it lags a lot?

---

