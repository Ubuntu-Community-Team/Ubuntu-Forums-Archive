---
title: "poll_schedule_timeout stuck in System Monitor"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Books on 2010-11-23
I turned on the computer and the CPU fan rev'ed up and it was sluggish. I looked at System Monitor and it says "poll_schedule_timeout" in every process except for gvfs-fuse-daemon which says says "futex_wait_queue_me".

I googled and found this:

[INDENT]# Bug #488849 in linux (Ubuntu): “memory eaten: poll_schedule_timeout” -- 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488849](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488849)

# [ubuntu] Upgrade kernel to 2.6.30-9, Waiting channel=poll_schedule_timeout -- 
[http://ubuntuforums.org/showthread.php?t=1191910&page=3](http://ubuntuforums.org/showthread.php?t=1191910&page=3)

# poll_schedule_timeout on System Monitor -- 
[http://www.uluga.ubuntuforums.org/showthread.php?p=8172896](http://www.uluga.ubuntuforums.org/showthread.php?p=8172896)

# Many more for 'poll_schedule_timeout'
[http://www.google.com/search?hl=en&q=poll_schedule_timeout](http://www.google.com/search?hl=en&q=poll_schedule_timeout)[/INDENT]

Everyone is describing the same thing, all processed stuck on "poll_schedule_timeout" and the CPU going hard. But they say that it is stopped by a hard shutdown -- turn on the computer and it's supposed to be fine.

But my computer *stays that way*. It's like that on boot-up. I've rebooted three times. I refreshed Synaptic for new packages and kernal 2.6.35-23 was waiting, but after installing and rebooting the problem is still there.

How do I get my system freed up?

Thanks!

---

### Post by Books on 2010-11-23
**POSSIBLE SOLUTION TO Bug #488849 in linux (Ubuntu): “memory eaten: poll_schedule_timeout”**
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488849](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488849)

I may have found the problem. The **gnome-system-monitor** may be the trigger which starts the 'poll_schedule_timeout' status, and the only way to stop it is a hard shutdown (turning completely off, not just a re-start).

When I said earlier that the problem continued after I turned the computer off and back on, I noticed that the first thing I did was to turn on System Monitor to check the status. That may have been the trigger, so I thought it was the computer doing it.

I installed ksysguard and tried it -- the behavior is normal. Only when you run gnome-system-monitor do most of the open processes get stuck on 'poll_schedule_timeout'.

If you are having trouble with Bug #488849 stop using **gnome-system-monitor** and use instead **ksysguard** or another monitor until the issue is resolved.


ADDITIONAL THREADS:

poll_schedule_timeout, futex_wait_queue_me...what do these mean?
[http://ubuntuforums.org/showthread.php?t=1290763](http://ubuntuforums.org/showthread.php?t=1290763)

poll_schedule_timeout on System Monitor
[http://ubuntuforums.org/showthread.php?t=1284673](http://ubuntuforums.org/showthread.php?t=1284673)

---

