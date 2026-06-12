---
title: "Firefox 3.0.6 freezing entire system"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by 5l4y3r on 2009-02-12
I'm having this problem when using Firefox 3 in Ubuntu 8.10 (both updated).
It happens randomly in many pages, some of them don't even have flash videos. It freezes the entire system and I have to force a reboot.
If anyone have a clue on how to solve this problem please share.
Thanks.

---

### Post by Michael.Godawski on 2009-02-12
hi,

are you sure it happens only when using Firefox?
Have you tried to run it via the terminal and check the System Logs for errors?

---

### Post by 5l4y3r on 2009-02-12
Yes. It only happens when using Firefox.
Can you please tell me the steps to check the System Logs for errors?

---

### Post by kostkon on 2009-02-12
> **5l4y3r said:**
> Yes. It only happens when using Firefox.
Can you please tell me the steps to check the System Logs for errors?
*System &#8594; Administration &#8594; System Log*

To add more logs, select *File &#8594; Open* and then go into the
```
/var/log
```
folder where the system logs exist.

---

### Post by 5l4y3r on 2009-02-12
Alright. I'll wait and see if the problem happens again then I'll post the log here.
Thanks a lot.

---

### Post by 5l4y3r on 2009-02-20
Hi. I've been trying to find anything suspicious or wrong in the logs when the freezing occur but nothing so far. For example, if the freezing occur at 3:30, the last log registered is from 3:20 and there's nothing wrong with this last log.
So I started investigating anything wrong with the flash player I had installed since the installation of 8.10. I opened Aplications > Add/Remove and typed 'flash' then a package called "Macromedia Flash Plugin" appeared and was unmarked. I've found that really strange because I had flash installed long time ago and sites like YouTube were working OK.
Then I installed this plugin too and went testing it for 2 days now. So far the freezings are gone. Pages with the minimum flash that before were freezing the entire system now aren't.
Let's wait a little longer and see if it really works. Thanks for the help and tips.

---

