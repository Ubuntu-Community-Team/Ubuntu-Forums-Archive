---
title: "What gets lost in a clean install?"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by ScottyD135 on 2010-12-14
Hi everyone!

Just a quick question with regard to clean install of the OS on a separate '/' partition...

If I perform a clean install of an upgrade and I decide that I want to change to a different version (i.e. 10.04), will I lose my settings like with my printer/scanner or nvidia graphics, etc?

I spent a number of hours (admittedly noobish) in getting my Brother printer/scanner set up for local and network usage.  I also spent a good deal of time in getting my graphics and visual settings "just so".

So, if I have a separate partition for '/' and for '/home' what exactly do I lose when I perform a clean install?

Thanks for your time!
S

---

### Post by Quackers on 2010-12-14
If you do a clean install you lose verything from the system you are currently running.
If you have a separate /home partition now, you can mount that as /home for the new installation and just install the new OS to / (root) partition

---

### Post by littlepeon on 2010-12-15
to help clarify the last answer--
all of the settings for the operating system will be reset in a clean install....

however if u had a separate home partition, your individual program settings would still be kept.

---

### Post by synapsys on 2010-12-15
You'll loose all installed programs (on root partition) and all OS settings. There are a lot of settings and config files stored in your home folder, mostly related to program settings. You won't lose those. You will definitely have to reconfigure your printer and graphics settings. You should do some googling, maybe your printer is better supported in later versions like 10.04 and 10.10. Just think, the more times you do it, the less "noobish" you will become...:D

---

### Post by Verbeck on 2010-12-15
its not exactly necessary to reinstall to make a separate /home

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by ScottyD135 on 2010-12-15
> **synapsys said:**
> You'll loose all installed programs (on root partition) and all OS settings. There are a lot of settings and config files stored in your home folder, mostly related to program settings. You won't lose those. You will definitely have to reconfigure your printer and graphics settings. You should do some googling, maybe your printer is better supported in later versions like 10.04 and 10.10. Just think, the more times you do it, the less "noobish" you will become...:D

Ha ha!  It's definitely my goal to be as much or more comfortable in linux as I am in Windows.

I'm currently using 10.04.  My printer and scanner work well, thanks to Brother's support and drivers, but when I upgraded from 9.04 to 9.10 and finally 10.04, my networked printer was giving me problems (sometimes it still is...).  What I wondered was if I did a clean install of 10.10 to see if any CUPS wrinkles had been smoothed out, whether I would have to reconfigure everything.  I think that's definitely been answered here.

Thanks to all for your time and advice!
S

---

