---
title: "Disk Utility (how to stop an operation)"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by manders2600 on 2011-05-18
Hey, thanks in advance for anyone willing to help me out with this.

I recently set up a 12TB RAID 6 array with 10 2TB drives, via Disk Utility.  They just finished synchronizing (took a little less than a day) and I accidentally clicked the Check and Repair button.  Before I realized what I was doing (I had meant to format it) it began to "repair" the array.  This, by all appearances, seems like it will take nearly as long as it did to originally synchronize the array, but I cannot figure out a way to make it stop.  When I click "Stop Array" it tells me that an operation is already running.

I would like to dispense with the repairing of the array, as I have already tested the disks individually, as well as having waited for them to synchronize.  Worst case scenario is that I have to wait another day to use them, but I am wondering if there is a way to manually stop the "repair" without messing anything up in the array?

Thanks,

Mark

---

### Post by Mr Stoozer on 2011-05-19
Did you let it run or get it stopped? 
It's a little late for advice now, but for what it's worth, i would've let it finish its operation.

---

### Post by manders2600 on 2011-05-19
Yeah, I let it do its thing.  I have actually decided to try rebuilding this over about a week with different stripe sizes, taking benchmarks each time, to see what is optimal.  I am thinking 128k for a RAID-6 with 8 2TB drives, but I would like to see if there are better options.

---

