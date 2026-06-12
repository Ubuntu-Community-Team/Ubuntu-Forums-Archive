---
title: "General troubleshooting and help finding system logs"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by qazokm on 2009-01-30
I've been having problems with Ibex on my HP tx2500z laptop. It's been crashing really regularly on two separate installs (standard 64 and studio 64). I can't seem to link the problems to any one program or process and it seems completely random. I've not yet tried disabling all system processes to find the trouble, but that's my next move. I've tried to find where information might be stored about the crash but I haven't been able to find any info, and I was wondering if there was a guide that might help me trouble shoot random problems like this. Something that listed where the log files are and what they each log.

Thanks in advance.

---

### Post by dorkdork777 on 2009-01-30
System logs are generally stored in "/var/log". They're mostly organised into folders, and all named appropriately; it shouldn't be too hard to find the one you want. I suspect clues may be found in one of these files - 
[list][*]messages
[*]messages.0
[*]faillog
[*]syslog
[*]syslog.0
[*]user.log
[*]user.log.0
[/list]
That's just telling from the names; I don't actually have any experience with these files. Someone else may be able to fill you in?

---

