---
title: "Clock changes in Windows XP?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by geobones on 2009-03-07
Hi, 
My first post. I have Ubuntu 8.04LTS installed on my secondary hard drive and Windows XP on my primary drive. I switch between drives and operating systems via the BIOS. After I have finished using Ubuntu on the secondary drive and gone back to XP on the primary drive, the time on the task bar in XP has change by some eight hours. Can anyone explain why? I always have to readjust the time back to normal in XP.

George...

---

### Post by Toxicity999 on 2009-03-07
this is a matter of difference between windows and the way ubuntu handles things. Ubuntu reads the system clock as is, and offsets it by software, where windows can do either in it's own... interesting ways.

The easiest fix for this is to check the time options in windows to keep it synchronized with a time server, and make sure you set it to the proper time zone.

---

### Post by mobilediesel on 2009-03-07
Ubuntu defaults to setting the BIOS time to UTC (Coordinated Universal Time) and displays in your local timezone. Windows just displays what the BIOS tells it. Try [http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_217.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_217.html)
It tells you how to make it not use UTC so it'll stop confusing Windows.

---

### Post by Wabbitoid on 2009-03-07
I have the exact same problem -- except I'm using Vista as my second OS.  

Each time I boot Ubuntu (8.10), I'm guaranteed that the next time I boot Vista, the Windows clock will be  off again.  If I fix it and continue to reboot into Vista, the clock will stay sane.  

However, as soon as I've booted Intrepid, any subsequent boots into Vista will have the clock issue.

It's driving me nuts!  Any ideas?

---

### Post by Toxicity999 on 2009-03-07
The answers above should solve your problem as well.

---

### Post by taurus on 2009-03-07
> **Wabbitoid said:**
> I have the exact same problem -- except I'm using Vista as my second OS.  

Each time I boot Ubuntu (8.10), I'm guaranteed that the next time I boot Vista, the Windows clock will be  off again.  If I fix it and continue to reboot into Vista, the clock will stay sane.  

However, as soon as I've booted Intrepid, any subsequent boots into Vista will have the clock issue.

It's driving me nuts!  Any ideas?

Look in System -> Administration -> Time and Date and check your **Time zone:**.

---

