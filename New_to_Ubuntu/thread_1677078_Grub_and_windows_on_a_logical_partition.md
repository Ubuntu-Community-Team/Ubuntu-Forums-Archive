---
title: "Grub and windows on a logical partition"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Falc7 on 2011-01-28
Here is the situation, the laptop came with windows. I created a new extended partition (sda4) and installed ubuntu in a logical partition (sda7) within that, and then I installed another copy of windows on another logical partition again within the extended partition (sda8). 

I then reinstalled grub so I could boot into ubuntu again, however grub doesn't have an option to boot into the new copy of windows on sda8, I have tried updating grub, but it didn't work.

---

### Post by HermanAB on 2011-01-28
AFAIK Windows can only boot off a primary partition.

---

### Post by mharrison on 2011-01-28
Although I think you might be a little late for this.

This article might help you if you would be willing to "start over"

[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)

---

### Post by Falc7 on 2011-01-28
i see, thanks

---

