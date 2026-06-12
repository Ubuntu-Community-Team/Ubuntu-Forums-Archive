---
title: "Hibernate not working"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Telos3K on 2011-01-13
Hi,

I recently migrated from wubi to a dual-boot partition with 10.04, on an Asus UL-30a.  Everything went well, but one remaining issue is that I can't get hibernation to work. (Ironically, it worked in wubi, although I did not expect it to.) I set up a swap partition using GParted, and set the UUID in fstab and resume--or so I think I did. I also eventually want to optimize my partitioning, but I've started [another thread]("http://ubuntuforums.org/showthread.php?t=1652522") for that. That thread describes my current partitioning in detail, in case that is helpful for this hibernation problem. 

My syslog output is below.  I'm fairly inexperienced so whatever it is I need to do, please walk me through it.  

Many thanks!

```

0000000e1000 - 0000000000100000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 11 16:09:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 11 16:09:22 ubuntu kernel: [    0.614852] PM: Resume from disk failed.
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 11 17:33:45 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 11 17:33:45 ubuntu kernel: [    0.600620] PM: Resume from disk failed.
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 11 18:55:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 11 18:55:05 ubuntu kernel: [    0.607578] PM: Resume from disk failed.
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 11 20:01:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 11 20:01:38 ubuntu kernel: [    0.593131] PM: Resume from disk failed.
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 11:52:22 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 11:52:22 ubuntu kernel: [    0.614324] PM: Resume from disk failed.
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 11:54:05 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 11:54:05 ubuntu kernel: [    0.602730] PM: Resume from disk failed.
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 12:42:35 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 12:42:35 ubuntu kernel: [    0.592313] PM: Resume from disk failed.
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 14:28:30 ubuntu kernel: [    0.604882] PM: Resume from disk failed.
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 15:35:55 ubuntu kernel: [    0.603132] PM: Resume from disk failed.
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 16:18:53 ubuntu kernel: [    0.599611] PM: Resume from disk failed.
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 16:25:52 ubuntu kernel: [    0.594462] PM: Resume from disk failed.
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 17:27:21 ubuntu kernel: [    0.593608] PM: Resume from disk failed.
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 17:38:32 ubuntu kernel: [    0.588371] PM: Resume from disk failed.
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 19:05:01 ubuntu kernel: [    0.615282] PM: Resume from disk failed.
Jan 12 23:58:33 ubuntu kernel: [17657.218411] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
Jan 12 23:58:33 ubuntu kernel: [17657.218419] PM: Marking nosave pages: 00000000bdda0000 - 0000000100000000
Jan 12 23:58:33 ubuntu kernel: [17657.220096] PM: Basic memory bitmaps created
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 00:02:02 ubuntu kernel: [    0.601198] PM: Resume from disk failed.
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 00:07:50 ubuntu kernel: [    0.605219] PM: Resume from disk failed.
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 00:11:38 ubuntu kernel: [    0.600836] PM: Resume from disk failed.
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 12:50:01 ubuntu kernel: [    0.600242] PM: Resume from disk failed.
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 13:52:33 ubuntu kernel: [    0.600611] PM: Resume from disk failed.
bwbloch@ubuntu:~$
```

---

### Post by bcbc on 2011-01-13
Let's go with some basic command output:
```
sudo blkid
free
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

I know you did some of this already in the migration thread, but let's get it in one place. According to [this]("https://wiki.ubuntu.com/AsusUL/AsusUL30A") hibernate should work.

It's not possible to hibernate a wubi install unless you use a swap partition. Are you sure it was working or are you talking about Suspend, not hibernation?

---

### Post by Telos3K on 2011-01-13
Well, I was clicking on "hibernate" not suspend, so I assume that's what it was doing.  And I remember reading that you can't hibernate in wubi, so I was a bit confused, but I didn't pursue it because I was more concerned with things that were supposed to work but weren't, than things that weren't supposed to work but were.....

Here's the output from the above commands:

```
bwbloch@ubuntu:~$ sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="BCB68218B681D376" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="B19401CA6A583703" TYPE="ntfs" 
/dev/sda6: LABEL="Ubuntu OS" UUID="b610e25d-4073-487b-abc3-db17a16dea91" TYPE="ext2" 
/dev/sda7: LABEL="Swap" UUID="24622487-0dd5-4c54-bd7f-724c9bf66979" TYPE="swap" 
bwbloch@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       4025304    1913196    2112108          0     182428     950524
-/+ buffers/cache:     780244    3245060
Swap:      8156640          0    8156640
bwbloch@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#/dev/sda2	/host	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
/dev/sda5	/media/DATA	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf800
#/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
#/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0


UUID=b610e25d-4073-487b-abc3-db17a16dea91    /    ext4    errors=remount-ro    0    1
UUID=24622487-0dd5-4c54-bd7f-724c9bf66979    none    swap    sw    0    0
bwbloch@ubuntu:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=24622487-0dd5-4c54-bd7f-724c9bf66979
bwbloch@ubuntu:~$ 
```

---

### Post by bcbc on 2011-01-13
You have some issue with /dev/ramzswap0 - it shouldn't be there. See [http://ubuntuforums.org/showthread.php?p=7268741](http://ubuntuforums.org/showthread.php?p=7268741) for how to remove.

Or to paraphrase (taken from [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/328437/)):
> To check if one has Compcache enabled run:
sudo swapon -s

If there is a ramzswap in there along with your normal swap settings it means it is enabled. To disable it:

sudo rm /usr/share/initramfs-tools/conf.d/compcache && sudo update-initramfs -u

And restart. Check to see if it is installed by running this again after rebooting:
sudo swapon -s

It should be gone now.

There is some further speculation that installing casper causes this e.g. if you used remastersys at some point. So... read further on that in the bug report. At least, if it crops up again.
Hopefully removing this will fix your problem.

---

### Post by Telos3K on 2011-01-13
I followed the above and now get:
```
bwbloch@ubuntu:~$ sudo swapon -s
[sudo] password for bwbloch: 
Filename				Type		Size	Used	Priority
/dev/sda7                               partition	6143992	0	-1
bwbloch@ubuntu:~$
```

However, when I go to hibernate, same problem, the computer freezes and shuts down.  This time, when restarting, I got a message at the login screen:  "Resuming from [disk UUID]" and it restarted in a very creaky fashion.

I did in fact use remastersys a while back (were you able to read that from my output or what that just a really good guess?)  Do I need to uninstall something?

Thanks!

---

### Post by bcbc on 2011-01-13
It's not so much that I guess, that I assume that there'll be something unknown/unexpected thrown in the mix ;)
Otherwise you wouldn't be having any problems. And remastersys was mentioned in that bug report.

Ok, so try to remove casper (just in case this is installed)
```
sudo apt-get remove --purge casper
sudo update-initramfs -u
```

Repeat the check on the ramzswap and remove if necessary. Reboot.

Then try to hibernate and if there is a problem, respond with 
```
sudo swapon -s
free
grep 'PM:' /var/log/syslog
```

---

### Post by Telos3K on 2011-01-13
Did the above.  Now when I try to hibernate, the screen freezes and eventually the machine shuts down.  When I reboot it, I get that "resume from dev/[UUID]" message, and a lot of ugly hard drive crunching noise, the screen goes black and then comes back to life -- to where I left off when I hibernated.

Here's the diagnostics:
```
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 14:28:30 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 14:28:30 ubuntu kernel: [    0.604882] PM: Resume from disk failed.
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 15:35:55 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 15:35:55 ubuntu kernel: [    0.603132] PM: Resume from disk failed.
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 16:18:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 16:18:53 ubuntu kernel: [    0.599611] PM: Resume from disk failed.
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 16:25:52 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 16:25:52 ubuntu kernel: [    0.594462] PM: Resume from disk failed.
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 17:27:21 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 17:27:21 ubuntu kernel: [    0.593608] PM: Resume from disk failed.
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 17:38:32 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 17:38:32 ubuntu kernel: [    0.588371] PM: Resume from disk failed.
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 12 19:05:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 12 19:05:01 ubuntu kernel: [    0.615282] PM: Resume from disk failed.
Jan 12 23:58:33 ubuntu kernel: [17657.218411] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
Jan 12 23:58:33 ubuntu kernel: [17657.218419] PM: Marking nosave pages: 00000000bdda0000 - 0000000100000000
Jan 12 23:58:33 ubuntu kernel: [17657.220096] PM: Basic memory bitmaps created
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 00:02:02 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 00:02:02 ubuntu kernel: [    0.601198] PM: Resume from disk failed.
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 00:07:50 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 00:07:50 ubuntu kernel: [    0.605219] PM: Resume from disk failed.
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 00:11:38 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 00:11:38 ubuntu kernel: [    0.600836] PM: Resume from disk failed.
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 12:50:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 12:50:01 ubuntu kernel: [    0.600242] PM: Resume from disk failed.
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 13:52:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 13:52:33 ubuntu kernel: [    0.600611] PM: Resume from disk failed.
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 15:12:27 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 15:12:27 ubuntu kernel: [    0.594764] PM: Resume from disk failed.
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 16:17:53 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 16:17:53 ubuntu kernel: [    0.596384] PM: Resume from disk failed.
Jan 13 16:18:55 ubuntu kernel: [  103.082309] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
Jan 13 16:18:55 ubuntu kernel: [  103.082318] PM: Marking nosave pages: 00000000bdda0000 - 0000000100000000
Jan 13 16:18:55 ubuntu kernel: [  103.083989] PM: Basic memory bitmaps created
Jan 13 16:20:11 ubuntu kernel: [  103.083991] PM: Syncing filesystems ... done.
Jan 13 16:20:15 ubuntu kernel: [  103.096162] PM: Preallocating image memory... done (allocated 903730 pages)
Jan 13 16:20:15 ubuntu kernel: [  108.149964] PM: Allocated 3614920 kbytes in 5.05 seconds (715.82 MB/s)
Jan 13 16:20:15 ubuntu kernel: [  108.272562] PM: freeze of drv:ieee80211 dev:phy0 complete after 121.932 msecs
Jan 13 16:20:15 ubuntu kernel: [  108.690432] PM: freeze of drv:sd dev:0:0:0:0 complete after 417.648 msecs
Jan 13 16:20:15 ubuntu kernel: [  108.990089] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 239.700 msecs
Jan 13 16:20:15 ubuntu kernel: [  109.004373] PM: freeze of devices complete after 853.812 msecs
Jan 13 16:20:15 ubuntu kernel: [  109.005423] PM: late freeze of devices complete after 1.045 msecs
Jan 13 16:20:15 ubuntu kernel: [  109.264768] PM: Saving platform NVS memory
Jan 13 16:20:16 ubuntu kernel: [  109.460386] PM: Creating hibernation image: 
Jan 13 16:20:16 ubuntu kernel: [  109.470008] PM: Need to copy 110893 pages
Jan 13 16:20:16 ubuntu kernel: [  109.470008] PM: Normal pages needed: 110893 + 1024, available pages: 928686
Jan 13 16:20:16 ubuntu kernel: [  109.470008] PM: Restoring platform NVS memory
Jan 13 16:20:16 ubuntu kernel: [  110.263683] PM: early restore of devices complete after 1.821 msecs
Jan 13 16:20:16 ubuntu kernel: [  111.119304] PM: restore of drv:i915 dev:0000:00:02.0 complete after 701.147 msecs
Jan 13 16:20:17 ubuntu kernel: [  111.472576] PM: restore of drv:usb dev:usb1 complete after 259.386 msecs
Jan 13 16:20:17 ubuntu kernel: [  111.732623] PM: restore of drv:usb dev:usb2 complete after 260.028 msecs
Jan 13 16:20:17 ubuntu kernel: [  112.083387] PM: restore of drv:usb dev:1-3 complete after 346.875 msecs
Jan 13 16:20:17 ubuntu kernel: [  112.362187] PM: restore of drv:usb dev:2-1 complete after 278.782 msecs
Jan 13 16:20:17 ubuntu kernel: [  112.418680] PM: restore of devices complete after 2091.959 msecs
Jan 13 16:20:17 ubuntu kernel: [  112.419933] PM: Image restored successfully.
Jan 13 16:20:17 ubuntu kernel: [  112.421026] PM: Basic memory bitmaps freed
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 20:22:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 20:22:56 ubuntu kernel: [    0.608562] PM: Resume from disk failed.
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdda0000 - 00000000bddaf000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bddaf000 - 00000000bdde0000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bdde0000 - 00000000bde00000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000bde00000 - 00000000fed20000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed40000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fee00000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 13 20:48:56 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 13 20:48:56 ubuntu kernel: [    0.604125] PM: Resume from disk failed.
Jan 13 20:50:23 ubuntu kernel: [   99.362028] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
Jan 13 20:50:23 ubuntu kernel: [   99.362036] PM: Marking nosave pages: 00000000bdda0000 - 0000000100000000
Jan 13 20:50:23 ubuntu kernel: [   99.363715] PM: Basic memory bitmaps created
Jan 13 20:51:40 ubuntu kernel: [   99.363717] PM: Syncing filesystems ... done.
Jan 13 20:51:46 ubuntu kernel: [   99.371695] PM: Preallocating image memory... done (allocated 903730 pages)
Jan 13 20:51:46 ubuntu kernel: [  108.281053] PM: Allocated 3614920 kbytes in 8.90 seconds (406.17 MB/s)
Jan 13 20:51:46 ubuntu kernel: [  108.640974] PM: freeze of drv:sd dev:0:0:0:0 complete after 288.199 msecs
Jan 13 20:51:48 ubuntu kernel: [  108.942598] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 239.664 msecs
Jan 13 20:51:48 ubuntu kernel: [  108.964232] PM: freeze of devices complete after 682.641 msecs
Jan 13 20:51:48 ubuntu kernel: [  108.965248] PM: late freeze of devices complete after 1.010 msecs
Jan 13 20:51:48 ubuntu kernel: [  109.224918] PM: Saving platform NVS memory
Jan 13 20:51:48 ubuntu kernel: [  109.420245] PM: Creating hibernation image: 
Jan 13 20:51:48 ubuntu kernel: [  109.430008] PM: Need to copy 128391 pages
Jan 13 20:51:48 ubuntu kernel: [  109.430008] PM: Normal pages needed: 128391 + 1024, available pages: 911188
Jan 13 20:51:48 ubuntu kernel: [  109.430008] PM: Restoring platform NVS memory
Jan 13 20:51:48 ubuntu kernel: [  110.223641] PM: early restore of devices complete after 1.774 msecs
Jan 13 20:51:48 ubuntu kernel: [  111.114212] PM: restore of drv:i915 dev:0000:00:02.0 complete after 715.155 msecs
Jan 13 20:51:48 ubuntu kernel: [  111.472591] PM: restore of drv:usb dev:usb1 complete after 259.401 msecs
Jan 13 20:51:48 ubuntu kernel: [  111.622643] PM: restore of drv:usb dev:usb2 complete after 150.032 msecs
Jan 13 20:51:48 ubuntu kernel: [  111.973104] PM: restore of drv:usb dev:1-3 complete after 346.150 msecs
Jan 13 20:51:48 ubuntu kernel: [  112.027386] PM: restore of devices complete after 1720.430 msecs
Jan 13 20:51:48 ubuntu kernel: [  112.027680] PM: Image restored successfully.
Jan 13 20:51:48 ubuntu kernel: [  112.028896] PM: Basic memory bitmaps freed
bwbloch@ubuntu:~$ 
```

---

### Post by bcbc on 2011-01-14
> **Telos3K said:**
> Did the above.  Now when I try to hibernate, the screen freezes and eventually the machine shuts down.  When I reboot it, I get that "resume from dev/[UUID]" message, and a lot of ugly hard drive crunching noise, the screen goes black and then comes back to life -- to where I left off when I hibernated.


Apart from the ugly crunching noise, it sounds pretty similar to my hibernate experience. There is no display indicating that it is hibernating and showing the progress - it just gets on with it. Also I find when it restores the screen is usually dark or goes straight to screensaver/locked once I move the mouse.

So, that part sounds normal. Just a bit worrisome to have that hard drive noise. I'd run a quick check on your disks - if they have SMART monitoring the Disk Utility under System/Administration should indicate if there are any issues.

---

### Post by Telos3K on 2011-01-16
Disk Utility SMART status shows disk is healthy.

Turns out that when I hibernate simply by closing the laptop (which is how I normally do it), everything works smoothly. It's only when I hibernate from the dropdown that the process gets a little funky, for some reason. So it's a solved problem.  Many thanks.

Question: Can I use remastersys in the future, if afterward I uninstall casper and go through the above steps?

---

### Post by bcbc on 2011-01-17
> **Telos3K said:**
> Disk Utility SMART status shows disk is healthy.

Turns out that when I hibernate simply by closing the laptop (which is how I normally do it), everything works smoothly. It's only when I hibernate from the dropdown that the process gets a little funky, for some reason. So it's a solved problem.  Many thanks.

Question: Can I use remastersys in the future, if afterward I uninstall casper and go through the above steps?
I assume you'd repeat the step to remove ramzswap and casper after playing with remastersys.

Are you sure that it doesn't Suspend when you close the lid. That's normally the default option - but you can check this through the System, Preferences, Power options.

---

### Post by Telos3K on 2011-01-24
You are, if course, correct -- closing the lid suspends, which is good enough for what I need. Hibernate is a bit clunky, but I think between suspend and just shutting the machine down, I'm covered.

Many thanks!

---

