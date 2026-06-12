---
title: "Understanding &quot;top&quot;"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by RussW210 on 2009-01-19
Hello everyone,

I am trying to understand why my k9copy hogs up my computer's memory.  I have 3gb of RAM in my computer.

I typed in the terminal "top" and am reading the window.  There is a line which reads:

Mem: XXXXXXXXXX total, XXXXXXXX used, XXXXXXXXXX free, XXXXXXXXX buffers

When I start k9copy it climbs rapidly so practically all (except for a few thousand kb's) the memory is being used.  When k9copy is finished though, that amount used does not drop, it stays at almost full even though I have closed out of k9copy and have nothing running on my computer.

Can someone help me out here... is all my Memory being used up?  When k9copy is running it says about 1.4% under the %MEM column.  Don't understand why that used number spikes so high and stays there...

Thanks for any help I can get.

---

### Post by mcduck on 2009-01-19
Linux uses all RAM not used by programs for caching recently accessed data. This improves your system's performance quite a lot (reading data from RAM is roughly 1000 times faster than reading it from hard disk), and besides, RAM not used means you've wasted your money when you paid for it. ;)

As soon as some program need more RAM some cached data is dropped, so the RAM used for caching still available for programs if they need it.

The easiest way to check the actual RAM usage is to run "free -m" and then read from the "+/- buffers/cache"-line.

edit: In this case k9copy uses 1,4% of your RAM. All data that it reads is temporary stored in the available RAM so it can be accessed quicker if the system needs the same data again.

After your computer has been running for a while the RAM usage (including cache) should be close to 100%.

---

### Post by RussW210 on 2009-01-19
Very well put mcduck.  I fully understand now.  Learn something new every day :O)  THANKS!!!!

---

