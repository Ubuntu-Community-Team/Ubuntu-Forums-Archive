---
title: "lucid power usage"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-05-06
Hi all, I've been noticing some pretty heavy power usage from lucid linx netbook edition. Just as an example, running windows, the idle time of my samsing netbook is around 7 hours (not advertised, but my personal experience). I recently switched to ubuntu for all the reasons that most of us have, and am really liking it, I have just been suspicious of the power usage and tonight tested it by fully charging the netbook , closing the lid (with power settings set to blank screen when lid is closed) with no programs running and wireless turned off and found that the battery died sometime between 5 and 6 hours - it would have been more accurate but I got a bit caught up in the election.

I have downloaded  Samsung tools in addition to the power manager. I'm fairly certain there aren't any settings I can change to increase the time, and it's still a reasonable time to be without a power output, I was just wondering if any one else had noticed increase power consumption, or if they knew why the os is drawing more power?

Please no posts about comparing linux to windows, I was just wondering about ubuntu?

Cheers in advance!

---

### Post by mörgæs on 2010-05-07
You can try a minimal Ubuntu:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

Less applications simply means less battery drain.

---

### Post by 3rdalbum on 2010-05-07
First, check that there aren't any programs hogging the CPU.

Try installing the "Powertop" package and running it in the terminal:

```
sudo powertop
```

This will suggest a few things to change to increase battery life, and it also lets you know how many times per second your programs wake up the CPU; this latter feature can let you know what programs you should try and avoid or use sparingly.

---

### Post by jonnny_j22 on 2010-05-08
Cheers for this, still not able to replicate the windows battery life, but an hour and a half tends to be worth it not to go through the problems of windows, and I'm sure this will be handy anyway when I've got a long train journey!

---

