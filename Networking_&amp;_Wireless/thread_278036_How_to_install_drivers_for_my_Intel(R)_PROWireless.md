---
title: "How to install drivers for my Intel(R) PRO/Wireless 3945ABG Network Connection"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by moodys on 2006-10-15
Have trouble with my wireless netwrok card(Intel(R) PRO/Wireless 3945ABG Network Connection) I have already downloaded the update drivers for Linux from Intel website but I have no idea how tom install the drivers can somebody walk me through this process please.
Thank you

---

### Post by pgilmon on 2006-11-06
I downloaded the drivers from intel and found a file named ipw3945d in those drivers, created a link from /sbin/ipw3945d-2.6.17-10-generic to that file and... voila, it works. 
Of course, you have to change the name ipw3945d-2.6.17-10-generic to match with your kernel.

---

### Post by pgilmon on 2006-11-06
[[Deleted by poster]]

---

### Post by SendDerek on 2006-11-06
Just out of curiosity, have you installed Network Manger?

I have the same wireless adapter and by just installing Network Manager I was able to get online.  The drivers and what-not should be already built into both Dapper and Edgy.

---

### Post by pgilmon on 2006-11-16
I think that the drivers were there as you say, but in order to install the drivers from nvidia I had to remove the restricted-modules. I guess that's the reason why it didn't work.

---

