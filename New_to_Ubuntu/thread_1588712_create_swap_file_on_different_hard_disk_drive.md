---
title: "create swap file on different hard disk drive"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by knowlittle on 2010-10-05
Hi, my computer has 2 hard disk drives and I like to move the swap file to the drive that is being use less. Could someone tell me how to do this? I can not figure out how Ubuntu address a partition. For example, I remember in the old DOS day, it's cd D: to address drive D.

---

### Post by Elfy on 2010-10-05
Linux does not use c or d or e ... etc

Link to swap wiki page - [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Specifically, this might help - [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Some other links 

[https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html](https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by HermanAB on 2010-10-05
Howdy,

All you need to do is read the swapon man page.  It has a good explanation:
$ man swapon

---

### Post by knowlittle on 2010-10-09
Thank you for the replies. I managed to achieve this. 

Under Ubuntu 10.4.1, I use Places - Home Folder, I mounted the drive and rename it HD2 from New Volume, which is impossible to be referred to in Terminal. 

I found my other hard disk under /media. 

After that all I did was following:  [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?) . Note: I had to replace /mnt/ by /media/HD2.

All worked. It marginally more responsive. This tells me, I may need to buy new computer!!!

---

