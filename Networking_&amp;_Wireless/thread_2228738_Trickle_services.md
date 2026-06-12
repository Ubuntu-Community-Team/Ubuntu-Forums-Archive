---
title: "Trickle services"
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-06-09
Hi,
since downloading stuff using scp seems to use all available resources I want to prioritize some services.
I stumbled across trickle which could let me do this.
Sadly all I can find is the standard conf file which looks like this:
```
# [ssh]
# Priority = 1
# Time-Smoothing = 0.1
# Length-Smoothing = 2
# [ftp]
# Priority = 8
# Time-Smoothing = 5
# Length-Smoothing = 2
```
So where do I get the info which name to put in the brackets?
Is scp already uncluded in ssh?
What would I do with e.g. Teamspeak or Firefox?
These are the three things I'd like to prioritize.
1) Teamspeak
2) Firefox
3) scp
4) everything else

While scp and firefox is startable with $ scp and $ firefox which would make me think I might be able to simply put "scp" and "firefox" into those brackets, teamspeak is not. It is started via bash script.

So what has to go into the brackets so I am able to do this?

---

### Post by TheFu on 2014-06-09
I don't know anything about trickle. Sorry.  What does the man page say?

**rsync** will let you limit the bandwidth used for any transfer task and it runs over ssh/scp/sftp by default.
**--bwlimit=RATE          limit socket I/O bandwidth**
is the option.  Learn more about it in the man page for rsync.

Yes, ssh includes scp, sftp. Nothing more to install or configure after the keys are setup and the ssh port is opened to the world.  Well ... **fail2ban** is a really good idea whenever ssh/scp/sftp are used. If you allow connections to any of these things over the internet, don't use passwords - use keys.

According to the trickle man page
>      trickle is a userspace bandwidth manager.  Currently, trickle supports
     the shaping of any SOCK_STREAM (see socket(2)) connection established via
     the socket(2) interface.  Furthermore, trickle will not work with stati&#8208;
     cally linked executables, nor with setuid(2) executables.  trickle is
     highly configurable; download and upload rates can be set separately, or
     in an aggregate fashion.

Lots of other useful information in the man page.  Looks like all settings can be set on the command line for each app we'd like to control bandwidth over.  That means creating a script to start each one and only running that script - not clicking the default startup methods in a GUI (er ... unless you manually replace where those things point).

While I don't know, but I expect the name in the brackets is just the program name.  BTW, there is no mention of the .initfile in the manpage.

---

### Post by chris137 on 2014-06-09
This won't be exactly what I want.
rsync only lets me do this via fix limit.
I want to do this because I have pretty unstable network due to powerLAN which is pretty bad in my room but I get best speeds whith it.

This is why I want to prioritize it rather than giving it a fix limit.
Also this would be possible with scp too.

If scp is uncluded in ssh was just regarding trickle conf.

My home network is pretty secure, also I am always using keys ;)

---

