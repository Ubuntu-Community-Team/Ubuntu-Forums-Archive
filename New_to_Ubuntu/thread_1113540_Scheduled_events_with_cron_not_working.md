---
title: "Scheduled events with cron not working"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by S.lewis on 2009-04-01
We've got an eeebox in the office that is used for showing a slideshow with company pictures during the day. I'm trying to find a way to get the monitor to go into standby at 5PM Monday to Friday and come out of standby at 8AM Monday to Friday.

So far, I've found that the command 'xset -display :0 dpms force off' turns it off and force on turns it on which is fine but when I try to schedule the events in cron they don't appear to execute. 

Here's my crontab file, would anyone be kind enough to let me know where I'm going wrong?

```
# m h  dom mon dow   command
00 8 * * 1 xset -display :0 dpms force on
00 8 * * 2 xset -display :0 dpms force on
00 8 * * 3 xset -display :0 dpms force on
00 8 * * 4 xset -display :0 dpms force on
00 8 * * 5 xset -display :0 dpms force on
00 17 * * 1 xset -display :0 dpms force off
00 17 * * 2 xset -display :0 dpms force off
00 17 * * 3 xset -display :0 dpms force off
00 17 * * 4 xset -display :0 dpms force off
00 17 * * 5 xset -display :0 dpms force off
```

I've even tried adding in lines such as

```
13 * * * * root echo "test"
```

But they don't seem to work either, so I really have no idea. I previously got the scheduling to work when I was playing around with it but haven't had any success since. If I'm doing something stupid, please let me know!

Thanks

---

### Post by keplerspeed on 2009-04-01
I just tried it, works for me!!

# m h  dom mon dow   command
36 9 * * * xset -display :0 dpms force off

Other than that.... it looks good. Do a test, change the minute and hr to the current time (or a minute advance) wait a min and see what happens. If nothing happens, only thing will be the day of week. 1 through 5. Im not sure but is 1 monday, or sunday???

---

### Post by S.lewis on 2009-04-01
Apparently 0 is Sunday. I've tried testing a few times but no dice so far.. will keep playing I guess.

---

### Post by S.lewis on 2009-04-01
Still no dice, anyone have any ideas? :(

---

### Post by Cheesehead on 2009-04-01
One, make sure cron is working with a test:

User crontab entry. Each minute, it will create or touch the testfile.testfile on your desktop.```
* * * * * /usr/bin/touch /home/USERNAME/Desktop/testfile.testfile
```

Two, instead of the command 'xset', try the whole path '/usr/bin/xset'. Cron is not clever about paths.

Three, consider moving the commands to a separate shell script that gets activated by cron. That way, you can add logging or notification to help debug the problems.

Will the user be eternally logged in? If logged out, the user's cron jobs shouldn't run. Also, since root doesn't start the gdm session, xset may not know where 'display :0' is. I've had problems with that in the past.

(The more complicated DBus method 'setDpmsMode' -or something similar- can also be controlled by cron to achieve the same effect since it's independent of the user session)

---

### Post by llamabr on 2009-04-01
> **Cheesehead said:**
> If logged out, the user's cron jobs shouldn't run. 

I don't think that's true.  crond should run all cron files, even if I'm not logged in.

Instead of having a million lines in your cron file like that, try writing it into a script that cron calls. 

Just a thought.

---

### Post by S.lewis on 2009-04-02
Did a few tests and the /usr/bin/xset bit seems to have made the difference. Thanks!

---

### Post by hyper_ch on 2009-04-02
well, two things:

cron has not the same path info as the normal user also there's a different shell be executed. That's why it's recommended to write a full shell script where you also specify the shell.

e.g.

```

#!/bin/bash
/usr/bin/xset -display :0 dpms force on

```
and chmod it so that it's executable.


second, just make two cron entries like:
```

0 8 * * 1,2,3,4,5 /path/to/xseton.sh
0 17 * * 1,2,3,4,5 /path/to/xsetoff.sh

```

---

### Post by S.lewis on 2009-04-02
Thanks for the advice hyper_ch but I have it working now and don't want to ruin a good thing. Will take your comments on board if I decide to do something similar in the future though.

I appreciate everyone's help, thanks.

---

