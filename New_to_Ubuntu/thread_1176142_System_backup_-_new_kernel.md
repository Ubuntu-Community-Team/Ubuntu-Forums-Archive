---
title: "System backup - new kernel"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by furialis on 2009-06-02
I bought a new SSD HD and the necessary drivers are not included in the 2.6.28-11 kernel, so I followed [this]("http://ubuntuforums.org/showthread.php?t=311158") guide and now I can see the new HD with Gparted. How can I make a liveCD with my new kernel? I tried remastersys, but it doesn't seem to work. I also tried to do
```
sudo dd if=/dev/sda of=/dev/sdb
```
This filled my new drive even though my root partition is 4 gigs - weird. 
Anyway, any advice is appreciated.

---

