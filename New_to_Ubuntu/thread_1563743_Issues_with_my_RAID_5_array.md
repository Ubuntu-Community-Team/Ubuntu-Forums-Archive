---
title: "Issues with my RAID 5 array"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-08-29
So...

I thought it would be a good idea to install Ubuntu onto a RAID 5 array which had been build by taking a small partition from each of my 4 HDDs. I figured that I would be able to have my operating system secure AND fast, because that's what RAID 5 does, right? WRONG!!

When there are no file operations taking place on the other partitions on my machine, it runs very fast. However, when there is ANY file being moved/copied/pulled to network, the array becomes very slow. This makes complete sense because, in theory, the RAID 5 array should run 3-4x the speed of the slowest disk. If you happen to be doing other things with ANY of the disks in the array, your slowest disk becomes VERY slow, making the entire system crawl.

I think I might have to do a rebuild with RAID 0... or with no RAID on the operating system.

-Kurt

---

