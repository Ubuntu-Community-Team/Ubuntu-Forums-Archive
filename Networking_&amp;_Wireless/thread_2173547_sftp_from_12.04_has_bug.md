---
title: "sftp from 12.04 has bug"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by wzis on 2013-09-10
[COLOR=#333333][FONT=Arial]You can find the bug by doing following:[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]1. stty -echo[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]2. sftp user@server[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]key in password as required.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]3. cd /[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]4. ls -l[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]5. bye[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]6. stty -a

By right, the sftp commands entered in step 3-5 and the command entered after sftp exits at step 6 shouldn't be visible, but they do.
I tested sftp on other UNIX/Linux platforms, found Solaris/AIX/HP-UX and RHEL 5.5 all work properly. So this bug needs be fixed.[/FONT][/COLOR]

---

### Post by mörgæs on 2013-09-10
Is it also present in 13.10?

---

