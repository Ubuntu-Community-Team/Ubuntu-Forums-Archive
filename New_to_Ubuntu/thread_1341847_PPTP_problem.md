---
title: "PPTP problem"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Bizness on 2009-11-30
Hi all, first post, new to Linux and hence Ubuntu so needing some help (on a very basic level please :D)

I've been trying to set up a VPN server for my work to (eventually) facilitate iPhone to Exchange compatibility.  I'm utterly against opening ports on the main firewall and hence have another internet connection that I will use for this purpose.

I've followed this chaps guide... [http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/)
...which has been reasonably straightforward thus far, but having now rebooted to begin use/debugging etc. I'm now stuck with the following screen and have no idea what to do...

"Starting PPTP Daemon:" 

Cursor's flashing and no matter what key I press, nothing happens.  What have I done, what am I doing, how ... etc

All help gratefully received.

---

### Post by yeats on 2009-11-30
There *should* be some sort of logging information created by that program.  I would use the System -> Administration -> Log File Viewer and look at the daemon.log entries.

---

### Post by Bizness on 2009-11-30
Thanks for the reply mate, but can you be a bit more basic?

I'm just stuck looking at that message and flashing cursor at the minute, what do I do to get past that?  Was about to rebuild it and start again.

---

### Post by ukripper on 2009-11-30
may help - [http://ubuntuforums.org/showthread.php?t=887062](http://ubuntuforums.org/showthread.php?t=887062)

---

### Post by Bizness on 2009-11-30
Thanks mate, I'll have a gander.

---

### Post by Bizness on 2009-11-30
Well it looks like a better guide to set up, so thanks for that.

But I'm still stuck with an unusable machine at the mo'.  Anyone have any ideas how to get past this screen?

---

### Post by ukripper on 2009-11-30
reboot and boot into recovery mode and then install rcconf:
```
sudo apt-get install rcconf
```

Disable PPTP:
```
sudo rcconf
```

find PPTP daemon and uncheck there to stop it form loading at boot.

---

### Post by Bizness on 2009-11-30
Thanks UKRipper, but I must frustrate you with more questions (sorry)

How do I get into the Recovery Mode?  (For starters :)

---

### Post by Bizness on 2009-11-30
OK, I've worked that out :)

Do I drop out to command prompt with networking?

---

### Post by Bizness on 2009-11-30
Resolved and I'm in. :)

---

### Post by ukripper on 2009-11-30
sorry mate was away for lunch. Couldn't answer your queries. So was taht pptp daemon listed there when you were in recovery mode?

---

### Post by Bizness on 2009-11-30
It was mate, thanks for your help.

Upon getting into the GUI now though, I can't get the machine on the network or internet.  Clearly I've ballsed something up during the VPN set up, so I'm just wiping and will start again with the guide in the link posted on page 1.

Again, thanks all for your help. :)

---

