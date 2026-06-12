---
title: "KPPP Sprint Problem Finally Solved"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-11-03
Hello,

After 6 months of trying everything you could imagine, and being a new Linux user with not a lot of computer experience, I finally stumbled on the answer on this forum thanks to samjh from Australia.

The problem was that kppp would go through all the steps but would not connect.

Here are some of the theads I started to try to fix it.

[http://ubuntuforums.org/showthread.php?t=1266426](http://ubuntuforums.org/showthread.php?t=1266426)

[http://ubuntuforums.org/showthread.php?t=1242659](http://ubuntuforums.org/showthread.php?t=1242659)

[http://www.dslreports.com/forum/remark,23079184?hilite=sprint](http://www.dslreports.com/forum/remark,23079184?hilite=sprint)

I even installed 8.04, and Mint on other partitions to try it and the same thing as 9.04, about a month ago I decided to wait for 9.10 and see what happens. I clean installed 9.10 on the 8.04 partition and formatted to ext4. 

When I installed kppp, it would not open from the menu and I had to use the terminal with sudo, I decided to try to fix that before I configured kppp, here is the thread I started for this problem.

[http://ubuntuforums.org/showthread.php?t=1311845](http://ubuntuforums.org/showthread.php?t=1311845)

After I did the fix suggested by samjh and configured it and tried it, it went right on line, I was surprised and booted up my 9.04, did the fix and it fixed it there.

Seems the problem was that kppp needs root privileges and that was not, for some reason happening when I installed it with Synaptic.

I hope this helps someone else.

BarnacleBill

---

