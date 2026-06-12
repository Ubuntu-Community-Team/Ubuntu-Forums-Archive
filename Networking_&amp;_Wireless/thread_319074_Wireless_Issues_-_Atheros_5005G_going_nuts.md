---
title: "Wireless Issues - Atheros 5005G going nuts?"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by mattalves on 2006-12-15
Heypa all,

Seems like my Atheros 5005G wireless adapter (on a Acer Aspire 3502) went nuts (or maybe it was my Dapper?). All of a sudden it decided not to work anymore, and it wasnt even recognized by Ubuntu - from dmesg I could see that there was some issue with HAL and the hardware revision and madwifi and so on. 

As some others mentioned in the forum, switching back to Windows could make it work once again - luckly, I had enough space to install the XP that came with the notebook, and found the adapter working flawlessly. And whenever I booted Dapper again, there was my ath0 in its correct place, also working flawlessly.

What can be done to prevent it happening again? Is there some link between windows making it work and then dapper recognizing it again? I'd really appreciate any insight on the matter.

Cheers!

---

### Post by maestrobwh1 on 2007-09-13
I can't help you but can tell you I have a similar issue with my atheros card, as when I booted into XP (fortunately I had a dual boot system to begin with), it seemed stable for a bit, although after a few boots in ubuntu, it started being flakey again.  I have no answers yet!
[http://ubuntuforums.org/showthread.php?p=3358001#post3358001]("http://ubuntuforums.org/showthread.php?p=3358001#post3358001")

---

### Post by maestrobwh1 on 2007-09-13
I just tried this today and it really seemed to help my issue.  It took maybe 15 minutes.

[http://ubuntuforums.org/showthread.php?t=485579&highlight=how+to+madwifi+source]("http://ubuntuforums.org/showthread.php?t=485579&highlight=how+to+madwifi+source")

---

