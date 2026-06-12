---
title: "no boot:&quot;one of the mounts listed in /etc/fstab cannot be mounted"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by pottzie on 2010-01-22
When I started Ubuntu 9.1, after a few minutes the mouse "froze," and wouldn't move when I gave it a swipe no matter what. So I rebooted (my only option, since I couldn't get the cursor to move.)
 When I rebooted, everything "went off a cliff." I get the Ubuntu screen, then it just goes black, like it's waiting for something to happen. No error report, just a black screen. When I tried recovery mode it said "One or more of the mounts listed in /etc/fstab cannot yet be mounted." Also "Swap:waiting for UUID=0c1f40b-052-4fa1-a16d-e379b5(here it went off the screen and looped back on the other side)575b80
 The recovery mode then kicked in some more and I got to a log-in prompt, so I logged in and got "/dev/sda3 on / type ext3 (rwerrors=remount ro)
 
Any suggestions?

---

### Post by pottzie on 2010-01-22
Solved it by going in with the live CD and "mucking around." Wish I could be clearer in my description, but just tried to reinstall Ubuntu, and when Gparted asked where the hell my boot sector is (and I have no idea how to declare one-there isn't any option that I can see. This is after I choose to install manualy, as I don't want to overwrite the Windows partition.), I just exited and rebooted. It took a few tries, the first gave me some goofy tag saying that my monitor needed to be reset to some goofy spec that was nowhere to be found on my monitor set-up menu. Seemed odd, since the monitor has been working fine for quite a while now. But after "hammering it" i.e. rebooting more than three times, it worked. 
 Maybe that friggin' download that I did a few weeks back that had something like, oh, 60 files and took twenty minutes wasn't such a good idea. Especially since the thing that I wanted didn't work when I finished; some of the dependancies were wrong-go figure.
 60 files. WTF was I thinking?

---

