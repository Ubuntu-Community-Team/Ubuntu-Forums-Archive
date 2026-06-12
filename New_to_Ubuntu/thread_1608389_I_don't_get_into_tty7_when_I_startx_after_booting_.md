---
title: "I don't get into tty7 when I startx after booting into command line"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by chichopep on 2010-10-29
Hi,

I am using ubuntu 10.10 desktop i386 with fluxbox. I boot directly to the command line by having added "text" to the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
in /etc/default/grub, as explained by sisco311 in these threads:
[http://ubuntuforums.org/showthread.php?t=1305659](http://ubuntuforums.org/showthread.php?t=1305659)
[http://newyork.ubuntuforums.org/showthread.php?p=9643769](http://newyork.ubuntuforums.org/showthread.php?p=9643769)

Afterwards, if I want to go into graphical mode, I choose one of these two options: either I "sudo service gdm start" or I "startx" into fluxbox directly.

I would like to just startx, but when I do so, I don't get into tty7 but I kind of remain in tty1. I think I am experiencing this bug:
[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/535521](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/535521)
This is the output of $ ck-list-sessions
Session1:
	unix-user = '1000'
	realname = 'Philo'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ''
	x11-display-device = ''
	display-device = '/dev/tty1'
	remote-host-name = ''
	is-local = TRUE
	on-since = '2010-10-29T04:50:13.978237Z'
	login-session-id = ''
	idle-since-hint = '2010-10-29T04:50:52.002045Z'
The session is not active. I don't have sound, and  I can't automaticaly mount drives, etc.

The bug has apparently been fixed in LTSP 5.2. But i says in the report of the bug that "closing in LTSP, the problem is still there on consolekit though". I would like to see the solution, by having a look at the new /etc/X11/Xsession.d/90consolekit, or whatever. But I do not know how I can access that information. I have tried to download the alternate ubuntu live cd with LTSP, but I could not find what I was looking for in there.

Does anybody know how I can access the solution to the bug? Thank you for any help.

---

